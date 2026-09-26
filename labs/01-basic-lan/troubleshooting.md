# Lab 1 Troubleshooting — Subnet Mismatch

## Scenario

The original working configuration is:

| Device | IP Address | Subnet Mask |
|---|---|---|
| PC0 | 192.168.10.10 | 255.255.255.0 |
| PC1 | 192.168.10.20 | 255.255.255.0 |

Both hosts are in the same network:

`192.168.10.0/24`

They can communicate directly through the Layer 2 switch.

## Deliberate Fault

Change PC1 to:

- IP address: `192.168.20.20`
- Subnet mask: `255.255.255.0`

PC0 remains:

- IP address: `192.168.10.10`
- Subnet mask: `255.255.255.0`

The hosts are now in different IP networks:

- PC0 → `192.168.10.0/24`
- PC1 → `192.168.20.0/24`

## Expected Symptom

From PC0:

```text
ping 192.168.20.20
```

The ping should fail.

## Why It Fails

A switch forwards Ethernet frames inside a local Layer 2 network, but it does not route traffic between different IP subnets.

PC0 uses its subnet mask to determine that `192.168.20.20` is not on its local subnet. It therefore needs to send the traffic to a default gateway.

Because this lab has no router/default gateway, there is no Layer 3 device available to route traffic between `192.168.10.0/24` and `192.168.20.0/24`.

## Troubleshooting Process

1. Verify physical links are up.
2. Run `ipconfig` on both PCs.
3. Compare the IP addresses and subnet masks.
4. Identify that the devices are in different /24 networks.
5. Confirm that no router/default gateway exists.
6. Restore PC1 to the original subnet.
7. Test connectivity again with `ping`.

## Fix

Restore PC1 to:

- IP address: `192.168.10.20`
- Subnet mask: `255.255.255.0`

Then test from PC0:

```text
ping 192.168.10.20
```

The ping should succeed again.

## Key Lesson

A switch can connect devices in the same LAN, but communication between different IP subnets requires a Layer 3 device such as a router or multilayer switch.

## Evidence Still Required

This note documents the planned troubleshooting exercise. The lab should only be marked complete after the Packet Tracer build is actually tested and the following evidence is added:

- Working topology screenshot
- Successful ping screenshot
- Failed ping screenshot
- Restored successful ping screenshot

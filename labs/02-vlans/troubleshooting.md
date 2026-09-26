# Lab 2 Troubleshooting — VLAN Segmentation

## Deliberate Fault

After the working VLAN configuration is verified, move PC1's switch port (Fa0/2) from VLAN 10 to VLAN 20.

```text
enable
configure terminal
interface fa0/2
switchport access vlan 20
end
```

Then test from PC0:

```text
ping 192.168.10.20
```

The ping should fail even though both PCs still use addresses from 192.168.10.0/24.

## Diagnosis

Run:

```text
show vlan brief
```

If Fa0/2 appears under VLAN 20 instead of VLAN 10, the access port is assigned to the wrong Layer 2 broadcast domain.

## Fix

```text
enable
configure terminal
interface fa0/2
switchport access vlan 10
end
show vlan brief
```

Retest:

```text
ping 192.168.10.20
```

The ping should succeed again.

## Key Lesson

A VLAN separates devices at Layer 2. Two hosts may use IP addresses from the same IPv4 subnet, but if their switch ports belong to different VLANs they are not in the same Layer 2 broadcast domain and cannot communicate directly.

Inter-VLAN communication requires Layer 3 routing, which is introduced in Lab 3.

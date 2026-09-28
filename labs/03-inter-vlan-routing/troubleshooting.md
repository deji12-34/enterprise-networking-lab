# Lab 3 Troubleshooting — Incorrect Default Gateway

## Fault
Change HR-PC1's default gateway from `192.168.10.1` to `192.168.10.254`.

## Expected behavior

- HR-PC1 can still reach HR-PC2 because they are in the same VLAN/subnet.
- HR-PC1 cannot reach Sales or IT because traffic for remote networks must be sent to the correct default gateway.

## Diagnosis

On HR-PC1 run:

```text
ipconfig
```

Compare the configured gateway with the router subinterface for VLAN 10.

On R1 run:

```text
show ip interface brief
```

The correct gateway for VLAN 10 is `192.168.10.1`.

## Fix
Restore HR-PC1's default gateway to `192.168.10.1` and retest the cross-VLAN ping.

## Key lesson
A host sends traffic for a remote subnet to its default gateway. If the gateway is wrong, local communication may still work while routed communication fails.

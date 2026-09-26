# Lab 2 Packet Tracer Build Guide

## 1. Place the devices

Add:

- 1 × Cisco 2960 switch
- 6 × PCs

Rename them:

- PC0, PC1
- PC2, PC3
- PC4, PC5
- Switch0

## 2. Cable the devices

Use **Copper Straight-Through** cables.

| PC | Switch Port |
|---|---|
| PC0 | Fa0/1 |
| PC1 | Fa0/2 |
| PC2 | Fa0/3 |
| PC3 | Fa0/4 |
| PC4 | Fa0/5 |
| PC5 | Fa0/6 |

Wait until the links become green.

## 3. Configure the PCs

Use **Desktop → IP Configuration** on each PC.

| PC | IPv4 Address | Subnet Mask |
|---|---|---|
| PC0 | 192.168.10.10 | 255.255.255.0 |
| PC1 | 192.168.10.20 | 255.255.255.0 |
| PC2 | 192.168.20.10 | 255.255.255.0 |
| PC3 | 192.168.20.20 | 255.255.255.0 |
| PC4 | 192.168.30.10 | 255.255.255.0 |
| PC5 | 192.168.30.20 | 255.255.255.0 |

Leave the default gateway blank.

## 4. Configure VLANs on Switch0

Open **Switch0 → CLI** and enter:

```text
enable
configure terminal

vlan 10
name HR
exit

vlan 20
name SALES
exit

vlan 30
name IT
exit

interface range fa0/1-2
switchport mode access
switchport access vlan 10
exit

interface range fa0/3-4
switchport mode access
switchport access vlan 20
exit

interface range fa0/5-6
switchport mode access
switchport access vlan 30
exit

end
show vlan brief
```

## 5. Verify VLAN membership

Expected result:

```text
VLAN  Name   Ports
10    HR     Fa0/1, Fa0/2
20    SALES  Fa0/3, Fa0/4
30    IT     Fa0/5, Fa0/6
```

## 6. Test connectivity

Same VLAN should work:

```text
PC0> ping 192.168.10.20
PC2> ping 192.168.20.20
PC4> ping 192.168.30.20
```

Cross-VLAN traffic should fail:

```text
PC0> ping 192.168.20.10
PC0> ping 192.168.30.10
```

## 7. Perform the fault exercise

Move Fa0/2 into VLAN 20:

```text
enable
configure terminal
interface fa0/2
switchport access vlan 20
end
```

Then test:

```text
PC0> ping 192.168.10.20
```

It should fail.

Check:

```text
show vlan brief
```

Restore the correct VLAN:

```text
configure terminal
interface fa0/2
switchport access vlan 10
end
show vlan brief
```

Retest the ping.

## 8. Save the lab

Save the Packet Tracer project as:

```text
lab02-vlan-segmentation.pkt
```

Then capture the screenshots listed in the evidence folder.

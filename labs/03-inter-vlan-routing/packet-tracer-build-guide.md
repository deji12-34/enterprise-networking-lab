# Lab 3 Packet Tracer Build Guide

## Goal
Enable communication between VLAN 10 (HR), VLAN 20 (Sales), and VLAN 30 (IT) using **router-on-a-stick**.

## 1. Start from Lab 2

Open the completed Lab 2 file and save a copy as:

```text
lab03-inter-vlan-routing.pkt
```

Do not overwrite the Lab 2 file.

## 2. Add the router

Add one Cisco 1941 or 2911 router and name it `R1`.

Connect:

| Device | Interface | To | Interface |
|---|---|---|---|
| R1 | G0/0 | SW1 | Fa0/24 |

Use a copper straight-through cable.

## 3. Configure the switch trunk

On SW1:

```text
enable
configure terminal
interface fa0/24
switchport mode trunk
switchport trunk allowed vlan 10,20,30
no shutdown
end
show interfaces trunk
```

`Fa0/24` must show as a trunk carrying VLANs 10, 20, and 30.

## 4. Configure router subinterfaces

On R1:

```text
enable
configure terminal
hostname R1

interface g0/0
no shutdown
exit

interface g0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit

interface g0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
exit

interface g0/0.30
encapsulation dot1Q 30
ip address 192.168.30.1 255.255.255.0
exit

end
show ip interface brief
```

## 5. Add default gateways to the PCs

| Department | PCs | Default Gateway |
|---|---|---|
| HR | HR-PC1, HR-PC2 | `192.168.10.1` |
| Sales | SALES-PC1, SALES-PC2 | `192.168.20.1` |
| IT | IT-PC1, IT-PC2 | `192.168.30.1` |

Keep the existing PC IP addresses from Lab 2.

## 6. Test inter-VLAN routing

From HR-PC1:

```text
ping 192.168.20.10
ping 192.168.30.10
```

Both should now succeed.

Also test the gateways:

```text
ping 192.168.10.1
ping 192.168.20.1
ping 192.168.30.1
```

## 7. Deliberate troubleshooting fault

On HR-PC1, temporarily set the default gateway to:

```text
192.168.10.254
```

Then try:

```text
ping 192.168.20.10
```

Same-VLAN communication should still work, but cross-VLAN communication should fail.

Restore the gateway to:

```text
192.168.10.1
```

and retest.

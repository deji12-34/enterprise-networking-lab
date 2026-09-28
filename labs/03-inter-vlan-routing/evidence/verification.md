# Lab 3 — Evidence Verification

Lab 3 has been built and tested in Cisco Packet Tracer using router-on-a-stick.

## Verified Results

| Check | Result |
|---|---|
| SW1 trunk interface | Fa0/24 |
| Trunk encapsulation | 802.1Q |
| VLANs allowed on trunk | 10,20,30 |
| R1 parent interface | G0/0 up/up |
| R1 VLAN 10 subinterface | G0/0.10 — 192.168.10.1 up/up |
| R1 VLAN 20 subinterface | G0/0.20 — 192.168.20.1 up/up |
| R1 VLAN 30 subinterface | G0/0.30 — 192.168.30.1 up/up |
| Inter-VLAN routing proof | IT-PC2 successfully reached HR-PC2 (192.168.10.20) |
| Deliberate fault | IT-PC2 default gateway changed to an incorrect address |
| Fault result | IT-PC2 → HR-PC2 failed with 100% packet loss |
| Repair | IT-PC2 gateway restored to 192.168.30.1 |
| Recovery result | IT-PC2 → HR-PC2 succeeded with 4/4 replies |
| Packet Tracer project | lab03-inter-vlan-routing.pkt supplied |

## Packet Tracer Project Integrity

SHA-256:

`57bee6b1b0cf9878f9ba5ab0ddd72382e0152dc8b908ca450282605ebf508588`

File size: 56,273 bytes.

## Final Host-to-Host Verification

IT-PC2 successfully reached SALES-PC1 at `192.168.20.10` with 4/4 replies and 0% packet loss.

Screenshot SHA-256:

`fe220b1f6b87230b18c3bb68c3bba528a84c46a2bbcb3c73713ee0520615efa8`

This completes the required inter-VLAN routing verification across HR, Sales and IT.

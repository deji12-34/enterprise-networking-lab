# Lab 2 — VLAN Segmentation

## Objective
Segment a small company network into separate departments using VLANs.

## Scenario
Create three departments:
- HR — VLAN 10
- Sales — VLAN 20
- IT — VLAN 30

## Tasks
- [ ] Add at least 6 PCs and 1 switch
- [ ] Create VLAN 10, VLAN 20 and VLAN 30
- [ ] Name the VLANs HR, SALES and IT
- [ ] Assign switch access ports to the correct VLANs
- [ ] Configure IP addresses for each department
- [ ] Verify same-VLAN communication
- [ ] Verify that different VLANs cannot communicate yet
- [ ] Inspect VLAN membership with `show vlan brief`

## Suggested Addressing
| VLAN | Department | Network |
|---|---|---|
| 10 | HR | 192.168.10.0/24 |
| 20 | Sales | 192.168.20.0/24 |
| 30 | IT | 192.168.30.0/24 |

## Core Commands
```
enable
configure terminal
vlan 10
name HR
vlan 20
name SALES
vlan 30
name IT
show vlan brief
```

## Evidence to Add
- [ ] Topology screenshot
- [ ] `show vlan brief` output
- [ ] Successful same-VLAN ping
- [ ] Failed cross-VLAN ping
- [ ] Explanation of why VLANs improve segmentation

## Status
Not started.

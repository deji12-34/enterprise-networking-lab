# Lab 2 — Evidence Verification

Lab 2 was completed in Cisco Packet Tracer and verified through real test results.

## Verified Results

| Check | Result |
|---|---|
| VLAN 10 (HR) membership | Fa0/1, Fa0/2 |
| VLAN 20 (SALES) membership | Fa0/3, Fa0/4 |
| VLAN 30 (IT) membership | Fa0/5, Fa0/6 |
| Same-VLAN test | HR-PC1 → HR-PC2 succeeded, 4/4 replies |
| Cross-VLAN test | HR-PC1 → SALES failed as expected, 0/4 replies |
| Deliberate fault | Fa0/2 moved from VLAN 10 to VLAN 20 |
| Fault result | HR-PC1 → HR-PC2 failed, 0/4 replies |
| Repair | Fa0/2 restored to VLAN 10 |
| Recovery result | HR-PC1 → HR-PC2 succeeded, 4/4 replies |
| Packet Tracer project | lab02-vlan-segmentation.pkt supplied after completion |

## Evidence Integrity

The following SHA-256 hashes correspond to the real files captured during the lab session.

| Evidence | SHA-256 |
|---|---|
| Final topology screenshot | `bbd0d01275577cecd5380ce641194d91d7113dfde61b1e6d7f846084e2ec71b6` |
| Final `show vlan brief` screenshot | `44f76aa47eef99f3a5bc1095c100279a5a7b14cb4313562f5e5efc270e0d6f35` |
| Same-VLAN success screenshot | `87e47177b8009fe04a2716d07953f9263134fe9961d63a12006900e8106fa06f` |
| Cross-VLAN failure screenshot | `a243ae9bd572d7beedc7856cf4081dbc13c9e131eeefe0fcd5a9ca8876c1b616` |
| Wrong-VLAN configuration screenshot | `8b8067c7631f97786570667fdf2434dcbfba6901d12a8ca3cfd7ab5a24f6e6f4` |
| Wrong-VLAN failure screenshot | `3b49869f926f543f1e1cf5b81dbc2d394cc4c01460867419fd77da7e4e5b3418` |
| Restored VLAN configuration screenshot | `149c80adca82b09f5af251ecd238543223a862dd29b392cb05f91b682923ee65` |
| Restored connectivity screenshot | `4ec903aa9f49cbf701a3e1a0e755bfd040e506934ff6e8042463bfe30ddfe8ed` |
| `lab02-vlan-segmentation.pkt` | `9420d6bd547574ace777714fed97eacf7938e5ab5e5e164c1bdd23679bf2dc0e` |

## What This Proves

The lab demonstrates that access-port VLAN membership creates separate Layer 2 broadcast domains, hosts in the same VLAN can communicate directly, hosts in different VLANs remain isolated without Layer 3 routing, and an incorrect VLAN assignment can be identified and repaired by checking switch configuration and VLAN membership.

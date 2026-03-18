🛠️ Lessons Learned & Troubleshooting Insights

This lab wasn’t just about getting the network to work—it was about working through the moments where nothing did. Key takeaways include:

NIC & Interface Challenges
Early issues with NIC detection, bridge assignments, and switch port behavior forced me to methodically check link states and interface mappings.

Physical vs. Configuration Problems
Even simple tests, like a cable returning 0, taught me to slow down and consider whether the issue was physical or logical.

Layered Misconfigurations
Mismatched interfaces (e.g., enp1s0f0 vs enp3s0) and missing bridges (vmbrlan) compounded problems, breaking VM connectivity.

Most network issues aren’t one big mistake—they’re multiple small mismatches stacking together.

Methodical Debugging
Fixing problems required patience:

Verifying link lights and interface states

Reviewing Proxmox bridge configurations

Aligning VLAN tagging between switch and OPNsense

Key Takeaway
Networking is often about careful validation at every layer and questioning assumptions, not just applying fixes blindly.

⚡ Quick Wins / Common Fixes
| Issue                                | Cause                                               | Fix / Action Taken                                                                     |
| ------------------------------------ | --------------------------------------------------- | -------------------------------------------------------------------------------------- |
| NIC link lights not showing          | Interfaces were down or misassigned                 | `sudo ip link set enp1s0f1 up` & verify `ip link` status                               |
| VM connectivity broken               | Missing VLAN-aware bridge / misaligned interfaces   | Created missing bridge (`vmbrlan`) and aligned VLAN tagging between Proxmox and switch |
| Switch ports behaving unexpectedly   | Incorrect access/tagged port settings               | Reviewed switch config → ensured access vs trunk ports matched intended VLANs          |
| Confusing cable / connectivity tests | Physical vs configuration ambiguity                 | Slowed down → confirmed cable, verified interface, traced path logically               |
| Multiple small mismatches stacking   | Small misconfigurations across bridges, NICs, VLANs | Methodical layer-by-layer verification: link lights → Proxmox bridge → OPNsense VLANs  |


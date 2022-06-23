**Bridge Protocol Data Units** (BPDUs) are [frames](https://en.wikipedia.org/wiki/Frame_(networking) "Frame (networking)") that contain information about the [spanning tree protocol](https://en.wikipedia.org/wiki/Spanning_tree_protocol "Spanning tree protocol") (STP). A switch sends BPDUs using a unique source [MAC address](https://en.wikipedia.org/wiki/MAC_address "MAC address") from its origin [port](https://en.wikipedia.org/wiki/Port_(computer_networking) "Port (computer networking)") to a [multicast address](https://en.wikipedia.org/wiki/Multicast_address "Multicast address") with destination MAC (01:80:C2:00:00:00,[[1]](https://en.wikipedia.org/wiki/Bridge_protocol_data_unit#cite_note-1) or 01:00:0C:CC:CC:CD for [Cisco proprietary Per VLAN Spanning Tree](https://en.wikipedia.org/wiki/Spanning_Tree_Protocol#Per-VLAN_Spanning_Tree_and_Per-VLAN_Spanning_Tree_Plus "Spanning Tree Protocol")).[[2]](https://en.wikipedia.org/wiki/Bridge_protocol_data_unit#cite_note-2)

There are two kinds of BPDUs for 802.1D Spanning Tree:[[3]](https://en.wikipedia.org/wiki/Bridge_protocol_data_unit#cite_note-3)

-   Configuration BPDU, sent by root bridges to provide information to all switches.
-   TCN (Topology Change Notification), sent by bridges towards the root bridge to notify changes in the topology, such as port up or port down.

By default the BPDUs are sent every 2 seconds.
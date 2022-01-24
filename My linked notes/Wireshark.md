Wireshark ([wireshark.org](https://www.wireshark.org/)) is an open-source graphical **packet capture** and analysis utility, with installer packages for most operating systems. Having chosen the interface to listen on, the output is displayed in a three-pane view. The packet list pane shows a scrolling summary of frames. The packet details pane shows expandable fields in the frame currently selected from the packet list. The packet bytes pane shows the raw data from the frame in hex and ASCII. Wireshark is capable of parsing (interpreting) the headers and payloads of hundreds of network protocols.

You can apply a capture filter using the same expression syntax as tcpdump (though the expression can be built via the GUI tools too). You can save the output to a .pcap file or load a file for analysis. Wireshark supports very powerful display filters ([wiki.wireshark.org/DisplayFilters](https://wiki.wireshark.org/DisplayFilters)) that can be applied to a live capture or to a capture file. You can also adjust the coloring rules ([wiki.wireshark.org/ColoringRules](https://wiki.wireshark.org/ColoringRules)), which control the row shading and font color for each frame.

![Screenshot shows list of items with headings No., Time, Source, Destination, Protocol, Length, Info. Highlighted item is further detailed in 2 panes.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8605-1599771795036.png)

Wireshark protocol analyzer. (Screenshot used with permission from wireshark.org.)

Wireshark output of a packet analysis. (Screenshot used with permission from wireshark.org.)

Another useful option is to use the **Follow TCP Stream** context command to reconstruct the packet contents for a TCP session.

The PCAP file format has some limitations, which has led to the development of PCAP Next Generation (PCAPNG). Wireshark now uses PCAPNG by default, and tcpdump can process files in the new format too ([cloudshark.io/articles/5-reasons-to-move-to-pcapng](https://cloudshark.io/articles/5-reasons-to-move-to-pcapng/)).
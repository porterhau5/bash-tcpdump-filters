bash-tcpdump-filters
====================

Bash script for using tcpdump filters to identify interesting packets

Usage
-----
First, source the functions:
<pre>. tcpdumpfilter</pre>

<pre>filter &lt;pcap&gt; &lt;output dir&gt;</pre>

Example: <pre>filter example.pcap out</pre>

Requirements
------------
"tcpdump" should be installed and on your $PATH. The code here was written against Tcpdump 4.1.1 and libpcap 1.1.1.

Background
----------
The idea is to have one place to store all of the interesting tcpdump filters I use or come across. The filters I chose to be in here are ones that will provide useful information for someone who is trying to gain a grasp on their network situational awareness. For example, summary of DNS query names, fragmented packets, illegal TCP flag combinations. Currently, it's leaning more towards the suspicious or anomalous packets than just general packet summarization.

Filters
-------
IP Fragments - Fragmented packets on a network can indicate that a host or network device is misconfigured or that someone might be trying to perform IDS/IPS evasion
IP Options - Unlike TCP Options, IP Options aren't used frequently and should be paid attention to
Evil bit - If this reserved bit is set then the packet is mostly likely crafted
Reserved TCP flags - If these reserved bits are set, then the packet is most likely crafted
ECN flags - Packets with ECN flags set (NS, CWR, ECE)

TODO
----
* Protocol summarization
* Application protocol analysis
* Read in multiple pcaps or a directory of pcaps
* Run filters in parallel
* Auto-create output directory
* Create parameter which dictates tcpdumps output (e.g. nnvvXS)
* Option to write out pcap instead of ASCII

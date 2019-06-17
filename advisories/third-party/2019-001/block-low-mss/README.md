## Workaround to block connections with low MSSs

#### [iptables.txt](iptables.txt)
For a Linux instance, use iptables module tcpmss to
set a range of TCP MSS values to reject. An attacker using a small
(in this example < 500) MSS will drop the TCP SYN packets.
This will block connection establishment and block the attack.

#### [tc-bytecode](tc-bytecode)
Outputs tc commands to install a bpf ingress filter,
as for above TCP SYN packets are dropped.

#### [tcpdump](tcpdump)
Used by tc-bytecode to invoke tcpdump(8) with a rule
set to detect a TCP-SYN packet header with a MSS option in any
possition that request a small MSS.

#### [tc.txt](tc.txt)
The output from tc-bytcode, copy/paste to a sudo'd shell
to install a tc ingress filter for small MSS.

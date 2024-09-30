# Sippts VoIP Scanner

Sippts is a set of tools to audit VoIP servers and devices using SIP protocol. Sippts is programmed in Python and it allows us to check the security of a VoIP server using SIP protocol.

```
Commands:
  {scan,exten,rcrack,send,wssend,enumerate,leak,ping,invite,dump,dcrack,flood,sniff,spoof,tshark,rtpbleed,rtcpbleed,rtpbleedflood,rtpbleedinject}
    scan                                          Fast SIP scanner
    exten                                         Search SIP extensions of a PBX
    rcrack                                        Remote password cracker
    send                                          Send a customized message
    wssend                                        Send a customized message over WS
    enumerate                                     Enumerate methods of a SIP server
    leak                                          Exploit SIP Digest Leak vulnerability
    ping                                          SIP ping
    invite                                        SIP INVITE attack
    dump                                          Dump SIP digest authentications from a PCAP file
    dcrack                                        SIP digest authentication cracking
    flood                                         Flood a SIP server
    sniff                                         SIP network sniffing
    spoof                                         ARP Spoofing tool
    tshark                                        Filter data from a PCAP file with TShark
    rtpbleed                                      Detect RTPBleed vulnerability (send RTP streams)
    rtcpbleed                                     Detect RTPBleed vulnerability (send RTCP streams)
    rtpbleedflood                                 Exploit RTPBleed vulnerability (flood RTP)
    rtpbleedinject                                Exploit RTPBleed vulnerability (inject WAV file)
```

{% embed url="https://github.com/Pepelux/sippts/tree/v4.1.0" %}

---
title: 'Isip - Interactive Drink Toolkit For Bundle Manipulations, Sniffing,
Human Inwards The Meat Attacks, Fuzzing, Simulating Of Dos Attacks'
date: 2019-09-25T06:46:00+01:00
draft: false
---

Interactive gulp [toolkit](http://www.kitploit.com/search/label/Toolkit) for parcel manipulations, sniffing, [man inwards the middle](http://www.kitploit.com/search/label/Man%20In%20The%20Middle) attacks, fuzzing, simulating of dos attacks.  
  
**Video**  
  

[![](https://3.bp.blogspot.com/-3F63TIr5pLk/W9hshVKTDdI/AAAAAAAANEU/TtA7Y_4nqF0rVQg3rOn9PqaQ-uzrCtBgwCLcBGAs/s640/isip.png)](https://asciinema.org/a/11128)

  
**Setup**  

```
git clone https://github.com/halitalptekin/isip.git cd isip pip install -r requirements.txt
```

  
**Usage**  

*   Packet [manipulation](http://www.kitploit.com/search/label/Manipulation) tools are inwards `packet` cmd loop. First start, you lot are inwards the `main` cmd loop.

```
isip:main> parcel isip:packet>
```

*   Create a novel gulp parcel amongst `new` command. If you lot don't write name, isip practise the parcel named yesteryear `message-{id}`.

```
isip:packet> novel isip:packet> novel r1
```

*   List the all created gulp [packets](http://www.kitploit.com/search/label/Packets) amongst `list` command.

```
isip:packet> list
```

*   Show properties of packets amongst `show` command. You tin type `ip`, `udp` or `sip` amongst `show` command.

```
isip:packet> present message-1 isip:packet> present message-1 ip isip:packet> present message-1 udp isip:packet> present message-1 gulp isip:packet> present message-1 ip src isip:packet> present message-1 udp sport isip:packet> present message-1 gulp uri isip:packet> present message-1 gulp headers.to
```

*   Set the properties of packets amongst `set` command. You tin type `ip`, `udp` or `sip` in addition to properties label amongst `show` command.

```
isip> gear upward message-1 ip src 12.12.12.12 isip> gear upward message-1 udp sport 4545 isip> gear upward message-1 gulp method OPTIONS isip> gear upward message-1 gulp headers.from "blabla"
```

*   Set the random properties of packets amongst `set` command. You tin role amongst `random-headers-from`, `random-headers-to`, `random-headers-call-id`, `random-headers-max-forwards`, `random-headers-user-agent`, `random-headers-contact`, `random-headers-invite-cseq`, `random-headers-register-cseq` commands.

```
isip:packet> gear upward message-1 ip src random-ip isip:packet> gear upward message-1 udp sport random-port isip:packet> gear upward message-1 gulp headers.from random-headers-from isip:packet> gear upward message-1 gulp headers.to random-headers-to isip:packet> gear upward message-1 gulp headers.contact random-headers-contact isip:packet> gear upward message-1 gulp trunk random-data 50
```

*   Send the parcel amongst `send` command.

```
isip:packet> post message-1 1 isip:packet> post message-1 150
```

*   Parse the text file to parcel amongst `parse` command.

```
isip:packet> parse test/test1.txt r1
```

*   Load the packets from `pcap` file amongst `load` command. If you lot don't write name, isip practise the parcel named yesteryear `message-{id}`.

```
isip:packet> charge test.pcap r1 isip:packet> charge test.pcap
```

*   Save the packets tp `pcap` file amongst `save` command. You tin salvage the parcel listing merely unmarried command.

```
isip:packet> salvage r1 test.pcap isip:packet> salvage r2 test.pcap # assume you lot accept r2.0, r2.1, r2.2, r2.3 ...
```

*   Open the [wireshark](http://www.kitploit.com/search/label/Wireshark) for packets amongst `wireshark` command.

```
isip:packet> wireshark r1 isip:packet> wireshark r2 # assume you lot accept r2.0, r2.1, r2.2, r2.3 ...
```

*   List the history amongst `hist` command.

```
isip:packet> hist
```

*   Execute the vanquish ascendance amongst `shell` or `!`.

```
isip:packet> vanquish ls -la isip:packet> ! truthful cat /etc/passwd
```

*   Show the assistance page amongst `?` or `help` command.

```
isip> ? isip> assistance isip:packet> ? isip:packet> assistance isip:packet> assistance novel isip:packet> assistance post isip:packet> assistance gear upward isip:packet> assistance show
```

  
  

**[Download Isip](https://github.com/halit/isip)**
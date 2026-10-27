# S4. The neighbour's note and indicators

*Flare 2 · Rockhopper Reach Power Co-op (RRPC), security desk, to HTA · Wed 7 Oct 2026 · TLP:AMBER*

*The neighbour sends smoke signals but will not say how the fire started. Read what they sent.*

## The note

> HTA: we saw unexplained activity on two engineering hosts on Monday 5 and Tuesday 6 October. We do not know how it started. Our logging is thin: some hosts keep seven days, none keeps process events, and we have no samples. The one lead is that an engineer on one host downloaded a "governor tools" archive from a vendor mirror on Monday morning, which is not how your mail came in. We are sharing the network indicators our firewall and proxy kept, and nothing else. We cannot say whether this is your intruder.

## Indicators

| Type | Value | Seen | Note |
|---|---|---|---|
| host | steam-relay.invalid | Mon 5 Oct, 06:12 | A script and a library were fetched from it by a workstation after a vendor-mirror download. |
| address | 203.0.113.19 | Mon 5 Oct, 06:12 | The address that host resolved to. |
| address | 203.0.113.62 | Mon 5 Oct, 06:31 onward | A beacon destination, about every 20 minutes. |
| certificate | 73:17:d2:d3:5c:27:30:c3:75:c6:81:1d:53:ab:33:31:c7:ea:aa:57:a2:fb:7b:f4:c4:ee:52:ea:b3:98:21:21 | Mon 5 Oct, 06:31 onward | SHA-256 fingerprint of the certificate that address presented to our firewall's inspection point. |
| interval | about 20 minutes | Mon 5 Oct onward | Between connections to the beacon destination. |
| address and port | 198.51.100.77:443 | Tue 6 Oct, 14:32, once | A single connection from one engineering host, no reply body logged. We do not know what it was. |

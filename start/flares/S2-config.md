# S2. The implant's configuration, as LIR recovered it

*Flare 1 · LIR note LIR-HTA-1005-03 · TLP:AMBER*

*The Undercurrent, one hour twenty into the watch. LIR has brought the implant up in one piece from the memory image, and the nets have hauled in three beacons (S3). What the implant carries was folded small. LIR's analyst unfolded it, and here is what it said.*

The implant keeps its configuration in a folded form. LIR's analyst unfolded it in LIR's lab with the implant's own routines and reports the result as text. The Hold's record of the implant is `wks-r4-12_qfhelper_pid2208.bin`.

**The configuration record** (one line, fields separated by semicolons):

```
v=2;i=0c8f2d;c=HV2641;h=ember-relay.invalid;ua=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36;t=1200
```

| Field | Value | LIR's reading |
|---|---|---|
| `v` | `2` | Configuration version. |
| `i` | `0c8f2d` | The implant's identifier on this victim. |
| `c` | `HV2641` | Campaign tag. |
| `h` | `ember-relay.invalid` | The command host. |
| `ua` | `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36` | The user agent the implant presents. |
| `t` | `1200` | Base beacon interval, in seconds. |

**LIR's notes**

- The implant connects to the address in the proxy log (`203.0.113.45:8443`) and presents `h` as the Host header, so the address in the proxy log is a front for the command host.
- The campaign tag has the form `HV` + year + number. LIR reads the number as the planned week of the campaign; the beacons fall in week 41 of 2026.
- The layout of the record matches the format strings in the Hold's record of the implant: look at its Strings tab.
- The implant paces its beacons with a timer built from `t` and a jitter percentage. The three beacons in S3 fall 19 minutes 31 seconds and 20 minutes 51 seconds apart.
- The implant does not use the user agent that the loader's configuration block lists. LIR makes no judgement about why.
- The user-agent value contains semicolons of its own, so a reader that splits the record at every semicolon will cut it in the wrong places. Read from the first `ua=` to the last `;t=`.

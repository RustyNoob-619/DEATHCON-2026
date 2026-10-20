# S9. A proxy log excerpt

*Case file · start set · TLP:AMBER · proxy `proxy-r4`, client `wks-r4-12`, Monday 5 October 2026*

Policy note: the proxy decrypts HTTPS to named hosts and logs the request line. A connection to a bare address on a non-standard port is tunnelled without inspection, so the proxy logged no request line and no Host header for the connections to `203.0.113.45:8443`. In the tunnel lines, the bytes column is *sent/received*.

```
time (UTC)             client     method  destination                                          status  bytes   user agent
2026-10-05T07:59:14Z   wks-r4-12  GET     https://flue-cache.invalid/qf400/QF400_4.2.1_Update.zip  200     53528   Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/130.0.0.0 Safari/537.36 Edg/130.0.0.0
2026-10-05T08:04:11Z   wks-r4-12  GET     https://steam-relay.invalid/qf400/qfsync.ps1         200     5472    Microsoft-WebDAV-MiniRedir/10.0.19045
2026-10-05T08:04:37Z   wks-r4-12  GET     https://steam-relay.invalid/qfcore.dll               200     77824   Mozilla/5.0 (Windows NT; Windows NT 10.0; en-US) WindowsPowerShell/5.1.19041.4648
2026-10-05T08:09:41Z   wks-r4-12  CONNECT  203.0.113.45:8443                                    tunnel  420/188  -
2026-10-05T08:29:12Z   wks-r4-12  CONNECT  203.0.113.45:8443                                    tunnel  420/188  -
2026-10-05T08:50:03Z   wks-r4-12  CONNECT  203.0.113.45:8443                                    tunnel  420/188  -
```

Lines before 07:59 and after the third tunnel are omitted from this excerpt. Every tunnel line to `203.0.113.45:8443` between 08:09 and the host's isolation on Wednesday has the same shape and falls about twenty minutes after the one before.

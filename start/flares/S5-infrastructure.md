# S5. The infrastructure sheet

*Flare 2 · passive-DNS, WHOIS and certificate records held by SWORD's collection desk · TLP:AMBER*

One row per name or address in this case, and a few that are not. Dates and times are UTC. The sheet does not say which rows belong together.

| Name or address | Registered or first seen (UTC) | Registrar or hosting | Resolves to | Certificate issuer | Validity (days) | Serial (start) | SHA-256 fingerprint |
|---|---|---|---|---|---|---|---|
| quillfeather-support.invalid | 2026-09-28 06:58 | Tidepool Registrar | 198.51.100.52 | - | - | - | - |
| flue-cache.invalid | 2026-09-28 07:12 | Tidepool Registrar | 203.0.113.31 | Quayside Trust CA | 372 | 6a:02:91:4e:c3:17:d8:2b:50 | cd:c7:20:2c:48:1f:32:a2:05:d4:40:3a:e2:5a:ee:eb:6d:b6:4b:53:e6:b9:e2:1a:e9:5c:ee:ae:96:4a:55:f3 |
| steam-relay.invalid | 2026-09-28 07:04 | Tidepool Registrar | 203.0.113.19 | Quayside Trust CA | 372 | 6a:02:37:b1:08:5e:aa:9d:12 | 73:17:d2:d3:5c:27:30:c3:75:c6:81:1d:53:ab:33:31:c7:ea:aa:57:a2:fb:7b:f4:c4:ee:52:ea:b3:98:21:21 |
| ember-relay.invalid | 2026-09-28 07:31 | Tidepool Registrar | 203.0.113.45 | Quayside Trust CA | 372 | 6a:02:c0:7d:63:f4:19:e8:3a | b2:37:77:4e:de:5c:09:7b:c9:fa:59:22:e4:69:d0:15:9d:a5:62:a5:72:ce:f3:39:ab:6b:df:18:97:eb:41:6a |
| 203.0.113.62 | 2026-10-05 06:31 (first seen) | Reedmere Hosting, AS64500 | - | Quayside Trust CA | 372 | 6a:02:37:b1:08:5e:aa:9d:12 | 73:17:d2:d3:5c:27:30:c3:75:c6:81:1d:53:ab:33:31:c7:ea:aa:57:a2:fb:7b:f4:c4:ee:52:ea:b3:98:21:21 |
| 203.0.113.45 | 2026-10-05 08:09 (first seen) | Reedmere Hosting, AS64500 | ember-relay.invalid | - | - | - | - |
| kiln-cache.invalid | 2025-08-11 06:44 | Tidepool Registrar | 203.0.113.88 | Quayside Trust CA | 372 | 6a:02:5d:e2:94:0b:71:c6:2f | e7:62:bb:9a:97:29:d2:70:b8:0a:8e:23:a3:32:97:51:9f:2d:d7:1b:2f:c9:b7:70:1c:ef:39:db:c3:0c:18:3a |
| vapor-sync.invalid | 2025-08-11 07:09 | Tidepool Registrar | 203.0.113.94 | Quayside Trust CA | 372 | 6a:02:ee:19:a7:36:4c:d0:85 | a6:7e:a9:43:86:66:4c:7f:54:32:17:44:46:af:4b:e8:31:b4:db:1b:08:a3:c8:9d:11:49:f3:09:4d:ea:91:ab |
| cinder-relay.invalid | 2025-08-18 06:57 | Tidepool Registrar | 203.0.113.97 | Quayside Trust CA | 372 | 6a:02:08:cb:52:fd:63:a1:9e | 95:50:50:d8:71:69:0f:ee:82:89:2e:4a:3b:68:6d:70:81:25:f6:40:87:ab:b2:9f:bd:29:45:90:91:62:9c:01 |
| gull-nest-4.invalid | 2024-05-17 10:03 | Bulkhaven Registrar | 198.51.100.140 | Brackish Free CA | 90 | 0f:48:d2:7a:ab:31:c9:06:e4 | 7d:b4:cf:01:62:84:75:69:21:8b:bd:a5:69:d3:d4:3e:e1:64:23:7c:ad:6e:21:e2:de:20:a3:28:f7:94:f7:2c |
| gull-nest-9.invalid | 2024-05-17 10:03 | Bulkhaven Registrar | 198.51.100.141 | Brackish Free CA | 90 | 0f:48:d2:7a:ab:31:c9:11:f0 | 7e:c4:0e:50:78:80:f1:ab:74:da:1b:ae:42:16:c5:78:26:01:34:d5:ac:73:f6:03:a7:cd:cc:27:dc:a8:ac:ad |
| gull-nest-12.invalid | 2024-05-17 10:04 | Bulkhaven Registrar | 198.51.100.142 | Brackish Free CA | 90 | 0f:48:d2:7a:ab:31:c9:2d:07 | ab:d8:e1:80:cb:6a:2b:3a:c9:60:c9:0c:ab:b4:cb:22:ec:65:71:ea:b1:12:a0:96:55:06:20:0c:ee:fc:5c:16 |
| reed-mirror.invalid | 2024-10-16 14:22 | Floeline Registrar | 198.18.4.21 | Quayside Trust CA | 365 | 31:9c:b4:60:1d:e7:82:af:56 | d6:43:9f:cc:98:ac:2d:bf:f8:0f:97:9e:73:12:a3:21:ec:3e:14:24:e2:26:11:d6:45:05:42:26:e0:14:c9:24 |
| 198.18.4.21 | 2024-10-16 14:30 (first seen) | Reedmere Hosting, AS64500 | reed-mirror.invalid | - | - | - | - |

**Notes.** A bare address has no registration date; the date shown is when the record collection first saw it. A dash means the collection holds no record. AS numbers are from the documentation range.

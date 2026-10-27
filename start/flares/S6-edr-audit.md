# S6. The EDR and audit log

*Flare 3 · HTA SOC export and QF Studio's audit trail · TLP:AMBER*

*Deep in the plant the valves are cold and the logs are thin. Say only what you can prove.*

## Process and logon events

| When (UTC) | Host | Event | Detail |
|---|---|---|---|
| Tue 6 Oct 06:52:14 | jmp-dmz-1 | Logon, remote session (type 10) | Account `pip.rookwood`, source `wks-r4-12`. First use of this account on this host. |
| Tue 6 Oct 07:10:03 | ews-2 | Logon, remote session (type 10) | Account `pip.rookwood`, source `jmp-dmz-1`. |
| Tue 6 Oct 07:24:37 | ews-2 | Process start `QFStudio.exe`; file open | Project folder `D:\Projects\Deepvent\Unit2_Governor\` opened in the same remote session. |
| Tue 6 Oct 07:41:20 | ews-2 | Process start `tar.exe` (built-in archive tool) | Reads the project folder; writes `u2gov.zip` to `\\jmp-dmz-1\share$\`. |
| Wed 7 Oct 06:48:51 | ews-2 | File write | `D:\Projects\Deepvent\Unit2_Governor\Unit2_Governor_backup.st` saved by `QFStudio.exe`. |
| Wed 7 Oct 09:40:12 | wks-r4-12 | EDR alert | Periodic outbound connections from `QFStudioHelper.exe` in `%PUBLIC%\Libraries\`. |
| Wed 7 Oct 10:05:00 | wks-r4-12 | Host isolated |  |
| Wed 7 Oct 10:20:00 | wks-r4-12 | Memory image taken | Files in `%PUBLIC%\Libraries\` quarantined. |

No unknown executable ran on `jmp-dmz-1` or `ews-2`: the activity there used the engineer's account and built-in tools. The EDR agent was installed on level 3 and above on Monday 21 September and records process, logon and file-access events.

## QF Studio's audit trail (`ews-2`)

| When (UTC) | Event | Object | Detail |
|---|---|---|---|
| Tue 6 Oct 07:24:40 | Project opened | `Unit2_Governor` | user `pip.rookwood` |
| Tue 6 Oct 07:25:02 | Project exported to Structured Text | `Unit2_Governor` (read-only export) | user `pip.rookwood` |
| Wed 7 Oct 06:48:51 | Project saved | `Unit2_Governor_backup.st` | user `pip.rookwood` |
| (none) | Download to controller | - | No download event is recorded for any controller between Mon 5 Oct and Thu 8 Oct 11:00. |

## Levels 2 and 1

The HMI and controller logs are 24-hour ring buffers. HTA exported them for the first time on **Thursday 8 October at 11:00**, so they begin on **Wednesday 7 October at 11:00**: after every event above. They cannot say whether anything happened on those levels before then.

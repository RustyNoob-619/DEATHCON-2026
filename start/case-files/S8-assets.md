# S8. HTA's assets by Purdue level

*Case file · start set · TLP:AMBER · supplied by HTA's engineering office*

HTA's zones and assets by Purdue level, with how long each level keeps its logs. It lists no events. The map in Figure 3 (`figures/fig3.png`) is drawn from it.

| Level | Zone | Assets | Role | Logs kept |
|---|---|---|---|---|
| 5 | Enterprise | Mail gateway `mail-gw1` | Inbound and outbound mail | 90 days (headers and attachment traces) |
| 5 | Enterprise | Web proxy `proxy-r4` | Web access for the R&D network | 60 days |
| 4 | Site business | R&D workstations `wks-r4-01` to `wks-r4-24` (including `wks-r4-12`) | Engineers' desktops | 60 days (EDR and file-access) |
| 3.5 | DMZ | Jump host `jmp-dmz-1` | The only route from level 4 into operations | 30 days |
| 3 | Operations | Engineering workstation `ews-2` (QF Studio) | Controller projects, downloads to controllers | 30 days (EDR and file-access); QF Studio keeps its own audit trail |
| 3 | Operations | Historian `hist-1` | Process history | 30 days |
| 2 | Supervisory | HMIs `hmi-t1` and `hmi-t2` | Operator panels for the three units | 24-hour ring buffer |
| 1 | Control | QF-400 governor controllers, units Skerry, Brine and Caldera | Governor control of each vent turbine | 24-hour ring buffer |
| 0 | Process | Vent turbines, thaw valves | The physical plant | None |

## Conduits

| Between | Route |
|---|---|
| Level 4 to the DMZ | Remote-session gateway to `jmp-dmz-1` only |
| DMZ to level 3 | Engineering sessions from `jmp-dmz-1` to `ews-2` |
| Level 3 to levels 2 and 1 | QF Studio's download path to the controllers; logged by QF Studio's audit trail and the controller's own ring buffer |

**Note.** Logs on levels 2 and 1 are ring buffers that overwrite themselves every 24 hours. HTA exports them only on request, with a vendor tool.

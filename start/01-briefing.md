# HTA-2026-1005: the briefing

*Case HTA-2026-1005 · Handling: TLP:AMBER, Undercurrent only · Everything in this case is invented: the world, the people, the vendor and the adversaries.*

## 1. Tasking

**To:** SWORD analysis cell. **From:** the Floe Assembly's Infrastructure Council. **Case:** HTA-2026-1005.

The ice has cracked at Hollow Rookery, and something has been swimming under it. You are analysts of SWORD, the Security Weaponisation & Operational Research Department. For a decade we have tracked the creatures that prey on the colonies, under our Rules of Engagement; we run counterintelligence, defensive and, under strict authority, offensive; and we are known across the critical-national-infrastructure community for warnings sent over the Undercurrent that reached rookeries before the wreckage did. You write the nets (YARA rules) that tie an adversary to its own tradecraft, and the Hold is yours to fish.

**Your objective is to use YARA rules, and everything else on the platform, to positively identify the malware samples in this case and to say whose tradecraft they carry.**

The Council wants, by Friday 9 October: **who is behind this, how sure you are, what the Warmgrid should detect, and what the Council should do.**

## 2. Preliminary incident summary

**HTA-2026-1005** (Lowtide Incident Response for the Hollowvent Thermal Authority, Thu 8 Oct 2026, TLP:AMBER)

**What happened.** On Monday 5 October a look-alike email reached three engineers of the Deepvent Project. One opened the attachment on `wks-r4-12` at 07:58 and followed its instructions. A beacon to `203.0.113.45:8443` was detected on Wednesday at 09:40 UTC and the host isolated at 10:05. LIR recovered a document, a ZIP with a shortcut and a decoy PDF, a loader DLL and a memory image of the running implant. **The PowerShell stage was not recovered when this summary was written.** On Tuesday and Wednesday the intruder reached the engineering workstation `ews-2` (level 3) and a modified copy of the `Unit2_Governor` PLC program was found there (the log arrives with Flare 3).

**Mail.** Mon 5 Oct 07:41 UTC, from `support@quillfeather-support.invalid`, to three engineers; subject *QF-400 governor firmware 4.2.1: update procedure required before Thursday's maintenance window*. Quillfeather Controls confirms it did not send it. The gateway kept the headers and a trace of the attachment, not the file (case file S1).

**Network.** Mon 07:59: `wks-r4-12` downloaded `QF400_4.2.1_Update.zip` from `flue-cache.invalid`. Mon 08:04: it requested `qfsync.ps1` and then `qfcore.dll` from `steam-relay.invalid`. From 08:09, beacons to `203.0.113.45:8443`, about every 20 minutes (proxy excerpt: case file S9).

**Process tree.** `explorer.exe` > `cmd.exe` > a hidden `powershell.exe` (the script ran from memory and was not kept); a copy of the legitimate `QFStudioHelper.exe` appears in `%PUBLIC%\Libraries\` and loads `qfcore.dll` (08:05). A memory image of that process was taken at 10:20; the implant carved from it is in the Hold.

**Operations network.** On Tuesday and Wednesday the intruder worked on `jmp-dmz-1` (the DMZ jump host) and `ews-2`. The events, the logs and what they can and cannot show arrive with Flare 3.

**Neighbour.** Rockhopper Reach Power Co-op reports activity on Monday and Tuesday from a different initial access and shares network indicators only (arrives with Flare 2).

**Preliminary assessment (automated enrichment, not analyst-reviewed).** A mutex, a user agent, an RC4 key and a Rich-header hash in `qfcore.dll` match a published Meridian report on **CRIMSON PETREL**. Confidence: *high*.

**Handling.** Under its retainer terms LIR keeps the original bytes of everything it recovers. What reached SWORD is LIR's **analysis record** of each item: the strings, structure fields and fingerprints that the platform's analysers read from it. Those records are in the Hold, found and read like any other sample; there is nothing in them to execute. LIR was still unpacking the memory image when this summary was written, so anything it calls "not recovered" may since have reached the Hold. The Hold also holds real malware samples: never execute anything from it, and do not upload anything from it to a public service.

## 3. What you are working with

- **The Hold** is the platform's corpus: real malware and goodware, and the records of this case, all together. Nothing marks which is which, and which samples belong to the case is part of the work. The case files give you traces (names, hash prefixes, times); the rest you establish from the records themselves, and you say how sure you are. A real sample that resembles the case is a lead to test, not a member of the case.
- **What a sample shows.** The **Overview**, **Strings**, **Module data** and **Similar** tabs and the **Pebble Lab** work from what the platform's analysers read from a sample. The **Hex blobs**, **Disassembly**, **Behaviour** and **YARA hits** tabs need further analysis and are empty for some samples. Write rules from strings and module fields (the analysts' guide says what a rule can see).
- **Case files** are handed to you outside the platform. They hold what the platform cannot: the email, the proxy log, HTA's asset sheet and, as the watch goes on, LIR's notes, the neighbour's advisory and the audit log.
- **Names.** A search for a single word, such as `orca` or `umbral`, may also find real entities in the Hold. Any overlap between the names, hosts or samples of this case and the real world, including open-source intelligence, is purely coincidental and is not evidence. **Do not use open-source intelligence to complete this exercise.**

## 4. Rules of Engagement for this exercise

1. **Defensive scope.** You analyse and you write. You do not contact, probe, scan, sinkhole or disrupt any party's infrastructure, or submit an indicator to a service that fetches it, and your recommendations are written, not executed.
2. **Stay inside the evidence.** Work from the Hold, the case files and the platform. Do not use open-source intelligence (web searches, public reports, threat-intelligence feeds, online sandboxes, passive-DNS or certificate services) to complete the exercise: the names and values here are invented, and a real-world match would be a coincidence, not evidence. A real sample in the Hold that resembles the case is a lead to test inside the platform, not proof by resemblance.
3. **Method over names.** Do not infer anyone's origin or nationality from a language, a schedule or a phrase.
4. **Layers.** Say which layer a value sits in and who set it before you count it.
5. **Detect or attribute.** For every rule, state which job it does. A rule that detects is not evidence of who wrote the code.
6. **Honest wording.** Mark every link on your chain as proven, assumed or unknown, and give a confidence word with every judgement.
7. **Share carefully.** Anything you send over the Undercurrent carries a TLP marking and says what partners may block and what they must not attribute.
8. **Closed test.** The rules you write here are exercise material for a closed test, not production detection.

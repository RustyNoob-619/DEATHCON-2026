# Tasks

*Core tasks (★) are done by every cell. Extensions (◇) are for fast cells. "Start" is a pointer to a feature or a search, never an answer. "Feeds" shows where a task's result is used later. Each task opens with a one-sentence dispatch in the world's voice, then the plain instruction.*

**Every task ends the same way.** Add what you found to your evidence board (the template: item, where found, layer, setter, cost to fake, does it contradict the file it sits in?) and update your chain board. The reasoning is done as you go, and task 6.1 starts from the finished boards.

## The clock

| Phase | Starts at |
|---|---|
| Phase 0: Briefing | 0:00 |
| Phase 1: Triage the delivery items | 0:05 |
| Phase 2: Read the stager and the loader | 0:35 |
| Phase 3: The missing link | 1:20 |
| Phase 4: The neighbour and the code | 2:20 |
| Phase 5: Reach into OT, and the SOC's rule | 3:00 |
| Phase 6: Assessment and sharing | 3:25 |
| End of the hands-on part | 4:00 |

These are budgets for a cell of three who split the work. New case files are released at the start of phases 3, 4 and 5.

The figures are in `figures/`: Figure 1 (the chain, with its gaps), Figure 3 (the Purdue map of HTA), Figures 5a to 5e (the five diamonds, also on the profiles) and Figure 6 (the blank incident diamond).

## Phases

### Phase 0: Briefing

*The facilitator reads the tasking aloud before the clock starts. The briefing, the glossary and Figures 1 and 3 reach you the day before.*

- **0.1★ Orientation.** *Dispatch: The courier has landed and the seal is broken. Before you touch the Hold, learn where the nets are kept.* Three platform warm-ups: in Dive, search `type:pe class:malware`, note the count, open any result and name its tabs (some are empty for some samples); open the Pebble Lab, paste the supplied smoke rule (it is in the rules part of the analyst guide, and it matches any PE file) and press Run on corpus: read how the counts, the malware and goodware split, the file types and the time are shown. *Feeds 3.3.*

### Phase 1: Triage the delivery items (E, 1a, 1b)

- **1.1★ The email.** *Dispatch: A letter came in on the tide wearing a vendor's feathers. Find out who really sent it.* Read the email (S1). List every trace it keeps of the attachment it no longer holds (name, size, a hash prefix), every sign that the sender is a look-alike, and what the message asks. What do you know about the attachment, and what do you not? *Start:* the header block and the gateway annotation. *Feeds 1.2.*
- **1.2★ Find the instruction document.** *Dispatch: The gateway kept the attachment's shadow. Find the thing that cast it.* Use the traces to find the document in the Hold, and say how sure you are it is the right one. Then read it: where does its link lead, which relationship layout does it use, and what else in the Hold is built like it? *Start:* the hash-prefix search (`sha256:<prefix>*`), then the Overview and Module data tabs (`ooxml`) and the fingerprint `office_rels_layout` (click a fingerprint to search for it). *Feeds 2.1 and 6.1.*
- **1.3★ The update package.** *Dispatch: Three items rode in one bundle. Open them all, and trust none of them yet.* Open the ZIP (`QF400_4.2.1_Update.zip`), the shortcut (`QF400_4.2.1_Release_Notes.pdf.lnk`) and the decoy PDF (`QF400_4.2.1_Release_Notes.pdf`). What does the shortcut run (read its whole argument string in Module data)? Read its machine name and volume serial. Which sample shares them, and what does that tell you? In the PDF (case file S7), which statements are specific to HTA? Compare them with what HTA publishes (S10). Mark E, 1a and 1b on your chain board. *Start:* `lnk_machine:*`, the shortcut's Similar tab, the `zip` member list, S7, S10. *Feeds 2.1 and 6.1.*

### Phase 2: Read the stager and the loader (2, 3)

- **2.1★ The missing script.** *Dispatch: The report says a script went missing. Scripts do not wander off on their own. Find it.* The incident summary says the PowerShell stage was not recovered, but the proxy excerpt (S9) shows it being fetched, and its record is in the Hold. Find it from what the shortcut's argument string and the proxy name, show what ties the script to the shortcut, then read its Strings tab: how is the script written, and what does its staging note say? Who else in the Hold writes scripts that way? Update your chain board. *Start:* the shortcut's arguments, S9, `name:` and `domain:` in Dive, the script's Strings and Similar tabs. *Feeds 2.2 and 3.2.*
- **2.2★ Read the loader.** *Dispatch: Take the loader apart on the ice and lay every part where the Council can see it.* Open `qfcore.dll`. On Module data read every group of fields the platform parsed for it, from the headers to the resources. On Strings find the configuration values and the strings that look like messages from a routine (Rare only, Rarest first). On the Overview read the fingerprints. List every value that stands out, say which you would trust and which you would not, and why. Then read the Similar tab: record every sample ranked above a score of 10 with its score and the fingerprints behind it. Do not decide yet. *Start:* Module data (hover a row for its YARA path), Strings, the Overview's fingerprints, Similar. *Feeds 3.1 and 6.1.*

### Phase 3: The missing link (4, 4')

*Flare 1 is released at the start of this phase (S2, S3).*

- **3.1★ Link the implant to the loader.** *Dispatch: Two catches that look cut from one cloth. Prove it, or say you cannot.* The implant (`wks-r4-12_qfhelper_pid2208.bin`) is in the Hold; the memory image was taken from the process that loaded the DLL. Using shared fingerprints (`function_hash:` for the decoder) and the strings both records carry, say what you can **prove** and what you can only **assume** about how the DLL and the implant relate, and what would close each assumption. Update your chain board. *Feeds 4.2 and 6.1.*
- **3.2★ The command host.** *Dispatch: The implant keeps a letter folded small inside itself, and LIR has unfolded it. Read it against the catch.* S2 is LIR's note on the implant's configuration and S3 holds three captured beacons, both as text. Compare the record's layout with the format strings on the implant's Strings tab. Which host does it name, which campaign, which interval? Compare the beacon times with the proxy excerpt (S9) and the user agent with what the loader says. List what each field tells you and what it contradicts elsewhere in the case. *Start:* S2, S3, S9, the implant's Strings tab. *Feeds 4.1, 4.2 and 6.1.*
- **3.3★ YARA 1: a tradecraft rule.** *Dispatch: Cast a net for the decoder's voice, and mend the mesh until it catches only what it should.* Write a rule from the strings the loader's decoder leaves behind. Choose them on the Strings tab (the "In corpus" column says how many samples carry each string; a filter such as Rare only can hide the strings you want) and use the file-type guard from the analysts' guide. Run it on the corpus and log it: hits, how many are goodware, and any hit that is not a sample you expected. Which samples do you expect it to hit (the loader, and what you have shown relates to it), and does it? For each hit you did not expect, open it and say whether it belongs to this case and why it matches. Is it a rule that **detects** or one that **attributes**? *Start:* Strings, the Pebble Lab, the rule-log template. *Feeds 5.2 and 6.3.*

### Phase 4: The neighbour and the code (infrastructure and code similarity)

*Flare 2 is released at the start of this phase (S4, S5).*

- **4.1★ Neighbour indicators and infrastructure.** *Dispatch: The neighbour sends smoke signals but will not say how the fire started. Read what they sent.* Read the neighbour's note and indicators (S4) and the infrastructure sheet (S5). Pivot each indicator: which match the incident, which match the Hold, which match nothing? Look at what repeats across the rows. What could each indicator that matches nothing be? The neighbour got in by a different door: what does that change in your hypotheses? *Start:* `domain:` and `url:` in Dive, the Food Web, S5's columns. *Feeds 4.2.*
- **4.2★ YARA 2: a rule from the implant's own strings.** *Dispatch: Fingerprints catch only what the platform already knows to look for. Go deeper than the catalogue.* The platform links samples by fingerprints, but the strings of a timing or planning routine carry none. On the implant's Strings tab sort by **Rarest first** and look at the strings that only a few samples carry; choose the ones that belong to a routine that plans a schedule, and write a rule from them and run it on the corpus. Which samples hit? For each hit you had not seen before, say what it is, what its Similar tab says and whether anything in the chain explains it. Then make a deliberately shorter version of the rule: keep only the string that mentions a seed, and run that too. What changes, and what does it cost? Update your chain board. *Start:* Strings (Rarest first), the Pebble Lab. *Feeds 5.2 and 6.1.*

### Phase 5: Reach into OT, and the SOC's rule

*Flare 3 is released at the start of this phase (S6).*

- **5.1★ Reach into OT.** *Dispatch: Deep in the plant the valves are cold and the logs are thin. Say only what you can prove.* Read S6 (the process tree, logons, the archive and the save, QF Studio's audit trail). Place every event on the Purdue map (Figure 3, drawn from the assets in S8) by level. Compare the modified PLC program (`Unit2_Governor_backup.st`) with the legitimate one (`Unit2_Governor_v12.st`): what was changed or added, and was it ever downloaded to a controller? What is **proven** below level 3, what is **assumed**, and what evidence would close the gap? *Start:* `name:Unit2_Governor*` for both programs, the Strings tabs of both programs side by side, S6. *Feeds 6.1.*
- **5.2★ YARA 3: the SOC's rule.** *Dispatch: The SOC cast its net early and is proud of the haul. Count the fish, then ask whether they are the right fish.* The SOC supplies a rule built from two strings the platform lists for the loader (it is in the rules part of the analyst guide). Run it on the corpus. List every hit. What does the rule **detect**, what does it **attribute**, and does the second follow from the first? Then say which of your own two rules (3.3 or 4.2) should replace it as the attribution rule, and why (reuse their log lines; no new scan is needed). Log it. *Feeds 6.3.*

### Phase 6: Assessment and sharing

- **6.1★ ACH and diamond.** *Dispatch: Lay the evidence on the ice and weigh each piece by what it cost the one who put it there.* In your cell, finish the chain board (every stage names the sample you hold for it, by hash prefix, and how sure you are), then read your evidence board top to bottom and mark anything you suspect was put there to mislead. Build the ACH matrix: your evidence against the five hypotheses, with cost-to-fake weights. Which two or three items discriminate the most? Fill the four vertices of the incident diamond (Figure 6) and its timestamp (M1) and methodology (M5) cells, **adversary vertex last**; the other meta-features are optional. *Feeds 6.2.*
- **6.2★ Write the assessment.** *Dispatch: Put your name to a judgement and say how far the ice will bear it.* In 200 words or fewer: judgement, confidence word, key evidence, alternatives, what would change your mind. Add five collection steps, in the platform and beyond. And say what you would tell the Council to do tomorrow, and what you would not tell them.
- **6.3★ Rule pack and sharing note.** *Dispatch: A net is only worth lending if you say what it catches and what it must never be used to name.* Package your rules (3.3, 4.2 and the one you would put in place of the SOC's in 5.2) with their log lines (hits, unexpected hits, goodware hits, layer, cost to fake, confidence, detection or attribution). Write a 100-word note for the Undercurrent with a TLP marking, what partners may block, what they must **not** attribute, and what you are still unsure of.

### Extensions (not in the timing)

- **3.4◇** Five lines on what the implant probably does, from static evidence only (its imports, its strings, the configuration grammar).
- **4.3◇** *Describe, do not query.* Say which passive source you would consult in a real case for the hosts and addresses in this case (passive DNS, certificate transparency), what you would expect it to return, and what "not found" would mean. **Run no lookup:** the names here are invented, and Rules of Engagement 1 and 2 forbid submitting them to a service or using open-source intelligence.
- **4.4◇** When your 4.2 rule has found a record you had not seen, ask the facilitator whether LIR has anything on it. If it does, what does it give, and where have you seen it before?
- **5.4◇** Triage the other Hold records: for five of your choice, say whether they are strongly, mediumly, weakly or not linked to the incident, and what the link is made of.
- **6.4◇** Three hunting queries and an indicator list tagged by layer and confidence, with a list of what *not* to block.

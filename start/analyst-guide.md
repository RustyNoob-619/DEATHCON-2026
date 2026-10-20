# Analyst guide: how a Capstone works, the Pebble Lab and the rules

*Sections 1 to 11 are general guidance for every Capstone and say nothing about a particular case. Sections 12 and 13 are about the Pebble Lab and the rules that come with this case. Read it first and keep it open.*

## 1. What a Capstone is

A Capstone is one case worked from first sight to a written judgement, using only the platform and the pages you are handed. You get a briefing, records in the Hold (among the real samples, with nothing to tell them apart but the evidence), case files that the platform cannot hold (emails, logs, notes from partners) and templates for your boards. You hand in an assessment, the rules you wrote and a sharing note.

Nothing in a Capstone runs, contacts or scans anything. What you work with is the platform's analysis of each sample (its strings, its parsed fields, its fingerprints), never the file itself. You are marked on reasoning, layer discipline, rule quality and honest wording. A correct name with weak reasoning scores less than a hedged name with strong reasoning.

## 2. Ground rules that apply to every Capstone

1. **Defensive scope.** You analyse and you write. You do not contact, probe, scan, sinkhole or disrupt anyone's infrastructure, and you do not submit an indicator to a service that fetches it. Your recommendations are written, not executed.
2. **Stay inside the case.** Work from the Hold, the case files and the platform. The briefing says whether outside sources are allowed; if it does not say so, they are not.
3. **Method over names.** Never infer anyone's origin or nationality from a language, a schedule or a phrase. Those are habits of an operator, and they are cheap to copy.
4. **Never execute anything from the Hold,** and do not upload anything from it to a public service.
5. **Closed test.** Rules you write in a Capstone are exercise material. They are not production detection.

## 3. The working loop

1. Read the briefing and its Rules of Engagement. Note what you are asked to deliver and by when.
2. Start your **chain board**: one row per link between stages, each marked proven, assumed or unknown.
3. Work the tasks in order. After each task, add what you found to your **evidence board** and update the chain board. The board is the reasoning; the assessment is its summary.
4. When a task asks for a rule, run it, read every hit (not just the count) and write a line in your **rule log** before you move on.
5. Near the end, build the **ACH grid** and the **diamond** from the finished boards, then write the assessment and the sharing note.

## 4. Layers, setters and cost to fake

Every value you find sits in a **layer** and was **set by** someone. Say both before you count it.

| Layer | Typical contents | Typical setter |
|---|---|---|
| Delivery | Emails, documents, shortcuts, archives, lures | The operator, or the builder of a kit |
| Staging | Scripts, downloaders, wrappers | Often a builder (a tool or a kit) |
| Payload | Loaders, implants, their routines and settings | The developer |
| Infrastructure | Domains, addresses, certificates, hosting | The operator |

The **cost to fake** is what it would cost someone else to copy the value. A string that every build of a public library carries is cheap. A routine that exists in one author's code only is expensive. A value in the outer layer of a file is usually cheaper than a value deep in its code. When two values in the same file disagree about who made it, suspect the cheaper one.

Three habits keep you honest:

- **Builder matches count once.** A kit, a packer or a template shared by many customers tells you about the seller, not the customer.
- **Test for internal consistency.** Do the toolchain, the timestamps, the imports and the strings of one file tell one story?
- **Persistence beats volume.** A habit that survives a year of builds is better evidence than ten matches on one afternoon's work.

## 5. Reading the platform

| Where | What it shows | Use it for | Traps |
|---|---|---|---|
| **Dive** (search) | Records matching a query | Pivoting from any value you read; finding a record from a trace | A hit count means nothing until you know what else carries the value. The Field Guide lists every field. |
| **Overview** | The record's fingerprints, strongest first | Clicking a fingerprint to find every record that carries it | Fingerprints only exist for what an analyser knows how to extract. A routine with no fingerprint is invisible here. |
| **Strings** | Every kept string, with how many records carry it ("In corpus") | Finding rare strings; building a rule | "Rare only" hides strings seen in more than a few records. The kind column is a pattern guess, not a meaning. The counts depend on the whole corpus. |
| **Module data** | Parsed fields (headers, imports, resources, properties) | Reading the toolchain; hover a row for its YARA path | A value can be copied from somewhere else. Check it against its neighbours. |
| **Similar** | Records ranked by shared fingerprints | A first list of relatives | It counts matches. It does not know who set a value or what it cost to fake, and a copied value ranks as high as an inherited one. |
| **Reports & chain** (Krill Chain) | Reports that mention the record and the stages they describe | Seeing how others laid the chain out | A report is somebody's reading, not evidence of yours. |
| **Food Web** | A graph of records, indicators and entities that share values | Spotting infrastructure that repeats | A shared provider is not a shared operator. |
| **Pebble Lab** | Runs YARA-X rules over the whole Hold | Testing a rule and reading the hits | Every run covers real samples too. Two scans run at a time. A rule can only match what a record keeps. |

Some tabs (Hex blobs, Disassembly, Behaviour, YARA hits) may be empty for some samples. That is not your mistake: section 12 says what a rule can and cannot see.

## 6. Detect or attribute

Every rule you write does one of two jobs, and you must say which.

- A rule that **detects** finds a thing. It is judged on its hits and its false positives.
- A rule that **attributes** ties a thing to the person who wrote it. It must be anchored on something only that author would produce.

Ask three questions of any rule: What is it anchored on? Who else could produce that? Would the hit list change if the author were somebody else? A rule built on a public routine, a shared library or a copied configuration detects faithfully and attributes nothing. Write the answers in your rule log.

## 7. Proven, assumed, unknown

Mark every link on your chain and every claim in your assessment:

- **Proven.** A file or a log shows it.
- **Assumed.** Something suggests it, but nothing shows it.
- **Unknown.** Nothing shows it either way.

For each assumed or unknown link, write what would close it. "A different log" is a good answer when you can name the log.

## 8. Confidence words, ACH and the diamond

- **Confidence words** are low, moderate and high. Give one with every judgement. They come from the cost-to-fake argument, not from a count.
- **ACH (analysis of competing hypotheses).** Rows are your evidence, columns are the hypotheses. Mark each cell consistent, inconsistent or neutral, weigh each row by its cost to fake, and add up the inconsistencies, never the consistencies. Keep items you suspect were planted in a separate block, because a false flag is built to push the tally the wrong way. The grid says how the evidence leans, not how sure to be.
- **The diamond** has four vertices (adversary, capability, infrastructure, victim) and meta-features (timestamp, phase, result, direction, methodology, resources). For every cell, write the attribute, the evidence, its layer, who set it, its cost to fake and a confidence word. Fill the adversary vertex last: it is a conclusion, not a starting point.

## 9. Writing it up

An assessment is 200 words or fewer:

1. The judgement.
2. One confidence word.
3. The two or three items that carry it, each with layer and cost to fake.
4. The alternatives you rejected, and why.
5. What would change your mind.

Outside the 200 words: five collection steps, in the platform and beyond, and what you would tell the customer to do next, and what you would not tell them.

## 10. Sharing: TLP

Every note you send outside your cell carries a TLP marking: CLEAR (public), GREEN (the community), AMBER (the recipients' organisations) or RED (named recipients only). A sharing note says four things: the marking and why, what partners may block or detect, what they must **not** attribute on, and what you are still unsure of.

Two rules of thumb: a rule's **hit list** is only as good as the corpus it was run over, and a detection rule shared as a courtesy is not an attribution rule.

## 11. Working in a cell

- One person owns the **rule log** and does the running in the Pebble Lab. Another keeps the **chain board**. The rest pivot and read.
- Sync at each release of new material (a flare). Compare boards, not conclusions.
- Hand in your filled templates when the facilitator asks. Pasting the Markdown tables is enough.
- A cell of two keeps the same minutes. Drop the optional parts first.

## 12. The Pebble Lab: what a rule can see, and how to read a run

The Pebble Lab runs real YARA-X rules over what the platform has kept of each sample. For many samples that is **attributes**, not bytes. Read this section before your first rule.

### What a rule can see

| You can write a rule from | Example | Where to read it |
|---|---|---|
| A string the analysers extracted | `$a = "job %u of %u done" ascii` | the sample's **Strings** tab |
| A module field | `pe.pdb_path contains "agent_build"`, `lnk.tracker_data.machine_id == "buildbox-07"` | the sample's **Module data** tab (hover a row for its YARA path) |
| The file-type marker | `uint16(0) == 0x5A4D` (a PE), `uint32(0) == 0x04034B50` (a ZIP or Office file) | how much of a file's start the platform keeps differs from sample to sample, so a byte test is approximate where the header is short |

Some samples have no code windows (their **Hex blobs** and **Disassembly** tabs are empty), and a pattern copied from another sample that has code will find nothing in them. If a rule finds nothing where you expect a hit, check which attribute you wrote it from. A result is marked approximate when a rule reads raw bytes (hex strings, regular expressions, byte offsets), because the platform keeps contexts, not files.

### Every run is over the whole Hold

**Run on corpus** (or Ctrl+Enter) always scans every sample the platform holds, real ones and the records of this case alike. The result gives the number of hits, how many are malware and how many goodware, their file types and the samples themselves.

- **Read the list, not just the count.** A hit you did not expect is either a record of this case you had not met or a real sample that carries the same attribute. Open it, read its Similar tab and say which, and why it matches.
- **Goodware hits are false positives.** One goodware hit is enough to say the rule is too broad to share.
- **Narrow a rule by changing the rule.** Add a second string, a module condition or the file-type guard; there is no other way to narrow a run.
- **Two scans run at a time.** A third waits: the message says "Another rule run is in progress", and you run it again in a few seconds. One person per cell does the running. A run can stop at the time limit with partial counts; the result says so.

### Starting points on the Strings tab

- **Rare only** shows strings that few samples carry and no goodware sample carries. **Rarest first** orders by how few samples carry a string.
- The **In corpus** column counts every sample that carries the string. A small **gw** number beside it counts goodware samples.
- **Rarest 5 to rule basket** and **Start a rule** build a rule from the rarest strings of the sample you are on. A starter rule is a place to begin: read what it catches before you trust it.

### Two reminders

- A rule that hits is not a rule that attributes. Say which job each rule does (Rules of Engagement 5).
- The Hold contains real malware. Nothing here executes anything, and you must not either.

## 13. The rules that come with the pack

Two rules and a skeleton come with the pack. Run them in the Pebble Lab like any other.

### The smoke rule (task 0.1)

Matches every PE file. Use it to see how counts, file types and time are shown.

```yara
import "pe"

rule smoke {
  condition:
    pe.is_pe
}
```

### The SOC's rule (task 5.2)

Written by the SOC after the automated enrichment: a key and a message that the platform lists for `qfcore.dll`.

```yara
rule soc_petrel {
  meta:
    author = "HTA SOC"
    description = "CRIMSON PETREL (preliminary)"
  strings:
    $key = "c4rR10n-P3tr" ascii
    $rc4 = "rc4k: key length 1..256 expected" ascii
  condition:
    any of them
}
```

### A rule skeleton

```yara
rule my_rule {
  meta:
    description = ""
    author = ""
    anchor = ""         // what the rule is anchored on, and who else could produce it
  strings:
    $a = "..."
  condition:
    uint16(0) == 0x5A4D and $a
}
```

## 14. Where to read more

- **Field Guide, Dive:** the query language and the field reference.
- **Field Guide, YARA-X:** the modules and how to write rules.
- **Field Guide, Platform:** getting around.
- Sections 12 and 13 above, and the case's **glossary**.

# GA4 CRO Insight Analyzer — Installation Guide

This is a **Claude Skill**: a packaged set of instructions that teaches Claude how to turn GA4 screenshots into structured, revenue-focused CRO reports. This guide covers how to install it, wherever you're using Claude.

---

## What's in the box

`ga4-cro-insight-analyzer.skill` is a zip archive (the `.skill` extension is just a naming convention — it's a regular zip file) containing:

```
ga4-cro-insight-analyzer/
├── SKILL.md                              ← entry point Claude reads first
├── references/
│   ├── methodology.md                    ← full analytical framework
│   ├── usage_guide.md                    ← screenshot tips & workflows
│   ├── output_schema.json                ← JSON output schema
│   ├── example_traffic_acquisition.md    ← worked example
│   ├── tool_manifest.json                ← config defaults & benchmarks
│   └── README.md                         ← background on the tool itself
└── assets/
    └── GA4_CRO_Report_Template.xlsx      ← starting template for Excel exports
```

You don't need to open or edit any of this — just install the whole `.skill` file as-is.

---

## Option A: claude.ai (web or desktop app) — easiest

1. Open **Settings → Capabilities** (may show as "Customize → Skills" depending on your account)
2. Click **"+"** → **"Create skill"**
3. Upload `ga4-cro-insight-analyzer.skill` directly — no unzipping or renaming needed
4. Make sure **Code execution and file creation** is toggled on in Settings, since Skills run through that feature
5. That's it. Start a new chat, upload your GA4 screenshots, and Claude will automatically use the skill when it's relevant (e.g. "audit my GA4," "diagnose this funnel," "give me a CRO report")

This also works the same way for **Claude Cowork**.

---

## Option B: Claude Code — for developers

Claude Code reads skills straight from your filesystem, so there's no upload step:

1. Unzip the file:
   ```bash
   unzip ga4-cro-insight-analyzer.skill -d ~/.claude/skills/
   ```
   (If your unzip tool complains about the `.skill` extension, just rename the file to `.zip` first — the contents are identical.)

2. Verify the folder landed correctly:
   ```bash
   ls ~/.claude/skills/ga4-cro-insight-analyzer/SKILL.md
   ```
   You should see the file. (Use `.claude/skills/` inside your project folder instead if you want it scoped to one project rather than available everywhere.)

3. Restart your Claude Code session, then run `/skills` to confirm it loaded.

---

## How to trigger it

Once installed, just talk to Claude naturally — you don't need to name the skill. Any of these will trigger it automatically:

- "Audit my GA4 screenshots"
- "Why is my funnel leaking?"
- "Check this traffic acquisition report"
- "Give me a CRO report for this account"
- Uploading GA4 screenshots and asking for insights, with no extra phrasing needed

Say "SINGLE" for a quick one-report read, or upload 2+ screenshots (or say "AUDIT") for a full cross-report analysis with correlations.

---

## A quick note on trust

Since a skill's instructions run automatically once triggered, it's good practice — especially for anything downloaded from outside your own team — to skim `SKILL.md` before installing. This one only reads GA4 data you provide and writes analysis/report files; it doesn't make network calls or run arbitrary shell commands.

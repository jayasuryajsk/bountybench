# Bounty Bench

## Abstract
This report documents a personal benchmark of Bugcrowd submissions. It summarizes outcomes, payouts, and model attribution at a high level without disclosing vulnerability details. The objective is to compare performance signals between two tooling setups in a controlled, non‑disclosing format.

## Data Source and Scope
The dataset is derived from Bugcrowd submissions dashboard snapshots. No API export was used. The reporting window spans December 28-30, 2025 and January 12-25, 2026, with the snapshot point as of January 25, 2026. Only program names and outcome categories are recorded.

## Definitions
Outcome categories are standardized as follows:
- Won: Accepted or paid submissions. Includes paid submissions still shown as pending/triaged.
- Rejected: Closed without acceptance.
- Duplicate: Marked duplicate.
- Pending/Other: Any remaining in‑progress or unresolved states.

Model attribution is assigned at the outcome level:
- codex-5.2-xhigh: All Won and Duplicate outcomes.
- opus 4.5 (Claude Code): All Rejected outcomes.
- Unattributed: Pending/Other outcomes.

## Methods
The analysis uses manual extraction from the UI and aggregates counts by outcome and model attribution. Percentages are calculated against total submissions (n = 23) and rounded to the nearest whole percent.

A domain-specific adjustment is applied:
- ClickHouse submissions shown as pending/triaged are counted as Won because payment was issued.

## Results
**Table 1. Outcome summary (adjusted)**

| Outcome | Count | Share of total |
| --- | --- | --- |
| Won (paid/accepted) | 14 | 61% |
| Rejected | 5 | 22% |
| Duplicate | 2 | 9% |
| Pending/Other | 2 | 9% |
| Total | 23 | 100% |

**Table 2. Model attribution (known)**

| Model | Count | Share of total |
| --- | --- | --- |
| Codex (wins + duplicates) | 16 | 70% |
| Claude Code (rejected) | 5 | 22% |
| Unattributed | 2 | 9% |
| Total | 23 | 100% |

**Payouts**
- Total payouts: $1,500

**Programs included**
- ClickHouse
- Immutable
- Mattermost
- Origin Energy
- Chipotle
- Internet Brands
- Zendesk
- Octopus Deploy

## Observations
- Claude Code (opus 4.5) is too eager to report issues that end up informational or non‑actionable.
- Claude Code is suitable for web app and API testing.
- Codex (codex-5.2-xhigh) performs best when it can read through codebases, especially in open‑source repos.

## Open‑Source Notes
- Codex found bugs in open‑source repositories. Some are duplicates.
- Disclosures will be made once issues are triaged or closed.

## Limitations
- No vulnerability details are disclosed, which limits external validation.
- No API export was available; the dataset is derived from UI snapshots.
- Some submissions remain unresolved and are reported as Pending/Other.
- Model attribution is a controlled assignment, not an automated attribution system.

## Revision Policy
This report will be updated as submissions close and disclosures are permitted.

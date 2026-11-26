# Editorial audit, November 2026

This folder records a full editorial review of the completed Revelation study (all 31 chapters, the glossary, and the index), done before the material goes out to a wider audience. It lives outside `content/`, so Quartz does not publish it.

## Files in this folder

| File | What it holds |
|---|---|
| `README.md` | This summary: scope, standards, decisions, and how to undo any part of the work. |
| `findings.md` | The working log, chapter by chapter: what was wrong, what was changed, and why. The second-pass results (errors the first pass introduced and how they were fixed) are at the end. |
| `changes-by-file.md` | Line counts for every file touched under `content/`. |

## How the work was done

1. **First pass (commit `11d5234`).** Every chapter's main note, Q&A, and Context file was read in full, followed by the glossary and the index. Each factual claim, quotation, and Scripture reference was checked against the biblical text and the primary sources the notes cite.
2. **Second pass (commit `837e7c0`).** Every first-pass edit was compared word by word against the original text on `main`, to catch errors the first pass introduced and anything it missed.
3. **Records commit.** This folder, plus the owner's decisions on the flagged items.

## Standards applied

- **Accuracy.** Wrong facts, misquotations, wrong verse references, and claims unsupported by the cited source were corrected. New historical or current-events details were checked against sources before being added.
- **The study's positions.** None of the study's interpretive positions were removed or reversed. Where a debated reading is stated as settled fact (the timing of the rapture, the Antichrist's origin, Babylon as Saudi Arabia, the fourth kingdom as an Islamic caliphate, the identity of the 144,000, and so on), the text now marks it as the study's reading and briefly names the main alternatives. That labeling is kept to about one per section.
- **Voice.** References to "the teacher" and "in the room" were removed. So were stock phrases that read as machine-written ("worth sitting with," "load-bearing," "genuinely") and the heavy em-dash style. The teaching voice is otherwise unchanged.
- **Format.** All chapters now share one structure:
  - an epigraph and an Overview
  - numbered sections
  - a Key Scriptures list in "Ref — description" form
  - a translation note
  - the standard intro and closing lines on the Q&A and Context files
- **Links.** Glossary links use `[[Glossary#Term|Display]]`. Every wiki link and glossary anchor resolves. Mentions of "the next session" or "a later session" now link the actual chapter.

## Owner decisions on flagged items (2026-11-25)

All of the following were approved as edited:

| Item | Location | What was done |
|---|---|---|
| "Allah = Satan" | Ch26 | Reworded: the study regards the god of Islamic end-times tradition as "a counterfeit behind which Satan stands." Islamic eschatology is attributed to the hadith rather than the Qur'an. |
| Saudi trafficking claim | Ch28 | Kept as the study's assessment, explicitly labeled as going beyond what the public record can prove. |
| Joel Richardson, *The Gospel of the Skull Crusher* | Ch30 | Title confirmed by the owner; text unchanged. |
| "Looking Ahead" to a session that was never held | Ch31 | Changed to "Looking Back." |
| Translation mix | Index; Ch25–31 footers | Ch1–25 quote the NIV and Ch26–31 the ESV. Notes state this; quotations were not converted. |
| Ark remains and flood geology | Ch04 | Durupınar "ark" claims and flood-geology evidence are presented as claims, alongside the mainstream assessment. |
| Kainam/Canaan conflation in Jubilees | Ch06 | Split into the two separate episodes Jubilees records (Jub 8:1–4 and 10:29–34). The study's conclusion about the giants in Canaan is kept, labeled as its reading. |
| Broad glossary and index edits | `References/Glossary.md`, `index.md` | Approved, even though the usual per-chapter rule is additions only. |

## Undoing or revisiting changes

All the work sits in three commits on `editorial-audit-2026-11`, so any part can be reversed.

- **Undo everything:** close the PR without merging. If it is already merged, `git revert` the three commits, newest first.
- **Undo one pass:** `git revert 837e7c0` (second pass) or `git revert 11d5234` (first pass). Reverting the first pass without the second will conflict, because the second pass edits the same lines.
- **Restore one file to its original:** `git checkout main -- "content/Chapter 06/i. The Divine Council and the Seventy Nations.md"` before merging, or `git checkout <commit-before-merge> -- <path>` after.
- **Look up one change:** search `findings.md` for the chapter, then run `git log -p --follow -- "<path>"` to see the exact before and after.

## Known limits

- Verse numbers were checked by hand where a passage was edited. Chapter numbers were checked by machine across every file, but verse numbers were not.
- Current-events statements in Ch19 and Ch28 reflect reporting available in November 2026 and will date. Each is marked "as of 2026" or "at the time of this session."
- The audio files at `/static/audio/chapter-NN.mp3` are hosted on Cloudflare, not in this repo. They were not part of this review.

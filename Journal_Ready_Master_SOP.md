# Journal-Ready Master SOP

## Purpose
Run a fixed, repeatable manuscript-refinement pipeline where only metadata and source files change (`paper_id`, `journal_id`, authors, manuscript, audit inputs).

## Variable Inputs (Per Paper)
- `paper_id`
- `journal_id`
- `authors` (names, affiliations, ORCID, corresponding author details)
- manuscript source file
- audit/prompt file
- journal workflow Excel database

## Constant Pipeline (Phases)
1. **Repository/Input Ingestion**  
   Load manuscript, audit input, author file, journal database.
2. **Audit Parsing**  
   Convert issues to structured amendment map.
3. **Journal Requirement Extraction**  
   Resolve journal rules from `journal_id` sheet.
4. **Skill Mapping**  
   Map tasks to fixed skill stack; no skipped modules.
5. **Scientific Improvement**  
   Strengthen rationale, methods clarity, discussion depth.
6. **AI + Plagiarism Reduction**  
   Improve naturalness while preserving scientific claims.
7. **References + DOI Validation**  
   Reconcile in-text citations, reference entries, DOI completeness.
8. **Statistical Validation**  
   Check reporting consistency, assumptions, effect-size transparency.
9. **Tables + Figures Alignment**  
   Ensure numbering, callouts, legends, end-matter compliance.
10. **Language Polish**  
    Journal-tone, readability, consistency.
11. **Final Compliance Gate**  
    Score readiness, risk, and outstanding limitations.
12. **Memory + Traceability Update**  
    Persist amendment log, phase state, and artifacts.

## Constant Skill Stack
- `academic-paper-critical-analysis-toolkit`
- `turnitin-2026-advanced-plagiarism-detection-system`
- `ai-writing-humanizer`
- `research-diagram-toolkit`
- plus journal workflow controller skills (`skill.md` / `controller.md` routing)

## Mandatory Output Bundle
- Final blinded manuscript (`.docx`)
- Title page (`.docx`)
- Cover letter (`.docx`)
- Audit report (`.md` or `.docx`)
- Compliance report (`.json`)
- Amendment log (`.md`)
- Reviewer readiness score (`.json`)
- Desk rejection risk (`.json`)
- Figures (publication-ready) + legends

## Gate Criteria (Default Targets)
- AI score: `< 10%` (or externally verified equivalent)
- Plagiarism score: `< 10%` (or externally verified equivalent)
- Reference accuracy: `100%` citation-reference mapping
- DOI completeness: `100%` where applicable
- Statistical validity: pass with transparent limitations
- Journal compliance: `>= 90%`
- Desk rejection risk: `< 5%` target

## Non-Negotiable Rules
- Never skip phases.
- Never overwrite source truth without traceability update.
- Never fabricate references/DOIs.
- Always log unresolved items explicitly in compliance outputs.

## Audit Prompt Binding (All Prompt Documents Must Land in Artifacts)
When `audit_prompt_docx` is provided (and any companion exemplar manuscript is listed in the run template), the controller must:
- Parse **every** numbered section, table, scorecard, placement rule, master revision block, and pre-submission checklist item from the audit prompt into the structured amendment map (Phase 1–2).
- Carry each item forward to explicit **pass/fail/partial** status in the amendment log, audit report, and compliance report (Phases 10–11); unresolved items must appear under `unresolved_items` with owner and next action.
- Treat the exemplar amended manuscript (when `paper_id` matches that run) as a **quality benchmark** for tone, section balance, anonymisation handling, and figure/table callouts—diff the working manuscript against it during Phase 8–9, without copying text verbatim (integrity).

## FIIB Business Review — P009 | J06 Enhancement Prompt (Full Implementation Cross-Walk)
**Sources:** `P009_FIIB_ManuscriptEnhancementPrompt.docx` (audit prompt); `P009_J06_FIIB_Amended_Manuscript.docx` (completed exemplar for the same paper title). **Audit reference:** P009_FIIB_AuditReport_v1. **Targets:** readiness ≥90/100; desk rejection risk below 5%.

### A. Strategic objective and scorecard (Prompt §1)
- Map the eight audit dimensions (Structure & Formatting; Research Quality; References & DOI; Plagiarism & Integrity; AI Content; Statistical Validation; Peer Review Simulation; Journal Matching) to compliance JSON fields.
- Prioritise bottlenecks called out in the prompt: **References & DOI**, **Peer Review Simulation**, **AI Content**—these must have explicit remediation tasks in Phases 4–7 and 9–10.

### B. Phase mapping (pipeline ↔ prompt)
| Pipeline phase | Prompt coverage |
|----------------|-----------------|
| Phase 1–2 Audit mapping | §1 scorecard, §2–4 directives, §6 master revision prompt, §7 checklist → structured tasks |
| Phase 2 Journal blueprint | §5.1 FIIB/SAGE figure-table rules; caption positions; greyscale; DPI |
| Phase 4 Scientific amendment | §3 major (Indian case 5.4; §6.4 reframe; case depth); §4.4 PRISMA narrative + §7.3 future research specificity |
| Phase 5 AI / plagiarism reduction | §4.1 AI-pattern reduction; §4.2 grey-literature statistic framing |
| Phase 6 References + DOI | §3.2 reference table (Accenture, Gartner, Capgemini, Kreger, Bughin, Lu, RBI); §4.2 McKinsey/WEF/Capgemini/Gartner attributions; no fabricated DOIs |
| Phase 7 Statistical / methods reporting | Word-count discipline §4.3; methodology transparency §4.4 |
| Phase 8 Tables + figures | §2.1–2.2 figures; §5 complete placement map; §5.3–5.6 Word embedding steps; Table 1/2 caption verification |
| Phase 9 Language polish | Journal tone; remove consultancy register in §6.4 per prompt |
| Phase 10 Compliance gate | §7 twenty-item checklist; projected score uplift table as **expected** not guaranteed |

### C. Critical — zero tolerance (Prompt §2)
1. **Figure 1 (PRISMA):** Embed at **end of Section 3**, after PRISMA protocol prose, before Section 4. Caption below, centred 10pt. In line with text; full column width; ≥300 DPI (600 preferred); PNG/TIFF. Caption: *Figure 1. PRISMA-Style Flow Diagram of Systematic Literature Review Protocol.* Source line: authors’ construction following PRISMA (Page et al., 2021). Flow must show Identification (Scopus, WoS, EBSCO) → Screening → Eligibility (exclusions per prompt) → Included counts.
2. **Figure 2 (dual-pathway framework):** Embed at **end of Section 4**, after integrated model paragraph, before Section 5. Caption below, centred 10pt; in line with text; full width; greyscale-safe; P1–P5 visible; P4 as conditional gate; SDG 8 / 9 / 16 convergence zone per prompt. Source: authors’ own construction.
3. **Double-blind anonymisation:** Remove identifying institution text from body acknowledgements; replace with withholding language; full acknowledgements **only** on separate title-page file.

### D. Major — required for 90+ (Prompt §3)
- **§3.1:** Add **§5.4 Indian Banking Sector: SBI and ICICI Bank** (400–600 words, Claim/Evidence/Interpretation/Implication) after §5.3; cite RBI digital lending 2023, SBI YONO / annual report, ICICI iMobile Pay, DPDPA 2023 vs EU/US framing; cross-reference in **§6 Discussion**.
- **§3.2:** Execute reference fixes: verify Accenture URL + retrieval date; Gartner specific report title + gated note if needed; verify/move Capgemini Smart Money URL or Internet Archive; Kreger (2024) Finextra → peer-reviewed substitute or retained with “industry trade source” note; remove Bughin / Lu if uncited in body; RBI → *Report of the Working Group on Digital Lending…* with publication URL and retrieval date.
- **§3.3:** Rename **§6.4** to *Implications for Practice: Evidence-Driven Propositions*; rewrite prescriptions as conditional, evidence-grounded statements (reskilling ↔ P4; sandboxing ↔ RBI/BIS; ESG ↔ SDG 16.6).

### E. Moderate — score uplift (Prompt §4)
- **§4.1:** Rewrite openings for §5.1–5.3 and paragraphs 3–4 in §6.3–6.4 to break rigid C-E-I-I rhythm; vary openers and sentence length; §6.3 narrative not bullet enumeration.
- **§4.2:** McKinsey USD 200–340B parenthetical anchor; WEF 44% + peer-reviewed companion; Capgemini 80% footnote precision; Gartner 30% labelled **industry forecast / analyst projection**.
- **§4.3:** Full word count (body vs references per FIIB rules); if body exceeds 10,000 words apply trim targets (§6.3–6.4; §2.4–2.5 overlap; transitions); aim **8,500–9,500** after adding §5.4.
- **§4.4:** **§7.3 Future research:** specify design, sampling frame, P4 measures (e.g. % tech budget reskilling; NIST AI RMF maturity), and analysis (SEM / multilevel, etc.) for P5 / median-split testing narrative.

### F. Figure and table placement — FIIB / SAGE (Prompt §5)
- Figures/tables **in body** at first mention proximity; **first in-text callout before** each object.
- Figures: caption **below**; Tables: caption **above** (bold 10pt); every object has **Source:** line; greyscale-safe; sequential independent numbering; avoid JPG for line art.

### G. Master revision sequence (Prompt §6)
Execute in order when automating: (1) anonymisation; (2) Figure 1 placeholder/embedding; (3) Figure 2 placeholder/embedding; (4) new §5.4; (5) §6.4 reframe; (6) reference hygiene; (7) AI-pattern rewrites; (8) §7.3 methods detail; (9) word-count pass; (10) caption/cross-reference verification.

### H. Pre-submission checklist — twenty items (Prompt §7)
Track individually in `compliance_report.json` / amendment log: F1 embedded; F2 embedded; acknowledgements anonymised in body; F1/F2 captions; Table 1/2 caption positions; §5.4 added + §6 cross-ref; §6.4 reframed; Bughin/Lu removed if orphan; Gartner/Capgemini labelled as industry forecasts in text; RBI specific report URL; §5–6 AI rewrites; §7.3 specificity; word count vs guidelines; greyscale figures; ≥300 DPI; callouts before objects; source notes on all figures/tables; full acknowledgements **title page only**.

### I. Exemplar amended manuscript (Prompt outcome reference)
`P009_J06_FIIB_Amended_Manuscript.docx` demonstrates implemented narrative structure (abstract through discussion), in-text Figure 1/2 references, case tables, and proposition table placement—use in Phase 8–10 for **structural and formatting** conformance checks against the same prompt set.

### J. J06 workflow database ↔ enhancement prompt (item-by-item)
For **Paper Id P009** and sheet **J06** in `Journal workflow Database.xlsx`, use the cross-walk in **`P009_J06_FIIB_Prompt_JournalDB_Alignment.md`** (same folder as this SOP): it maps prompt §7 (20 checks) and §2–§6 blocks to J06 rows, lists prompt-only and J06-only obligations, and defines a single closure rule so both artifacts stay consistent at submission.

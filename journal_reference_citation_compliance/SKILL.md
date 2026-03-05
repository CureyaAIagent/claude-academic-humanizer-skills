---
name: journal-reference-citation-compliance
description: >
  Validates references and in-text citations in academic manuscripts to ensure
  compliance with journal author guidelines. The skill checks citation style
  formatting, reference completeness, citation-reference matching, and
  adherence to journal submission requirements. It detects citation errors,
  formatting inconsistencies, missing references, and provides corrected
  reference formatting according to the required citation style.

version: "1.0"
author: CUREEYA

entry_point: system

capabilities:
  - Reference Formatting Validation
  - Citation Style Compliance
  - In-text Citation Detection
  - Citation-Reference Matching
  - Journal Author Guideline Compliance
  - Reference Completeness Check
  - Citation Consistency Analysis
  - Reference Formatting Correction
  - Bibliographic Integrity Verification

inputs:
  manuscript_text:
    type: string
    description: Full manuscript text including references.

  reference_section:
    type: string
    description: Extracted bibliography or reference list.

  target_journal:
    type: string
    description: Name of the journal for guideline verification.
    optional: true

  citation_style:
    type: string
    description: Citation style used by the manuscript (APA, IEEE, Harvard, Vancouver, MLA, Chicago).
    optional: true

system_prompt: |

  You are an Academic Reference Compliance Auditor and Journal Formatting Specialist.

  Your responsibility is to verify that references and in-text citations in a
  research manuscript follow the formatting and structural requirements of
  academic journals.

  The system must ensure that:

  - All citations are properly referenced.
  - Reference entries follow the correct citation style.
  - References contain complete bibliographic information.
  - Citation formatting matches journal author guidelines.
  - In-text citations correctly correspond to the reference list.

  The system must also recommend corrections to improve compliance with
  journal publication standards.

processing_pipeline:

  step_1_extract_citations:
    description: |
      Scan the manuscript and extract all in-text citations.

      Detect citation patterns such as:

      - Author-year format (APA/Harvard)
      - Numerical citations (IEEE/Vancouver)
      - Footnote-based citations (Chicago/MLA)

      Store each detected citation for matching analysis.

  step_2_extract_references:
    description: |
      Extract the reference list from the manuscript.

      Identify each reference entry and parse bibliographic fields:

      - author names
      - article title
      - journal name
      - publication year
      - volume
      - issue
      - page numbers
      - DOI (if available)

  step_3_citation_reference_matching:
    description: |
      Match each in-text citation with a reference entry.

      Detect the following issues:

      - citations present in text but missing in reference list
      - references listed but never cited
      - incorrect citation numbering
      - author-year mismatch
      - duplicate references

  step_4_reference_completeness_check:
    description: |
      Verify that each reference contains complete bibliographic details.

      Required elements include:

      - author names
      - publication year
      - article title
      - journal or book title
      - volume and issue
      - page numbers
      - DOI (when available)

      Flag references with missing information.

  step_5_citation_style_validation:
    description: |
      Validate formatting according to the specified citation style.

      Example rules:

      APA:
        Author, A. A. (Year). Title. Journal, Volume(Issue), Pages.

      IEEE:
        [Number] Author initials. Author surname, "Title," Journal,
        vol., no., pp., year.

      Vancouver:
        Author surname Initials. Title. Journal. Year;Volume(Issue):Pages.

      Identify formatting inconsistencies and deviations.

  step_6_journal_guideline_compliance:
    description: |
      Evaluate whether the manuscript references follow the
      author guidelines of the target journal.

      Verify:

      - reference ordering rules
      - citation numbering style
      - punctuation standards
      - abbreviation of journal names
      - DOI inclusion policies

      Flag any formatting violations.

  step_7_reference_consistency_analysis:
    description: |
      Detect inconsistencies across references.

      Common issues include:

      - inconsistent author name formatting
      - inconsistent capitalization
      - inconsistent journal abbreviations
      - mixed citation styles

  step_8_reference_correction_recommendation:
    description: |
      Generate corrected reference formatting based on
      the specified citation style.

      Provide properly formatted references
      and corrected in-text citation examples.

validation_rules:

  citation_integrity:
    - Every in-text citation must correspond to a reference entry.
    - Every reference entry should appear at least once in the text.
    - Citation numbering must follow sequential order (for numeric styles).

  formatting_rules:
    - References must follow the specified citation style.
    - Author names must be consistently formatted.
    - Titles must follow correct capitalization rules.
    - Journal names must follow standard abbreviation guidelines if required.

  completeness_rules:
    - Each reference must include core bibliographic components.
    - Missing fields should be flagged for correction.

analysis_outputs:

  citation_integrity_report:
    description: |
      Summary of citation-reference matching results.

      Includes:

      - total in-text citations
      - unmatched citations
      - unused references

  reference_formatting_report:
    description: |
      Evaluation of reference formatting quality.

      Includes detected style inconsistencies and formatting errors.

  journal_compliance_report:
    description: |
      Assessment of whether the manuscript follows
      the target journal's author guidelines.

  corrected_reference_list:
    description: |
      Fully corrected reference entries formatted
      according to the specified citation style.

  citation_correction_suggestions:
    description: |
      Suggested corrections for in-text citations
      that do not match the reference list.

risk_levels:

  compliant:
    description: >
      References and citations fully comply with journal guidelines.

  minor_issues:
    description: >
      Minor formatting inconsistencies detected.

  major_revision_required:
    description: >
      Significant citation mismatches or formatting issues detected.

final_output_format: |

  Reference and Citation Compliance Report

  Total In-text Citations: X
  Total References: X

  Unmatched Citations: X
  Unused References: X

  Formatting Errors Detected:
  - Reference 4 missing page numbers
  - Reference 7 inconsistent author formatting

  Journal Guideline Compliance:
  Moderate

  Recommended Corrections:

  Reference 4 (Correct Format Example):

  Author A., Author B. (2022). Title of Article.
  Journal Name. 15(2): 120-134.

  Citation Correction Example:

  Incorrect:
  (Smith, 2021)

  Correct:
  Smith et al. (2021)

  Overall Citation Compliance Score: 0–100

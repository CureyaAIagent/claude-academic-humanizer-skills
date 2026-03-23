---
name: comprehensive-citation-validation-engine
description: "End-to-end validation and correction system for academic manuscript citations and references, ensuring compliance with major citation styles and journal formatting standards"
topics: 
  - "academic-publishing"
  - "citation-validation"
  - "reference-correction"
  - "doi-integrity"
  - "journal-compliance"
  - "research-manuscripts"
license: "MIT"
visibility: "public"
version: "1.0"
mode: "Advanced Academic Validation + Expert Review"
---

## 📋 Description

This engine performs comprehensive end-to-end validation, correction, and enhancement of citations and references in research manuscripts while ensuring compliance with major citation styles (APA, IEEE, Harvard, Vancouver) and journal formatting guidelines. It combines automated checking with intelligent auditing to produce publication-ready references.

## 🔧 Inputs

manuscript_text: string               # Full text of the manuscript including in-text citations
reference_list: string                # Raw unstructured list of references at the end of the document
citation_style: string                # Supported: APA | IEEE | Harvard | Vancouver
enable_auto_correction: boolean       # Enable automatic fixing of errors where possible
strict_mode: boolean                  # Apply stricter matching thresholds if enabled
target_journal_guidelines: object     # Optional journal-specific formatting rules

## 📌 Processing Pipeline Overview

### Stage 1: Ingestion & Extraction

#### Step 1.1 – Extract In-Text Citations
actions:
  - parse_manuscript_text_using_regex_and_nlp
  - detect_all_in_text_citations
  - identify_style_specific_patterns
  - handle_complex_citation_structures

#### Step 1.2 – Parse Reference List
actions:
  - convert_raw_references_to_structured_metadata
  - extract_authors_years_titles_journals
  - handle_line_breaks_and_spacing_issues
  - process_special_characters_and_abbreviations

#### Step 1.3 – Normalize Metadata
actions:
  - trim_whitespace_and_remove_extra_punctuation
  - normalize_author_names
  - lowercase_dois_for_consistency
  - remove_redundant_information

### Stage 2: Matching & Verification

#### Step 2.1 – Match Citations With References
actions:
  - exact_author_year_matching
  - fuzzy_matching_with_threshold_0_85
  - identify_missing_references
  - identify_uncited_references
  - detect_mismatches_due_to_typos

#### Step 2.2 – Contextual Citation Validation
actions:
  - analyze_sentence_context_around_citations
  - flag_semantically_inappropriate_citations
  - detect_inappropriate_citation_placement

#### Step 2.3 – Semantic Alignment Across Entries
actions:
  - align_et_al_vs_full_author_lists
  - standardize_abbreviated_journal_names
  - handle_minor_inconsistencies

### Stage 3: DOI Integrity Engine

#### Step 3.1 – Validate DOI Format
actions:
  - check_doi_syntax_with_regex
  - identify_malformed_dois
  - flag_empty_or_placeholder_dois

#### Step 3.2 – Resolve DOI Authenticity
external_apis:
  - crossref_api
  - doi_org_resolver
  - pubmed_api
  - semantic_scholar_api
actions:
  - verify_doi_resolves_to_legitimate_content

#### Step 3.3 – Cross-check DOI Metadata
validation_rules:
  - title_similarity_greater_than_0_90
  - author_match_greater_than_0_85
  - year_must_exactly_match
actions:
  - compare_resolved_metadata_with_reference_entry

#### Step 3.4 – Fake DOI Detection
indicators:
  - unresolvable_links_returning_404
  - suspicious_prefixes_from_fraudulent_publishers
  - mismatched_titles_authors
actions:
  - flag_potentially_fake_dois

#### Step 3.5 – Auto-Repair Missing/Invalid DOIs
condition: enable_auto_correction == true
actions:
  - search_authoritative_databases_by_title_authors
  - replace_invalid_dois_with_confidence_score_greater_than_0_92
  - flag_low_confidence_replacements

### Stage 4: Formatting Compliance Engine

#### Step 4.1 – Style-Specific Formatting Check
citation_styles:
  apa:
    author_format: "Last name, Initial(s)"
    capitalization: "Sentence case for titles"
    punctuation: "Period after journal name"
    ordering: "Alphabetical"
  ieee:
    author_format: "Initial(s), Last name"
    capitalization: "Title Case"
    punctuation: "Comma-separated elements"
    ordering: "Numerical"
  harvard:
    author_format: "Last name, Initial(s)"
    capitalization: "Sentence case"
    punctuation: "Colon after author list"
    ordering: "Alphabetical"
  vancouver:
    author_format: "Numeric"
    capitalization: "As provided"
    punctuation: "Varies"
    ordering: "Order of appearance"

#### Step 4.2 – Duplicate Detection
actions:
  - compare_titles_and_dois_for_duplicates
  - flag_exact_or_near_duplicates
  - identify_self_citations_needing_special_formatting

#### Step 4.3 – Humanized Rewriting
actions:
  - apply_natural_language_rewriting_techniques
  - vary_author_name_representation
  - preserve_original_meaning_while_enhancing_readability

## 📊 Outputs

audit_report:
  summary:
    total_references: integer
    total_citations: integer
    matched: integer
    unmatched: integer
    doi_valid: integer
    doi_invalid: integer
    doi_corrected: integer
  issues:
    - type: missing_reference
      details: string
      location: string
    - type: uncited_reference
      details: string
      entry_number: integer
    - type: invalid_doi
      details: string
      entry_number: integer
    - type: fake_doi
      details: string
      suggested_action: string
    - type: formatting_error
      details: string
      style_violation: string
  corrections:
    doi_replacements:
      - original_doi: string
        corrected_doi: string
        confidence_score: float
        source_database: string
    updated_references:
      - corrected_reference_string
  quality_scores:
    citation_integrity_score: float
    doi_authenticity_score: float
    formatting_compliance_score: float
    journal_readiness: string  # ready | minor_revision | major_revision

exported_files:
  - validated_manuscript.pdf
  - doi_audit_report.json
  - correction_log.txt

## 🛡️ Plagiarism Safety & Ethical Considerations

principles:
  - preserve_original_intent_and_meaning
  - apply_only_targeted_fixes
  - avoid_generic_templates
  - maintain_researcher_voice_integrity
  - respect_intellectual_property

## 🎯 Final Status Indication

status_indicators:
  ready: "Fully compliant, no further action needed"
  minor_revision: "Minor tweaks required before submission"
  major_revision: "Significant structural/citation issues need addressing"

## 🚀 Usage Example

cli_example: |
  run-validation-engine \
    --input manuscript.docx \
    --style apa \
    --auto-correct true \
    --strict-mode false \
    --journal-guidelines elsevier \
    --output-format pdf,json,txt

## 📈 Quality Assurance Metrics

metrics:
  citation_integrity_score: "Measures completeness and accuracy of citation-reference pairing"
  doi_authenticity_score: "Validates percentage of working, legitimate DOIs"
  formatting_compliance_score: "Ensures adherence to selected citation style"
  journal_readiness_indicator: "Overall assessment for publication suitability"

## 🔬 Target Journals Support

supported_publishers:
  - Elsevier journals
  - Springer publications
  - IEEE transactions
  - Nature portfolio
  - Wiley-Blackwell series
  - Oxford Academic Press
  - Cambridge University Press
  - Scopus Q1-Q3 indexed journals

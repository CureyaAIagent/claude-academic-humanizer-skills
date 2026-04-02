---
name: super-memory-team
description: Complete academic validation with Mixtral 8x22B auditing, DOI resolution, citation integrity, plagiarism detection (<10%), and AI content monitoring.
---
version: 1.5.0
author: SuperMemory Team
tags:
  - academic-writing
  - mixtral-audit
  - plagiarism-detection
  - ai-content-monitoring
  - citation-integrity

# 🔧 Configuration Parameters
config:
  memory_source: "notion"
  audit_model: "mixtral_8x22b"
  primary_writer: "claude"
  statistical_validator: "python_api"
  doi_resolver_api: "https://doi.org/"
  plagiarism_detector: "copyleaks_api"  # or "turnitin_api"
  ai_content_detector: "originality_ai_api"  # or "contentatscale_api"

# 🗃️ Complete Memory Schema with Compliance Tracking
memory_schema:
  paper_id: string
  journal: string
  rules:
    - description: string
  error_memory:
    - message: string
      severity: [high|medium|low]
      fix_instruction: string
      category: [textual|statistical|citation|figure|table|reference|plagiarism|ai_content]
  section_locks:
    - section_name: string
      locked: boolean
  approved_sections:
    introduction: boolean
    methodology: boolean
    results: boolean
    discussion: boolean
  rejected_patterns:
    - pattern: string
  
  # Compliance Monitoring Memory
  compliance_memory:
    - check_type: [ai_content|plagiarism]
      section: string
      score: number  # percentage
      timestamp: string
      passed: boolean
      violations_found:
        - segment: string
        - similarity_source: string
        - recommended_fix: string
  
  # Existing Data Artifact Memory
  table_memory:
    - table_id: string
      caption: string
      headers_validated: boolean
      statistical_tests_applied: [string]
      p_values_reported: boolean
      errors_found:
        - column: string
          issue: string
          severity: [high|medium|low]
  
  figure_memory:
    - figure_id: string
      caption: string
      type: [chart|graph|diagram|image]
      data_source_linked: boolean
      statistical_significance_shown: boolean
      errors_found:
        - component: string
          issue: string
          severity: [high|medium|low]
  
  citation_memory:
    - reference_id: string
      cited_in_text: boolean
      bibliography_entry_complete: boolean
      doi_resolves: boolean
      year_consistent: boolean
      authors_formatted_correctly: boolean
      journal_name_normalized: boolean
      errors_found:
        - field: string
          issue: string
          severity: [high|medium|low]
  
  reference_memory:
    - bib_key: string
      entry_type: [article|book|inproceedings|techreport|misc]
      title: string
      authors: [string]
      year: number
      journal: string
      volume: string
      pages: string
      doi: string
      url: string
      citation_style_compliant: boolean
      errors_found:
        - field: string
          issue: string
          severity: [high|medium|low]

# ⚙️ Journal Rule Templates with Compliance Requirements
journal_templates:
  q1_generic:
    imrad_required: true
    citation_style: "APA"
    max_word_count_per_section: 500
    required_elements:
      - abstract_structure
      - method_dataset_link
      - result_citation_mapping
      - table_figure_citations
      - statistical_test_reporting
      - doi_resolution_mandatory
      - reference_integrity_check
      - ai_content_less_than_10_percent
      - plagiarism_less_than_10_percent
    forbidden_phrases:
      - "This paper discusses"
      - "In today's world"
      - "Rapidly growing field"
    compliance_requirements:
      - ai_content_threshold: 10
      - plagiarism_threshold: 10
      - original_contribution_required: true
      - self_citation_limit: 20  # Percentage of total citations
    data_requirements:
      - all_tables_must_have_captions
      - all_figures_must_be_referenced
      - statistical_significance_must_be_shown
      - p_values_must_be_reported_where_applicable
      - dois_must_resolve_to_valid_sources
      - bibliography_entries_must_be_complete

  ieee:
    extends: q1_generic
    citation_style: "IEEE"
    section_order: ["Abstract", "Introduction", "Related Work", "Proposed Method", "Experimental Results", "Conclusion"]
    figure_caption_required: true
    compliance_requirements:
      - ai_content_threshold: 10
      - plagiarism_threshold: 10
      - numeric_citations_bracketed
      - et_al_after_3_authors
    data_requirements:
      - experimental_results_must_show_confidence_intervals
      - comparative_analysis_required

  springer:
    extends: q1_generic
    citation_style: "Springer LNCS"
    section_order: ["Abstract", "Introduction", "Background", "Approach", "Evaluation", "Threats to Validity", "Conclusion"]
    double_blind_compliance: true
    compliance_requirements:
      - ai_content_threshold: 10
      - plagiarism_threshold: 10
      - author_names_anonymized
      - evaluation_metrics_must_be_defined
    data_requirements:
      - threat_analysis_required

  elsevier:
    extends: q1_generic
    citation_style: "Elsevier-Harvard"
    section_order: ["Abstract", "Keywords", "Introduction", "Methods", "Results", "Discussion", "Conclusions", "References"]
    keyword_limit: 6
    compliance_requirements:
      - ai_content_threshold: 10
      - plagiarism_threshold: 10
      - keywords_must_be_present
    data_requirements:
      - references_section_mandatory
      - alphabetical_bibliography_sorting

# ⚙️ Rule Compiler Output Template with Compliance Enforcement
rule_prompt_template: |
  ROLE: {{journal.name}} Journal Writer  
  TASK: Improve the given section WITHOUT introducing new errors  

  CONSTRAINTS:  
  - Follow {{journal.section_order}} structure strictly  
  - No repetition across sections  
  - No generic phrases (e.g., 'this study aims')  
  - Each claim must map to a reference  
  - Each result must map to a method  
  - Each conclusion must map to findings  
  - All DOIs must resolve to valid sources  
  - Citations must match bibliography entries exactly  
  - Reference formatting must follow {{journal.citation_style}} style  
  - AI-generated content MUST BE LESS THAN 10%  
  - Plagiarism MUST BE LESS THAN 10%  
  - All content MUST BE ORIGINAL CONTRIBUTIONS  
  {% for element in journal.required_elements %}
  - {{element}}
  {% endfor %}
  {% for requirement in journal.data_requirements %}
  - {{requirement}}
  {% endfor %}
  {% for compliance in journal.compliance_requirements %}
  - {{compliance}}
  {% endfor %}

  ERROR MEMORY:  
  {{error_memory}}  

  REJECTED PATTERNS:  
  {{rejected_patterns}}  

  LOCKED SECTIONS:  
  {{locked_sections}}  

  COMPLIANCE MEMORY:  
  {{compliance_memory}}  

  REFERENCE MEMORY:  
  {{reference_memory}}  

  CITATION MEMORY:  
  {{citation_memory}}  

  INSTRUCTION:  
  - Modify ONLY required parts  
  - Do NOT rewrite entire section  
  - Do NOT change approved content  
  - Ensure ALL citations have corresponding bibliography entries  
  - Verify ALL DOIs resolve correctly  
  - MAINTAIN ORIGINAL CONTENT (>90% human-authored)  
  - AVOID COPYING FROM OTHER SOURCES (>90% original)  

  OUTPUT:  
  - Clean corrected version  

# 🔐 Section Locking System
section_locks:
  introduction: true
  methodology: true
  results: false
  discussion: false
  references: false

# ✂️ Diff-Based Editing Engine Settings
diff_engine:
  mode: line_level
  preserve_formatting: true
  allow_rewrites: false

# 🧪 Audit System Integration (Mixtral 8x22B with Compliance Checking)
audit_system:
  enabled: true
  external_model: mixtral_8x22b
  audit_prompt: |
    Act as a senior academic editor reviewing a manuscript for top-tier journal submission.

    Perform comprehensive validation covering:

    TEXTUAL QUALITY:
    - Logical flow and coherence
    - Repetition avoidance
    - Claim-to-citation mapping
    - IMRAD adherence
    - Generic phrase elimination

    COMPLIANCE CHECKING:
    - AI-generated content detection (<10% threshold)
    - Plagiarism detection (<10% threshold)
    - Original contribution verification
    - Self-citation analysis (must be <20% of total)

    CITATION AND REFERENCE INTEGRITY:
    - Verify all in-text citations exist in bibliography
    - Check that all bibliography entries are cited in text
    - Resolve all DOIs to confirm they point to valid sources
    - Ensure citation formatting matches {{journal.citation_style}} style
    - Validate author names, years, journal titles, volumes, pages
    - Check for duplicate or missing references

    STATISTICAL ACCURACY:
    - Reported statistics accuracy verification
    - Appropriate statistical test usage
    - P-value and confidence interval reporting completeness
    - Outlier detection and handling documentation

    TABLE & FIGURE VALIDATION:
    - All tables/figures referenced in text
    - Captions match content accurately
    - Units and labels are clear and consistent
    - Statistical significance properly indicated

    Return ONLY structured feedback in this format:
    [
      {
        "category": "[textual|citation|reference|statistical|table|figure|plagiarism|ai_content]",
        "issue": "Brief description of problem",
        "severity": "[high|medium|low]",
        "location": "Section name or reference ID",
        "compliance_violation": true/false,
        "fix_instructions": "Specific steps to resolve"
      }
    ]

# 📈 Statistical Validation Engine
statistical_validation:
  enabled: true
  engine: "python_api"
  checks:
    - descriptive_statistics: true
    - normality_tests: true
    - correlation_analysis: true
    - regression_diagnostics: true
    - outlier_detection: true
  output_format: json

# 🔍 DOI Resolution and Citation Verification
citation_verification:
  enabled: true
  doi_resolver: "https://doi.org/"
  crossref_api: "https://api.crossref.org/works/"
  validation_checks:
    - doi_format_valid: true
    - doi_resolves_successfully: true
    - resolved_title_matches_citation: true
    - resolved_authors_match_citation: true
    - resolved_year_matches_citation: true
    - resolved_journal_matches_citation: true

# 🛡️ Plagiarism Detection System
plagiarism_detection:
  enabled: true
  detector_service: copyleaks_api
  threshold: 10  # percentage
  scan_modes:
    - internet_search: true
    - academic_databases: true
    - publications: true
    - cross_platform_check: true
  reporting:
    - similarity_score: true
    - source_identification: true
    - highlighted_segments: true

# 🤖 AI Content Detection System
ai_content_detection:
  enabled: true
  detector_service: originality_ai_api
  threshold: 10  # percentage
  detection_methods:
    - linguistic_pattern_analysis: true
    - sentence_structure_comparison: true
    - semantic_coherence_check: true
    - metadata_analysis: true
  reporting:
    - ai_probability_score: true
    - human_written_percentage: true
    - flagged_passages: true

# 📚 Reference Management System
reference_management:
  enabled: true
  bib_file_sync: true
  duplicate_detection: true
  missing_field_alerts: true
  style_compliance_checking: true
  cross_reference_validation: true

# 🔁 Complete Iteration Loop Behavior with Compliance Monitoring
loop_behavior:
  max_iterations: 7
  auto_lock_on_approval: true
  feedback_to_memory: true
  statistical_memory_update: true
  citation_memory_update: true
  reference_memory_update: true
  compliance_memory_update: true  # New addition

# 🧩 Core Components Mapping
components:
  memory_bank:
    storage_type: notion
    sync_frequency: real_time
  rule_compiler:
    input_fields: 
      - "error_memory"
      - "rejected_patterns" 
      - "approved_content"
      - "journal"
      - "reference_memory"
      - "citation_memory"
      - "compliance_memory"
    output_field: "enforced_rules"
  section_controller:
    lock_policy: strict
    modification_scope: section_specific
  diff_editor:
    engine: git_diff_style
    granularity: line_based
  auditor:
    type: dual_model
    primary: claude
    validator: mixtral_8x22b
  citation_checker:
    type: external_service
    resolver: crossref_api
    validator: mixtral_8x22b
  compliance_monitor:
    plagiarism_detector: copyleaks_api
    ai_detector: originality_ai_api
    validator: mixtral_8x22b

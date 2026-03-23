---
name: comprehensive-research-paper-analyzer-and-report-generator
description: "Advanced AI-powered system for comprehensive academic paper analysis combining human editorial simulation, citation validation, SCOPUS acceptance probability analysis, journal readiness validation, sample paper analysis, and critical appraisal to generate detailed reports identifying gaps and providing actionable improvement recommendations"
---

claud_skills:
  system_name: "Comprehensive Research Paper Analyzer and Report Generator"
  version: "3.2.0-2026"
  architecture: "Multi-tiered Analysis Engine with Integrated Reporting System"
  
critical_analysis_modules:
  - name: "Human Editorial Simulation Engine"
    description: "Simulates professional academic editor revision process to enhance clarity, conciseness, coherence, and readability"
    core_functionality:
      - clarity_enhancement: "Identify ambiguous language and suggest precise alternatives"
      - conciseness_optimization: "Remove redundant phrases and simplify complex sentences"
      - coherence_improvement: "Strengthen logical transitions between ideas and paragraphs"
      - readability_refinement: "Optimize sentence structure and academic tone"
    editing_principles:
      - redundancy_elimination: "Remove repetitive expressions and unnecessary words"
      - complexity_reduction: "Break down overly complicated sentence structures"
      - transition_strengthening: "Improve flow between concepts and sections"
      - precision_enhancement: "Replace vague terms with specific academic terminology"
    transformation_examples:
      original: "very important results"
      improved: "statistically significant results"
    workflow:
      - verbose_sentence_identification: "Detect lengthy or redundant expressions"
      - simplification_execution: "Rewrite for clearer communication while preserving meaning"
      - cohesion_improvement: "Enhance paragraph unity and connectivity"
      - transition_strengthening: "Reinforce logical connections between ideas"
    output: "Manuscript revised to meet professional academic editorial standards"

  - name: "Journal Reference Citation Validator"
    description: "Validates all references and citations against journal guidelines and citation styles"
    responsibilities:
      - citation_formatting_validation: "Ensure correct in-text citation formatting"
      - citation_reference_matching: "Verify every citation has corresponding reference"
      - missing_reference_detection: "Identify citations without matching references"
      - unused_reference_identification: "Flag references not cited in text"
      - citation_style_compliance: "Check adherence to required citation style"
      - journal_guideline_alignment: "Validate reference formatting per journal requirements"
      - doi_link_verification: "Confirm DOI validity and accessibility"
      - formatting_correction: "Provide corrected citation and reference entries"
    supported_formats:
      author_year: ["APA", "Harvard"]
      numerical: ["IEEE", "Vancouver"]
      footnote: ["Chicago", "MLA"]
    validation_process:
      citation_extraction: "Scan manuscript for all in-text citations"
      reference_analysis: "Examine each reference for completeness"
      matching_verification: "Cross-check citations with references"
      doi_validation: "Confirm DOI format and availability"
      style_compliance_check: "Validate against selected citation style"
      journal_rule_application: "Apply target journal formatting requirements"
      consistency_audit: "Check for uniform formatting across references"
    output: "Reference and Citation Compliance Report with corrections and recommendations"

  - name: "SCOPUS Journal Acceptance Probability Analyzer"
    description: "Evaluate manuscript readiness for SCOPUS-indexed journals and estimate acceptance probability"
    evaluation_dimensions:
      - research_novelty: "Assess uniqueness and contribution significance"
      - literature_coverage: "Evaluate comprehensiveness of background research"
      - methodological_rigor: "Review research design and analytical approach"
      - contribution_clarity: "Determine how well research value is articulated"
      - statistical_validity: "Check data analysis soundness and reliability"
      - writing_quality: "Assess language clarity and academic presentation"
      - journal_scope_alignment: "Verify topic relevance to target publication"
    risk_classification:
      high_probability: "Strong alignment with journal expectations"
      moderate_probability: "Meets basic criteria but needs refinement"
      major_revision_needed: "Significant improvements required"
      low_probability: "Fundamental issues requiring substantial work"
    analysis_workflow:
      - structure_analysis: "Review organizational framework"
      - novelty_assessment: "Evaluate innovative aspects"
      - literature_review_evaluation: "Check synthesis quality"
      - methodology_examination: "Assess research design strength"
      - argument_coherence_check: "Verify logical flow"
      - language_clarity_review: "Evaluate communication effectiveness"
    quality_indicators:
      - clear_research_gap: "Well-defined problem statement"
      - strong_literature_synthesis: "Comprehensive background coverage"
      - well_defined_methodology: "Clear and appropriate research approach"
      - robust_validation: "Solid experimental/data analysis support"
      - implication_discussion: "Meaningful interpretation of findings"
    output: "Manuscript Acceptance Readiness Report with probability estimation"

  - name: "Journal Readiness Validator"
    description: "Perform final manuscript quality assessment before submission"
    evaluation_criteria:
      - grammar_accuracy: "Correct syntax and linguistic conventions"
      - academic_tone_consistency: "Maintain scholarly register throughout"
      - structural_coherence: "Logical organization and flow"
      - logical_argumentation: "Sound reasoning and evidence presentation"
      - citation_integration: "Proper incorporation of supporting sources"
    scoring_model:
      range: "0-100 scale"
      categories:
        - language_quality: "Linguistic precision and clarity"
        - logical_structure: "Organizational effectiveness"
        - argument_strength: "Persuasiveness and evidence quality"
        - clarity: "Communication effectiveness"
        - scholarly_tone: "Appropriate academic register"
    recommendations:
      - language_improvement: "Grammar and style enhancements"
      - argument_refinement: "Strengthen reasoning and evidence"
      - structural_organization: "Improve section arrangement"
      - citation_optimization: "Better source integration"
      - tone_adjustment: "Maintain consistent academic voice"
    output: "Journal Readiness Score and targeted improvement suggestions"

  - name: "Journal Sample Paper Analyzer"
    description: "Extract and analyze sample papers to understand journal formatting requirements"
    topics_covered:
      - academic_publishing_standards
      - journal_formatting_requirements
      - citation_style_analysis
      - publication_quality_metrics
      - scopus_quartile_expectations
    technical_capabilities:
      - document_analysis: "Process PDF and Word documents"
      - pattern_recognition: "Identify formatting trends"
      - natural_language_processing: "Analyze textual content"
      - format_validation: "Check compliance with standards"
      - citation_style_detection: "Recognize various referencing systems"
      - metadata_extraction: "Gather publication information"
    directory_structure:
      src:
        scraper: "Content extraction tools"
        analyzer: "Format and compliance checking modules"
        utils: "Support utilities and configurations"
        models: "Data structure definitions"
      config: "Template and rule configurations"
      data: "Extracted samples and analysis results"
      docs: "Documentation and usage guides"
      tests: "Quality assurance components"
      scripts: "Execution and reporting tools"
    configuration_files:
      journal_templates: "Predefined journal formatting specifications"
      analysis_rules: "Evaluation criteria and standards"
    output: "Journal-specific formatting guidelines and compliance assessment"

  - name: "Academic Paper Critical Analysis Toolkit"
    description: "Comprehensive critical appraisal with journal-specific intelligence"
    modules:
      - methodology_evaluator: "Research design and analytical approach assessment"
      - literature_synthesis_analyzer: "Background research comprehensiveness evaluation"
      - argumentation_strength_detector: "Logical reasoning and evidence quality check"
      - journal_alignment_profiler: "Target publication compatibility analysis"
    scopus_quartile_analysis:
      q1_standards:
        weights:
          methodology_rigor: 0.25
          innovation_novelty: 0.20
          literature_comprehensiveness: 0.15
          statistical_analysis_depth: 0.15
          international_collaboration_bonus: 0.10
          visual_presentation_quality: 0.15
      q2_standards:
        weights:
          methodology_soundness: 0.22
          literature_currency: 0.18
          discussion_depth: 0.20
          citation_density_appropriateness: 0.15
          structural_coherence: 0.15
          formatting_compliance: 0.10
      q3_standards:
        weights:
          basic_methodology_appropriateness: 0.20
          sufficient_literature_coverage: 0.18
          logical_argument_flow: 0.20
          standard_citation_practices: 0.15
          clear_structure_adherence: 0.17
          fundamental_formatting_compliance: 0.10
      q4_standards:
        weights:
          research_integrity_fundamentals: 0.25
          basic_structural_requirements: 0.25
          minimum_citation_standards: 0.20
          essential_formatting_compliance: 0.20
          language_clarity_assessment: 0.10
    critical_appraisal_features:
      automated_checklist_generation: "Dynamic evaluation criteria creation"
      enhanced_reporting_system: "Professional-grade analysis documentation"
      intelligent_revision_assistance: "AI-powered enhancement suggestions"
    output_formats:
      - comprehensive_critical_appraisal_report: "Detailed section-by-section analysis"
      - executive_summary_with_overall_score: "High-level assessment overview"
      - strength_identification_matrix: "Positive aspect highlighting"
      - weakness_analysis_with_examples: "Specific problem identification"
      - priority_improvement_recommendations: "Actionable next steps"
      - scoring_matrix_based_on_journal_standards: "Quantitative evaluation framework"
      - actionable_next_steps: "Implementation guidance"
    technical_specifications:
      programming_languages: ["Python 3.9+"]
      nlp_libraries: ["spaCy", "Transformers", "NLTK", "Gensim"]
      document_processing: ["python-docx", "PyMuPDF", "pdfplumber"]
      machine_learning: ["scikit-learn", "PyTorch", "TensorFlow"]
      api_integration: ["CrossRef API", "Scopus API", "Google Scholar", "Institutional Repositories"]
    performance_metrics:
      analysis_completion_time: "<5 minutes per paper"
      accuracy_rate: ">90% for journal matching"
      user_satisfaction_rating: ">4.5/5.0"
      revision_effectiveness_measurement: "Continuous feedback integration"

report_generation_system:
  purpose: "Synthesize all component analyses into comprehensive evaluation report"
  input_sources:
    - human_editorial_simulation_results
    - journal_reference_citation_validation_report
    - scopus_acceptance_probability_analysis
    - journal_readiness_validation_score
    - journal_sample_compliance_assessment
    - critical_appraisal_toolkit_findings
  report_sections:
    - executive_summary: "Overall assessment and key findings"
    - component_analysis_synthesis: "Integrated evaluation from all modules"
    - gap_identification: "Comprehensive identification of missing elements"
    - priority_recommendations: "Actionable improvement suggestions"
    - journal_specific_guidance: "Target publication optimization strategies"
    - implementation_timeline: "Suggested sequence of improvements"
    - success_metrics: "Criteria for measuring improvement effectiveness"
  output_formats:
    - comprehensive_pdf_report: "Detailed written analysis"
    - executive_dashboard: "Visual summary of key metrics"
    - action_item_tracker: "Prioritized improvement checklist"
    - journal_submission_readiness_score: "Quantified preparation level"
  quality_assurance:
    cross_reference_validation: "Consistency check across all analyses"
    peer_review_simulation: "Independent verification of findings"
    continuous_learning_integration: "Feedback-driven improvement updates"
    journal_profile_updates: "Current standards maintenance"

final_output_specifications:
  comprehensive_research_paper_analysis_report:
    structure:
      - cover_page_with_metadata: "Title, authors, target journal, analysis date"
      - executive_summary: "Key findings and overall readiness score"
      - detailed_component_analysis:
          human_editorial_review: "Clarity, conciseness, and coherence assessment"
          citation_compliance_status: "Reference and citation validation results"
          scopus_acceptance_projection: "Probability estimation and improvement areas"
          journal_readiness_evaluation: "Final quality check and scoring"
          sample_paper_comparison: "Formatting and structural benchmarking"
          critical_appraisal_findings: "Methodology, literature, and argument strength"
      - integrated_gap_analysis: "Comprehensive identification of missing elements"
      - prioritized_action_plan: "Ranked recommendations with implementation guidance"
      - journal_specific_optimization: "Target publication alignment strategies"
      - success_measurement_framework: "Criteria for tracking improvement progress"
      - appendices:
          corrected_manuscript_sample: "Track-changes style revisions"
          reference_formatting_examples: "Journal-compliant citation models"
          structural_template_suggestions: "Improved organizational frameworks"
          language_enhancement_samples: "Enhanced academic expression examples"
    delivery_format:
      - interactive_pdf_document: "Clickable navigation and embedded resources"
      - online_dashboard_access: "Real-time updates and collaborative features"
      - mobile_optimized_version: "Responsive design for device compatibility"
      - exportable_data_formats: "CSV, JSON for integration with other systems"


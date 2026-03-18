---
name: journal-sample-paper-analyzer
description: "Comprehensive tool for extracting and analyzing sample papers from academic journals to understand formatting requirements, citation styles, and publication standards"
---
topics: 
    - "academic-publishing"
    - "journal-analysis"
    - "citation-style"
    - "research-tools"
    - "scopus-q1-q3"
    - "paper-formatting"
  license: "MIT"
  visibility: "public"

claude_skills:
  programming_languages:
    - python
    - yaml
    - json
    - html
    - css
  
  frameworks_libraries:
    - beautifulsoup4
    - selenium
    - requests
    - pandas
    - numpy
    - pyyaml
    - pdfplumber
    - pymupdf
    - crossrefapi
  
  ai_capabilities:
    - document_analysis
    - pattern_recognition
    - natural_language_processing
    - format_validation
    - citation_style_detection
    - metadata_extraction

directory_structure:
  src:
    scraper:
      - journal_scraper.py
      - paper_extractor.py
      - metadata_parser.py
    analyzer:
      - format_analyzer.py
      - citation_analyzer.py
      - compliance_checker.py
      - image_validator.py
    utils:
      - config_manager.py
      - validation_tools.py
      - logger.py
    models:
      - journal_template.py
      - paper_model.py
      - analysis_result.py
  config:
    - journal_templates.yaml
    - analysis_rules.yaml
    - credentials.yaml
  data:
    extracted_samples: {}
    analysis_results: {}
    compliance_reports: {}
  docs:
    - api_reference.md
    - usage_guide.md
    - contributing.md
  tests:
    - test_scraper.py
    - test_analyzer.py
    - test_utils.py
  scripts:
    - setup.sh
    - run_analysis.py
    - generate_report.py

dependencies:
  python_version: ">=3.8"
  pip_packages:
    - beautifulsoup4>=4.9.3
    - selenium>=4.0.0
    - requests>=2.25.1
    - pandas>=1.3.0
    - numpy>=1.21.0
    - PyYAML>=5.4.1
    - pdfplumber>=0.6.0
    - pymupdf>=1.19.0
    - crossrefapi>=1.0.0
    - python-docx>=0.8.11
    - pillow>=8.3.0
    - lxml>=4.6.3

configuration_files:
  journal_templates_yaml:
    template_schema:
      journal_name: string
      issn: string
      publisher: string
      website: string
      quartile_ranking: enum["Q1", "Q2", "Q3", "Q4"]
      format_requirements:
        font_family: string
        font_sizes:
          title: string
          authors: string
          abstract: string
          body_text: string
          references: string
          footnotes: string
        margins:
          top: string
          bottom: string
          left: string
          right: string
        line_spacing: string
        paragraph_spacing: string
      citation_style: string
      reference_format:
        style: string
        numbering_system: string
        doi_requirement: boolean
      figure_requirements:
        minimum_resolution: string
        accepted_formats: list
        maximum_width: string
        caption_format: string
      table_requirements:
        caption_position: string
        numbering_system: string
      word_limit:
        abstract: integer
        main_text: integer
        total: integer
      sections_required:
        - string
      submission_guidelines_url: string
    
    sample_template:
      journal_name: "Nature Scientific Reports"
      issn: "2045-2322"
      publisher: "Springer Nature"
      website: "https://www.nature.com/srep/"
      quartile_ranking: "Q1"
      format_requirements:
        font_family: "Times New Roman"
        font_sizes:
          title: "16pt bold"
          authors: "12pt"
          abstract: "12pt italic"
          body_text: "12pt"
          references: "10pt"
          footnotes: "10pt"
        margins:
          top: "1 inch"
          bottom: "1 inch"
          left: "1 inch"
          right: "1 inch"
        line_spacing: "1.5"
        paragraph_spacing: "6pt"
      citation_style: "Nature Style"
      reference_format:
        style: "numeric superscript"
        numbering_system: "consecutive numbers"
        doi_requirement: true
      figure_requirements:
        minimum_resolution: "300 DPI"
        accepted_formats: ["TIFF", "EPS", "PDF"]
        maximum_width: "180mm"
        caption_format: "below_figure_bold"
      table_requirements:
        caption_position: "above_table"
        numbering_system: "arabic_numerals"
      word_limit:
        abstract: 300
        main_text: 5000
        total: 6000
      sections_required:
        - "Abstract"
        - "Introduction"
        - "Methods"
        - "Results"
        - "Discussion"
        - "References"
      submission_guidelines_url: "https://www.nature.com/srep/publish/guidelines"

  analysis_rules_yaml:
    font_analysis:
      acceptable_fonts: 
        - "Times New Roman"
        - "Arial"
        - "Helvetica"
        - "Calibri"
      font_size_ranges:
        title_min: 14
        title_max: 24
        body_min: 10
        body_max: 14
      validation_rules:
        - check_font_consistency
        - verify_size_standards
        - validate_bold_italic_usage
    
    citation_analysis:
      supported_styles:
        - "APA"
        - "MLA"
        - "Chicago"
        - "IEEE"
        - "Nature"
        - "Science"
      doi_requirements:
        mandatory_for_q1: true
        mandatory_for_q2: true
        recommended_for_q3: false
        optional_for_q4: false
      
    image_analysis:
      resolution_check:
        minimum_dpi: 300
        recommended_dpi: 600
      format_acceptance:
        - "TIFF"
        - "EPS"
        - "PDF"
        - "JPEG"
        - "PNG"
      size_constraints:
        maximum_width_mm: 180
        minimum_width_mm: 80
    
    structure_analysis:
      required_sections:
        - "Abstract"
        - "Introduction"
        - "Methods"
        - "Results"
        - "Discussion"
        - "Conclusion"
        - "References"
      section_order_validation: true
      heading_hierarchy_check: true

github_workflows:
  ci_cd:
    name: "CI/CD Pipeline"
    on:
      push:
        branches: ["main", "develop"]
      pull_request:
        branches: ["main"]
    jobs:
      test:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v3
          - name: Set up Python
            uses: actions/setup-python@v4
            with:
              python-version: "3.9"
          - name: Install dependencies
            run: |
              python -m pip install --upgrade pip
              pip install -r requirements.txt
          - name: Run tests
            run: pytest tests/
      
      lint:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v3
          - name: Set up Python
            uses: actions/setup-python@v4
            with:
              python-version: "3.9"
          - name: Lint code
            run: flake8 src/

  scheduled_analysis:
    name: "Weekly Journal Analysis"
    on:
      schedule:
        - cron: "0 0 * * 1"  # Every Monday at midnight
    jobs:
      update_templates:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v3
          - name: Update journal templates
            run: python scripts/update_templates.py

environment_variables:
  required:
    - CROSSREF_API_KEY
    - INSTITUTIONAL_ACCESS_TOKEN
    - LOG_LEVEL
  optional:
    - PROXY_SERVER
    - CUSTOM_USER_AGENT
    - TIMEOUT_SECONDS

security_settings:
  credential_handling:
    storage_method: "encrypted_environment_variables"
    rotation_policy: "90_days"
    access_control: "role_based"
  
  rate_limiting:
    max_requests_per_minute: 60
    burst_limit: 10
    cooldown_period_seconds: 60
  
  compliance:
    robots_txt_respect: true
    terms_of_service_compliance: true
    copyright_respect: true

documentation:
  api_endpoints:
    - endpoint: "/api/v1/journals/{issn}/analyze"
      method: "GET"
      description: "Analyze journal formatting requirements"
      parameters:
        - name: "issn"
          type: "string"
          required: true
        - name: "paper_type"
          type: "string"
          required: false
          default: "sample"
      response_codes:
        - "200": "Success"
        - "404": "Journal not found"
        - "500": "Internal server error"
    
    - endpoint: "/api/v1/papers/{doi}/validate"
      method: "POST"
      description: "Validate paper against journal requirements"
      parameters:
        - name: "doi"
          type: "string"
          required: true
        - name: "journal_issn"
          type: "string"
          required: true
      response_codes:
        - "200": "Validation complete"
        - "400": "Invalid parameters"
        - "404": "Paper or journal not found"

testing_framework:
  unit_tests:
    coverage_target: "90%"
    testing_libraries: ["pytest", "unittest"]
    parallel_execution: true
  
  integration_tests:
    browser_testing: ["chrome", "firefox"]
    api_testing: true
    database_testing: false
  
  performance_tests:
    load_testing: true
    stress_testing: true
    response_time_targets:
      average_response_ms: 1000
      max_response_ms: 5000

deployment:
  containerization:
    docker_image: "journal-analyzer:latest"
    base_image: "python:3.9-slim"
    ports_exposed: [8000]
  
  orchestration:
    kubernetes_deployment: true
    scaling:
      min_replicas: 1
      max_replicas: 5
      target_cpu_utilization: 70
  
  monitoring:
    health_checks: true
    logging_integration: "ELK_stack"
    alerting_system: "Prometheus_Grafana"

contributing_guidelines:
  code_style:
    linter: "flake8"
    formatter: "black"
    import_sorter: "isort"
  
  branching_strategy:
    main_branch: "production ready code"
    develop_branch: "integration branch"
    feature_branches: "feature/*"
    hotfix_branches: "hotfix/*"
  
  pull_request_requirements:
    minimum_reviewers: 2
    status_checks_required: true
    documentation_updated: true
    tests_passing: true

license_information:
  type: "MIT"
  commercial_use: "permitted"
  modification: "permitted"
  distribution: "permitted"
  patent_use: "permitted"
  trademark_use: "restricted"

maintenance_schedule:
  regular_updates:
    frequency: "weekly"
    scope: "dependency updates and security patches"
  
  major_releases:
    frequency: "quarterly"
    scope: "new features and improvements"
  
  security_audits:
    frequency: "monthly"
    scope: "vulnerability assessments"

backup_policy:
  data_backup:
    frequency: "daily"
    retention_period: "30_days"
    storage_locations: ["local", "cloud"]
  
  configuration_backup:
    frequency: "weekly"
    retention_period: "90_days"
    storage_locations: ["cloud"]

disaster_recovery:
  recovery_time_objective: "4_hours"
  recovery_point_objective: "24_hours"
  backup_verification: "weekly"
  failover_procedures: "documented_and_tested"

performance_optimization:
  caching_strategy:
    redis_cache: true
    cache_ttl_hours: 24
    cache_warming: true
  
  database_optimization:
    indexing: true
    query_optimization: true
    connection_pooling: true

scalability_features:
  horizontal_scaling: true
  load_balancing: true
  microservices_architecture: true
  asynchronous_processing: true

monitoring_metrics:
  application_metrics:
    - response_time
    - error_rate
    - throughput
    - memory_usage
    - cpu_usage
  
  business_metrics:
    - papers_analyzed
    - successful_validations
    - user_satisfaction_score
    - system_uptime_percentage

logging_configuration:
  log_levels:
    development: "DEBUG"
    staging: "INFO"
    production: "WARNING"
  
  log_retention:
    debug_logs: "7_days"
    info_logs: "30_days"
    error_logs: "90_days"
  
  log_format:
    timestamp: true
    level: true
    module: true
    message: true

error_handling:
  retry_mechanism:
    max_retries: 3
    backoff_strategy: "exponential"
    timeout_seconds: 30
  
  fallback_strategies:
    - local_cache_fallback
    - simplified_processing
    - manual_intervention_required

internationalization:
  supported_languages:
    - "en"
    - "es"
    - "fr"
    - "de"
    - "zh"
  localization_framework: "gettext"
  rtl_support: false

accessibility:
  wcag_compliance: "AA_level"
  screen_reader_support: true
  keyboard_navigation: true
  color_contrast_ratio: "4.5:1"

data_privacy:
  gdpr_compliance: true
  ccpa_compliance: true
  data_encryption: "AES_256"
  data_retention_period: "2_years"

api_versioning:
  current_version: "v1"
  versioning_scheme: "URI_path"
  backward_compatibility: "12_months"
  deprecation_policy: "6_months_notice"

rate_limiting:
  api_limits:
    anonymous_users: 100_requests_per_hour
    authenticated_users: 1000_requests_per_hour
    premium_users: 10000_requests_per_hour
  throttling_algorithm: "token_bucket"

caching_strategy:
  multi_layer_caching:
    - in_memory_cache
    - redis_cache
    - cdn_cache
  cache_invalidation: "time_based_and_event_driven"
  cache_warming: true

security_measures:
  authentication:
    jwt_tokens: true
    oauth2_support: true
    session_management: true
  
  authorization:
    role_based_access: true
    permission_scopes: true
    audit_logging: true
  
  data_protection:
    encryption_at_rest: true
    encryption_in_transit: true
    data_masking: true
  
  network_security:
    firewall_rules: true
    intrusion_detection: true
    ddos_protection: true

third_party_integrations:
  academic_databases:
    - crossref_api
    - scopus_api
    - web_of_science_api
    - pubmed_api
  
  institutional_access:
    - sso_integration
    - proxy_authentication
    - ip_whitelisting
  
  analytics:
    - google_analytics
    - mixpanel
    - custom_analytics_dashboard

continuous_improvement:
  feedback_loop:
    user_feedback_collection: true
    automated_surveys: true
    sentiment_analysis: true
  
  ml_enhancements:
    recommendation_engine: true
    anomaly_detection: true
    predictive_analytics: true
  
  feature_flags:
    gradual_rollout: true
    a_b_testing: true
    kill_switches: true

technical_debt_management:
  code_quality_metrics:
    cyclomatic_complexity_threshold: 10
    code_duplication_threshold: 5_percent
    maintainability_index_minimum: 70
  
  debt_tracking:
    technical_debt_dashboard: true
    debt_priority_classification: true
    remediation_timeline: true

knowledge_base:
  documentation_portal: true
  faq_section: true
  video_tutorials: true
  community_forum: true
  support_tickets: true

release_management:
  release_process:
    automated_deployments: true
    rollback_capability: true
    blue_green_deployment: true
    canary_releases: true
  
  changelog_management:
    automated_changelog_generation: true
    semantic_versioning: true
    release_notes: true

community_engagement:
  open_source_contributions: true
  bug_bounty_program: false
  contributor_recognition: true
  community_events: true

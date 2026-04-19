# 📁 AGENT MEMORY STRUCTURE

## 🏠 ROOT DIRECTORY
/Lalit Prashad Publisher/

## 📂 DIRECTORIES
- Journal Readiness Reports/
- Audit Logs/
- Temporary Processing/

## 📊 MASTER TRACKER FILE
Journal_Readiness_Master_Tracker.xlsx

## 🗃️ DATA STRUCTURES

### 1. MANUSCRIPT METADATA CACHE
```json
{
  "manuscript_id": "string (UUID)",
  "filename": "string",
  "author_name": "string",
  "paper_title": "string",
  "upload_timestamp": "ISO 8601 datetime",
  "file_hash": "SHA-256 hash",
  "status": "enum: [pending, processed, audited, error]",
  "processing_start_time": "ISO 8601 datetime",
  "processing_end_time": "ISO 8601 datetime"
}
### 2. AUDIT RESULTS STORAGE
{
  "manuscript_id": "string (UUID)",
  "readiness_score": "integer (0-100)",
  "category": "enum: [well_prepared, moderately_prepared, underdeveloped]",
  "dimension_scores": {
    "structure_formatting": "integer (0-100)",
    "research_quality": "integer (0-100)",
    "references_doi": "integer (0-100)",
    "plagiarism_integrity": "integer (0-100)",
    "ai_detection": "integer (0-100)",
    "statistical_validation": "integer (0-100)",
    "peer_review_simulation": "integer (0-100)",
    "journal_matching": "integer (0-100)"
  },
  "detailed_feedback": {
    "strengths": ["array of strings"],
    "weaknesses": ["array of strings"],
    "risk_level": "enum: [low, medium, high]",
    "improvement_suggestions": ["array of strings"]
  },
  "audit_timestamp": "ISO 8601 datetime",
  "report_generated": "boolean",
  "excel_logged": "boolean"
}
### 3. FILE PROCESSING LOG
{
  "log_id": "string (UUID)",
  "manuscript_id": "string (UUID)",
  "action": "enum: [upload, process_start, process_complete, error, report_generate, excel_log]",
  "timestamp": "ISO 8601 datetime",
  "details": "string (error message or status details)",
  "user_agent": "string (if applicable)"
}
Author Name,Paper Title,Readiness Score (%),Category,Report File Name,Date,Remarks
"Sample Author","Research on AI",85,"moderately_prepared","SampleAuthor_ResearchonAI_AuditReport_v1.pdf","2024-01-15","Minor formatting issues detected"

### 4. PERFORMANCE METRICS CACHE
{
  "total_manuscripts_processed": "integer",
  "average_processing_time": "seconds",
  "category_distribution": {
    "well_prepared": "integer",
    "moderately_prepared": "integer", 
    "underdeveloped": "integer"
  },
  "last_reset_date": "ISO 8601 datetime"
}

### 5. FAILED PROCESSING QUEUE
{
  "failed_id": "string (UUID)",
  "manuscript_id": "string (UUID)",
  "error_type": "enum: [format_error, processing_error, storage_error, validation_error]",
  "error_message": "string",
  "retry_count": "integer",
  "timestamp": "ISO 8601 datetime"
}

### 6. ACTIVE PROCESSING QUEUE
{
  "queue_id": "string (UUID)",
  "manuscript_id": "string (UUID)",
  "priority": "enum: [normal, high]",
  "submission_time": "ISO 8601 datetime",
  "estimated_completion": "ISO 8601 datetime"
}

### 7. ACCESS LOG TEMPLATE
{
  "access_id": "string (UUID)",
  "manuscript_id": "string (UUID)",
  "user_identifier": "string",
  "action_type": "enum: [view_report, download_report, view_tracker]",
  "timestamp": "ISO 8601 datetime",
  "ip_address": "string",
  "success": "boolean"
}

### 8. REPORT NAMING CONVENTION REGISTRY
{
  "naming_pattern": "[AuthorName]_[ShortTitle]_AuditReport_v1.[extension]",
  "allowed_extensions": ["pdf", "txt"],
  "max_filename_length": 255,
  "reserved_characters": ["<", ">", ":", "\"", "/", "\\", "|", "?", "*"]
}

### 9. TRACKER FILE SCHEMA VALIDATION
{
  "required_columns": [
    "Author Name",
    "Paper Title", 
    "Readiness Score (%)",
    "Category",
    "Report File Name",
    "Date",
    "Remarks"
  ],
  "data_types": {
    "Readiness Score (%)": "integer (0-100)",
    "Category": "enum: [well_prepared, moderately_prepared, underdeveloped]",
    "Date": "ISO 8601 date format"
  }
}

### 10.STATUS RESPONSE FORMAT
{
  "request_id": "string (UUID)",
  "status": "enum: [processing, completed, error]",
  "manuscript_id": "string (UUID)",
  "message": "string",
  "estimated_time_remaining": "seconds (if processing)"
}

import json
import hashlib
import uuid
from datetime import datetime
from typing import Dict, List, Any, Optional
from enum import Enum
from dataclasses import dataclass, asdict
from pathlib import Path

class ManuscriptStatus(Enum):
    PENDING = "pending"
    PROCESSED = "processed"
    AUDITED = "audited"
    ERROR = "error"

class Category(Enum):
    WELL_PREPARED = "well_prepared"
    MODERATELY_PREPARED = "moderately_prepared"
    UNDERDEVELOPED = "underdeveloped"

class ActionType(Enum):
    UPLOAD = "upload"
    PROCESS_START = "process_start"
    PROCESS_COMPLETE = "process_complete"
    ERROR = "error"
    REPORT_GENERATE = "report_generate"
    EXCEL_LOG = "excel_log"

class ErrorType(Enum):
    FORMAT_ERROR = "format_error"
    PROCESSING_ERROR = "processing_error"
    STORAGE_ERROR = "storage_error"
    VALIDATION_ERROR = "validation_error"

@dataclass
class ManuscriptMetadata:
    manuscript_id: str
    filename: str
    author_name: str
    paper_title: str
    upload_timestamp: str
    file_hash: str
    status: str
    processing_start_time: Optional[str] = None
    processing_end_time: Optional[str] = None

@dataclass
class DimensionScores:
    structure_formatting: int
    research_quality: int
    references_doi: int
    plagiarism_integrity: int
    ai_detection: int
    statistical_validation: int
    peer_review_simulation: int
    journal_matching: int

@dataclass
class DetailedFeedback:
    strengths: List[str]
    weaknesses: List[str]
    risk_level: str
    improvement_suggestions: List[str]

@dataclass
class AuditResults:
    manuscript_id: str
    readiness_score: int
    category: str
    dimension_scores: DimensionScores
    detailed_feedback: DetailedFeedback
    audit_timestamp: str
    report_generated: bool
    excel_logged: bool

@dataclass
class ProcessingLog:
    log_id: str
    manuscript_id: str
    action: str
    timestamp: str
    details: str
    user_agent: Optional[str] = None

@dataclass
class PerformanceMetrics:
    total_manuscripts_processed: int
    average_processing_time: float
    category_distribution: Dict[str, int]
    last_reset_date: str

@dataclass
class FailedProcessing:
    failed_id: str
    manuscript_id: str
    error_type: str
    error_message: str
    retry_count: int
    timestamp: str

@dataclass
class ActiveQueue:
    queue_id: str
    manuscript_id: str
    priority: str
    submission_time: str
    estimated_completion: str

@dataclass
class AccessLog:
    access_id: str
    manuscript_id: str
    user_identifier: str
    action_type: str
    timestamp: str
    ip_address: str
    success: bool

class JournalReadinessMemoryManager:
    def __init__(self, base_path: str = "/Lalit Prashad Publisher/"):
        self.base_path = Path(base_path)
        self.reports_dir = self.base_path / "Journal Readiness Reports"
        self.logs_dir = self.base_path / "Audit Logs"
        self.temp_dir = self.base_path / "Temporary Processing"
        
        # Create directory structure
        self._create_directories()
        
        # Initialize data stores
        self.manuscript_cache: Dict[str, ManuscriptMetadata] = {}
        self.audit_results: Dict[str, AuditResults] = {}
        self.processing_logs: List[ProcessingLog] = []
        self.performance_metrics: PerformanceMetrics = self._init_performance_metrics()
        self.failed_queue: List[FailedProcessing] = []
        self.active_queue: List[ActiveQueue] = []
        self.access_logs: List[AccessLog] = []

    def _create_directories(self):
        """Create required directory structure"""
        directories = [
            self.reports_dir,
            self.logs_dir,
            self.temp_dir
        ]
        
        for directory in directories:
            directory.mkdir(parents=True, exist_ok=True)

    def _init_performance_metrics(self) -> PerformanceMetrics:
        """Initialize performance metrics with default values"""
        return PerformanceMetrics(
            total_manuscripts_processed=0,
            average_processing_time=0.0,
            category_distribution={
                "well_prepared": 0,
                "moderately_prepared": 0,
                "underdeveloped": 0
            },
            last_reset_date=datetime.utcnow().isoformat()
        )

    def generate_file_hash(self, file_content: bytes) -> str:
        """Generate SHA-256 hash of file content"""
        return hashlib.sha256(file_content).hexdigest()

    def create_manuscript_metadata(self, filename: str, author_name: str, 
                                 paper_title: str, file_content: bytes) -> ManuscriptMetadata:
        """Create and store manuscript metadata"""
        manuscript_id = str(uuid.uuid4())
        file_hash = self.generate_file_hash(file_content)
        
        metadata = ManuscriptMetadata(
            manuscript_id=manuscript_id,
            filename=filename,
            author_name=author_name,
            paper_title=paper_title,
            upload_timestamp=datetime.utcnow().isoformat(),
            file_hash=file_hash,
            status=ManuscriptStatus.PENDING.value
        )
        
        self.manuscript_cache[manuscript_id] = metadata
        return metadata

    def store_audit_results(self, manuscript_id: str, readiness_score: int,
                          category: Category, dimension_scores: DimensionScores,
                          detailed_feedback: DetailedFeedback) -> AuditResults:
        """Store audit results for a manuscript"""
        audit_result = AuditResults(
            manuscript_id=manuscript_id,
            readiness_score=readiness_score,
            category=category.value,
            dimension_scores=dimension_scores,
            detailed_feedback=detailed_feedback,
            audit_timestamp=datetime.utcnow().isoformat(),
            report_generated=False,
            excel_logged=False
        )
        
        self.audit_results[manuscript_id] = audit_result
        
        # Update performance metrics
        self.performance_metrics.total_manuscripts_processed += 1
        self.performance_metrics.category_distribution[category.value] += 1
        
        # Mark manuscript as audited
        if manuscript_id in self.manuscript_cache:
            self.manuscript_cache[manuscript_id].status = ManuscriptStatus.AUDITED.value
            
        return audit_result

    def log_processing_action(self, manuscript_id: str, action: ActionType, 
                            details: str, user_agent: Optional[str] = None):
        """Log processing actions"""
        log_entry = ProcessingLog(
            log_id=str(uuid.uuid4()),
            manuscript_id=manuscript_id,
            action=action.value,
            timestamp=datetime.utcnow().isoformat(),
            details=details,
            user_agent=user_agent
        )
        
        self.processing_logs.append(log_entry)

    def log_access(self, manuscript_id: str, user_identifier: str,
                  action_type: str, ip_address: str, success: bool):
        """Log user access attempts"""
        access_entry = AccessLog(
            access_id=str(uuid.uuid4()),
            manuscript_id=manuscript_id,
            user_identifier=user_identifier,
            action_type=action_type,
            timestamp=datetime.utcnow().isoformat(),
            ip_address=ip_address,
            success=success
        )
        
        self.access_logs.append(access_entry)

    def add_to_failed_queue(self, manuscript_id: str, error_type: ErrorType, 
                          error_message: str) -> FailedProcessing:
        """Add failed processing to queue"""
        failed_entry = FailedProcessing(
            failed_id=str(uuid.uuid4()),
            manuscript_id=manuscript_id,
            error_type=error_type.value,
            error_message=error_message,
            retry_count=0,
            timestamp=datetime.utcnow().isoformat()
        )
        
        self.failed_queue.append(failed_entry)
        return failed_entry

    def generate_report_filename(self, author_name: str, short_title: str, extension: str) -> str:
        """Generate standardized report filename"""
        # Clean filename of reserved characters
        cleaned_author = "".join(c for c in author_name if c not in '<>:"/\\|?*')
        cleaned_title = "".join(c for c in short_title if c not in '<>:"/\\|?*')
        
        return f"{cleaned_author}_{cleaned_title}_AuditReport_v1.{extension}"

    def get_excel_tracker_template(self) -> List[str]:
        """Get Excel tracker column headers"""
        return [
            "Author Name",
            "Paper Title", 
            "Readiness Score (%)",
            "Category",
            "Report File Name",
            "Date",
            "Remarks"
        ]

    def validate_tracker_entry(self, entry: Dict[str, Any]) -> bool:
        """Validate Excel tracker entry data types"""
        try:
            # Validate score is integer between 0-100
            score = int(entry.get("Readiness Score (%)", 0))
            if not 0 <= score <= 100:
                return False
                
            # Validate category
            category = entry.get("Category", "")
            valid_categories = [c.value for c in Category]
            if category not in valid_categories:
                return False
                
            # Validate date format
            date_str = entry.get("Date", "")
            datetime.fromisoformat(date_str.replace('Z', '+00:00'))
            
            return True
        except (ValueError, TypeError):
            return False

    def mark_report_generated(self, manuscript_id: str):
        """Mark that report has been generated"""
        if manuscript_id in self.audit_results:
            self.audit_results[manuscript_id].report_generated = True

    def mark_excel_logged(self, manuscript_id: str):
        """Mark that Excel entry has been created"""
        if manuscript_id in self.audit_results:
            self.audit_results[manuscript_id].excel_logged = True

    def is_manuscript_audited(self, manuscript_id: str) -> bool:
        """Check if manuscript has been audited (immutable)"""
        if manuscript_id in self.manuscript_cache:
            return self.manuscript_cache[manuscript_id].status == ManuscriptStatus.AUDITED.value
        return False

    def get_memory_stats(self) -> Dict[str, Any]:
        """Get current memory usage statistics"""
        return {
            "total_manuscripts": len(self.manuscript_cache),
            "audited_manuscripts": len([m for m in self.manuscript_cache.values() 
                                     if m.status == ManuscriptStatus.AUDITED.value]),
            "processing_logs_count": len(self.processing_logs),
            "failed_queue_size": len(self.failed_queue),
            "active_queue_size": len(self.active_queue),
            "access_logs_count": len(self.access_logs)
        }

    def export_memory_snapshot(self, filepath: str):
        """Export current memory state to JSON file"""
        snapshot = {
            "manuscript_cache": {k: asdict(v) for k, v in self.manuscript_cache.items()},
            "audit_results": {k: asdict(v) for k, v in self.audit_results.items()},
            "processing_logs": [asdict(log) for log in self.processing_logs],
            "performance_metrics": asdict(self.performance_metrics),
            "failed_queue": [asdict(item) for item in self.failed_queue],
            "active_queue": [asdict(item) for item in self.active_queue],
            "access_logs": [asdict(log) for log in self.access_logs],
            "export_timestamp": datetime.utcnow().isoformat()
        }
        
        with open(filepath, 'w') as f:
            json.dump(snapshot, f, indent=2)

# Example usage
if __name__ == "__main__":
    # Initialize memory manager
    memory_manager = JournalReadinessMemoryManager()
    
    # Create sample manuscript metadata
    sample_content = b"Sample manuscript content for testing"
    metadata = memory_manager.create_manuscript_metadata(
        filename="sample_paper.docx",
        author_name="John Doe",
        paper_title="AI in Healthcare",
        file_content=sample_content
    )
    
    print(f"Created manuscript: {metadata.manuscript_id}")
    
    # Store sample audit results
    dimension_scores = DimensionScores(
        structure_formatting=85,
        research_quality=90,
        references_doi=75,
        plagiarism_integrity=95,
        ai_detection=80,
        statistical_validation=88,
        peer_review_simulation=82,
        journal_matching=78
    )
    
    feedback = DetailedFeedback(
        strengths=["Strong methodology", "Clear abstract"],
        weaknesses=["Formatting issues", "Limited literature review"],
        risk_level="medium",
        improvement_suggestions=["Fix formatting", "Expand references"]
    )
    
    audit_result = memory_manager.store_audit_results(
        manuscript_id=metadata.manuscript_id,
        readiness_score=83,
        category=Category.MODERATELY_PREPARED,
        dimension_scores=dimension_scores,
        detailed_feedback=feedback
    )
    
    print(f"Audit completed. Readiness score: {audit_result.readiness_score}%")
    print(f"Category: {audit_result.category}")
    
    # Log processing action
    memory_manager.log_processing_action(
        manuscript_id=metadata.manuscript_id,
        action=ActionType.PROCESS_COMPLETE,
        details="Audit completed successfully"
    )
    
    # Generate report filename
    report_filename = memory_manager.generate_report_filename(
        "John Doe", "AI_in_Healthcare", "pdf"
    )
    print(f"Report filename: {report_filename}")
    
    # Get memory stats
    stats = memory_manager.get_memory_stats()
    print(f"Memory stats: {stats}")


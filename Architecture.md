## 📊 HELIOS System Diagrams

### 📅 AP Process - Accounts Payable (32 hours / 4 days)
![Diagrama de Arquitectura](images/diagram_AP.svg)

### 🧾 TAX Process - Tax Reporting (7 hours / 1 day)
![Diagrama de Arquitectura](images/diagram_TAX.svg)

### 📈 BI Process - Business Intelligence (1 hour)
![Diagrama de Arquitectura](images/diagram_BI.svg)

### 🏗️ Historical Context - HELIOS vs. Initial Situation
![Diagrama de Arquitectura](images/diagram_context.svg)

### 📊 HELIOS Summary - Systems Created from Scratch
![Diagrama de Arquitectura](images/diagram_summary.svg)


# 🏗️ HELIOS System Architecture

## 📊 System Overview

### 📅 AP Process - Accounts Payable (32 hours / 4 days)
- **Day 1-2**: Data collection and OCR processing (16 hours)
- **Day 3-4**: Supplier reconciliation and report generation (16 hours)
- **Input Sources**: 8 suppliers via Gmail API, 1 supplier via JPG scan, 11 suppliers via manual entry
- **Output**: 25-30 page PDF reports with complete reconciliation

### 🧾 TAX Process - Tax Reporting (7 hours / 1 day)
- **Scope**: IVA, IIBB, 931 reports for 3 legal entities
- **Challenges**: AFIP portal limitations, poor quality tickets
- **Automation Level**: 60% due to government system constraints

### 📈 BI Process - Business Intelligence (1 hour)
- **Data Volume**: USD 1.75B revenue, 80,000+ covers
- **Tools**: Python, pandas, matplotlib, plotly
- **Output**: Automated dashboards with predictive analytics

## 🏗️ Technical Architecture Details

### OCR Engine Architecture
- **9 Custom OCR Engines**: One per key supplier format
- **Accuracy**: 100% for 7 key suppliers, 80% for 2 challenging formats
- **Development**: 50+ iterations per supplier for optimization

### Data Processing Pipeline
Raw Input → Classification → OCR Processing → Validation → Consolidation → Reporting

### Validation System
- **Penny-level accuracy**: System stops if discrepancy > $0.01
- **Multi-dimensional reconciliation**: 3 legal entities × 5 locations
- **Automated alerts**: Missing emails, format errors, validation failures

## 📊 System Performance Metrics

| Component | Metric | Value | Impact |
|-----------|--------|-------|--------|
| **OCR Processing** | Accuracy (key suppliers) | 99.8% | Reduced manual work by 80% |
| **Data Validation** | Reconciliation accuracy | 100% | Eliminated $2,000 monthly discrepancies |
| **Report Generation** | Time per report | 0 hours | Saved 25+ hours monthly |
| **Processing Speed** | Invoices per hour | ~22 | 700 invoices in 32 hours |
| **System Uptime** | Monthly reliability | 100% | Zero processing failures |

## 🔧 Technology Stack Implementation

### Core Technologies:
- **Programming Language**: Python 3.9+ (9,000+ lines of business logic)
- **OCR & Data Extraction**: Tesseract OCR (fine-tuned per supplier), Gmail API, pandas
- **Reporting & Visualization**: reportlab (PDF), matplotlib/plotly, SQLite
- **Process Automation**: Custom ETL pipelines, rule-based validation engines

### System Constraints & Solutions:
| Constraint | Solution | Result |
|------------|----------|--------|
| **$0 Budget** | Open-source stack (Python, Tesseract) | Infinite ROI |
| **Poor Quality Invoices** | 50+ OCR iterations per supplier | 99.8% accuracy |
| **Manual Processes** | Strategic 80/20 automation | 80% volume automated |
| **Governmental Systems** | Semi-automated templates | 60% automation where possible |

## 🎯 Architectural Decisions

1. **OCR-per-Supplier vs. Universal Model**
   - Decision: Create 9 separate OCR engines
   - Rationale: Argentine invoices have highly variable formats by supplier
   - Result: 99.8% accuracy vs. ~85% with generic OCR

2. **Penny-Level Validation**
   - Decision: Stop process if discrepancy > $0.01
   - Rationale: Financial accuracy is non-negotiable
   - Result: 100% reconciliation accuracy

3. **80/20 Automation Strategy**
   - Decision: Automate 9 suppliers (80% volume), manual for 11 (20% volume)
   - Rationale: Maximize ROI on development effort
   - Result: 32 hours/month total vs. 160+ hours previously

4. **Modular System Design**
   - Decision: Separate AP, TAX, and BI modules
   - Rationale: Independent maintenance and scaling
   - Result: Can update/improve one module without affecting others

## 📈 Scalability & Future Improvements

### Current Capacity:
- **Volume**: 700 invoices/month, USD 500K annual payments
- **Entities**: 3 legal entities, 5 physical locations
- **Suppliers**: 20 total (9 automated, 11 manual)

### Scalability Path:
- Add new digital suppliers: Copy existing OCR engine pattern
- Migrate to cloud OCR: Replace Tesseract with Google Cloud Vision (if budget allows)
- Database upgrade: SQLite → PostgreSQL for larger datasets
- Real-time processing: Move from batch to streaming processing

### Maintenance Requirements:
- **Monthly**: 40 hours (32 AP + 7 TAX + 1 BI)
- **Quarterly**: OCR model retraining for format changes
- **Annual**: System review and optimization

---

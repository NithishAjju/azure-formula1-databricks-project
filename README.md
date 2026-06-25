
# Formula 1 Data Engineering Pipeline on Azure Databricks

## Project Overview

This project implements an end-to-end Data Engineering pipeline for Formula 1 racing data using Azure Databricks, PySpark, Delta Lake, and Azure Data Lake Storage Gen2 following the Medallion Architecture (Bronze, Silver, Gold).

The solution ingests raw Formula 1 datasets from cloud storage, applies data quality checks and transformations, and builds analytics-ready datasets to support reporting and business intelligence use cases.

---

## Business Objective

The objective of this project is to build a scalable and production-ready cloud data platform capable of:

- Analyzing driver performance across seasons
- Tracking constructor championship standings
- Supporting historical Formula 1 reporting
- Enabling analytical and BI workloads
- Demonstrating modern Data Engineering best practices

---

## Solution Architecture

```text
                Source Files
                     │
                     ▼
           Azure Data Lake Storage
                     │
                     ▼
               Landing Layer
                     │
                     ▼
              Bronze Layer
        (Raw Delta Tables)
                     │
                     ▼
              Silver Layer
      (Cleaned & Standardized Data)
                     │
                     ▼
               Gold Layer
      (Fact & Dimension Models)
                     │
                     ▼
             Analytics & Reporting
```

---

## Technology Stack

| Category | Technology |
|-----------|------------|
| Cloud Platform | Microsoft Azure |
| Storage | Azure Data Lake Storage Gen2 |
| Data Processing | Azure Databricks |
| Programming Language | Python |
| Big Data Framework | Apache Spark (PySpark) |
| Storage Format | Delta Lake |
| Metadata Management | Unity Catalog |
| Orchestration | Databricks Workflows (Lakeflow Jobs) |
| Version Control | Git & GitHub |

---

## Data Sources

The project processes multiple Formula 1 datasets:

| Dataset |
|----------|
| Circuits |
| Races |
| Drivers |
| Constructors |
| Results |
| Sprint Results |

Supported source formats:

- CSV
- JSON

---

# Medallion Architecture

## Bronze Layer

### Purpose

The Bronze layer serves as the raw ingestion layer.

### Activities

- Read source files from ADLS
- Enforce predefined schemas
- Add ingestion metadata
- Store data as Delta Tables

### Features

- Raw data preservation
- Schema enforcement
- Source file tracking
- Ingestion timestamp tracking

### Example Metadata Columns

```sql
ingestion_date
source_file
```

---

## Silver Layer

### Purpose

The Silver layer contains cleansed and standardized data.

### Transformations

- Data cleansing
- Null handling
- Duplicate removal
- Column standardization
- Data quality validation
- Business rule implementation

### Example Standardization

```text
circuitId    → circuit_id
circuitName  → circuit_name
lat          → latitude
long         → longitude
```

### Benefits

- Improved data quality
- Consistent naming conventions
- Analytics-ready datasets

---

## Gold Layer

### Purpose

The Gold layer provides business-ready datasets optimized for analytical workloads.

### Dimensional Model

#### Dimension Tables

```text
dim_drivers
dim_constructors
dim_races
```

#### Fact Tables

```text
fact_race_results
fact_sprint_results
```

### Benefits

- Faster analytical queries
- Historical trend analysis
- Simplified reporting
- BI tool integration

---

## Delta Lake Features Implemented

### ACID Transactions

Provides:

- Atomicity
- Consistency
- Isolation
- Durability

### Time Travel

Allows querying historical versions of datasets.

### Schema Enforcement

Prevents invalid records from entering the pipeline.

### Scalable Storage

Supports large-scale analytical workloads efficiently.

---

## Data Engineering Concepts Demonstrated

### Data Ingestion

- Batch ingestion
- Schema enforcement
- Metadata-driven ingestion

### Data Transformation

- Data cleansing
- Standardization
- Deduplication
- Data quality validation

### Data Modeling

- Star Schema Design
- Fact and Dimension Modeling

### Pipeline Orchestration

- Workflow scheduling
- Dependency management
- Retry mechanisms
- Monitoring and alerting

### Incremental Data Processing

Supports processing only newly arrived datasets instead of full table reloads.

---

## Workflow Execution

```text
Bronze Ingestion
        │
        ▼
Silver Transformation
        │
        ▼
Gold Data Modeling
        │
        ▼
Reporting & Analytics
```

Databricks Workflows are used to:

- Schedule pipeline execution
- Define task dependencies
- Handle failures
- Retry failed tasks
- Monitor pipeline health

---

## Reporting & Analytics Use Cases

The Gold layer enables answering questions such as:

- How did drivers perform across seasons?
- Which constructors dominated Formula 1 history?
- What are the yearly championship standings?
- Which drivers achieved the highest success over time?
- How do teams perform across different circuits and locations?

---

## Key Learnings

This project demonstrates hands-on experience with:

- Azure Data Lake Storage Gen2
- Azure Databricks
- Apache Spark (PySpark)
- Delta Lake
- Unity Catalog
- Medallion Architecture
- Data Warehousing
- Star Schema Modeling
- Incremental Data Processing
- Workflow Orchestration
- Production Data Pipelines

---

## Future Enhancements

- Real-time ingestion using Structured Streaming
- CI/CD using Azure DevOps
- Data Quality Framework implementation
- Power BI Dashboard Integration
- Automated Unit Testing
- Data Lineage Tracking
- Monitoring and Alerting Framework

---



## License

This project is intended for learning, portfolio demonstration, and showcasing modern Data Engineering practices using Azure Databricks and Delta Lake.
```

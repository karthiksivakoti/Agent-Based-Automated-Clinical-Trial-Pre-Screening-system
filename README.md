# 🏥 Clinical Trial Recruitment Automation using Agentic AI

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg?style=for-the-badge&logo=Python&logoColor=white)](https://www.python.org/)
[![BigQuery](https://img.shields.io/badge/BigQuery-%234285F4.svg?style=for-the-badge&logo=Google-Cloud&logoColor=white)](https://cloud.google.com/bigquery)
[![OpenAI](https://img.shields.io/badge/OpenAI-412991.svg?style=for-the-badge&logo=OpenAI&logoColor=white)](https://openai.com/)
[![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-%2376B900.svg?style=for-the-badge&logo=Seaborn&logoColor=white)](https://seaborn.pydata.org/)

An agent-based system for automating clinical trial pre-screening using Electronic Health Records (EHR) and Large Language Models (LLMs). Built with Python, BigQuery, OpenAI GPT-4o, and the MIMIC-III clinical database.

<p align="center">
  <img src="https://raw.githubusercontent.com/yourusername/clinical-trial-automation/main/images/workflow_diagram.png" alt="Agent Workflow Diagram" width="800"/>
  <br>
  <em>Agent-Based System Workflow Architecture</em>
</p>

## 🌟 Overview

Clinical trial recruitment is a critical bottleneck in medical research, with patient screening being particularly time-consuming and resource-intensive. This project demonstrates an agent-based approach to automate the pre-screening process by:

- Retrieving and processing patient data from electronic health records
- Parsing structured and unstructured clinical trial protocols
- Evaluating eligibility against both structured criteria (age, lab values, diagnosis codes) and natural language criteria
- Using LLMs to interpret unstructured data in clinical notes
- Providing detailed eligibility assessments with explanations

## 🔍 The Challenge

<p align="center">
  <img src="https://raw.githubusercontent.com/yourusername/clinical-trial-automation/main/images/recruitment_bottleneck.png" alt="Clinical Trial Recruitment Bottleneck" width="600"/>
</p>

Clinical trial recruitment faces significant challenges:

- Manual screening of EHRs is labor-intensive and error-prone
- Complex eligibility criteria spanning structured and unstructured data
- Critical information often buried in clinical notes
- Heterogeneous data formats across clinical systems
- High costs and delays associated with recruitment failures

## 🛠️ System Architecture

Our agent-based system comprises:

### 🤖 Orchestrator Agent
- Manages the end-to-end workflow
- Coordinates specialized tools
- Aggregates results into final eligibility assessment

### 🔎 Specialized Tools

#### 1. Patient Data Retriever
- Queries MIMIC-III database via BigQuery
- Retrieves demographics, diagnoses, medications, lab values, and clinical notes
- Processes and structures heterogeneous patient data

#### 2. Protocol Parser
- Interprets clinical trial protocols
- Extracts inclusion and exclusion criteria
- Categorizes criteria by type (age, diagnosis, lab, natural language)

#### 3. Eligibility Comparer
- Evaluates patient data against each criterion
- Handles structured criteria with programmatic logic
- Processes natural language criteria using LLM (GPT-4o)
- Manages uncertainty with configurable decision rules

## 📊 Key Features

- **Hybrid Evaluation Approach**: Combines deterministic rule-based processing for structured data with LLM-based analysis for unstructured text
- **Uncertainty Handling**: Configurable permissive/strict logic for managing uncertain assessments
- **Detailed Explanations**: Complete breakdown of how each criterion was assessed
- **Visualization Tools**: Multiple visualizations of eligibility outcomes and failure patterns
- **MIMIC-III Integration**: Direct querying of a realistic clinical database

## 📈 Results & Analysis

Our prototype demonstrates feasibility while highlighting important challenges:

<p align="center">
  <img src="https://raw.githubusercontent.com/yourusername/clinical-trial-automation/main/images/eligibility_pie_charts.png" alt="Eligibility Distribution" width="700"/>
  <br>
  <em>Eligibility Distribution Across Trial Types</em>
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/yourusername/clinical-trial-automation/main/images/criteria_failure_analysis.png" alt="Criteria Failure Analysis" width="600"/>
  <br>
  <em>Frequency of Criteria Leading to Ineligibility</em>
</p>

The system effectively processes both structured criteria (age, lab values, diagnosis codes) and makes reasonable assessments of natural language criteria when sufficient information is available in clinical notes.

## 🧠 LLM Integration

The system leverages OpenAI's GPT-4o to:

- Interpret natural language eligibility criteria
- Extract relevant information from clinical notes
- Make reasoned judgments based on available evidence
- Indicate uncertainty when information is insufficient

Example natural language criteria:
- "Patient is documented as a non-smoker or former smoker"
- "Patient has participated in another investigational drug trial within the last 30 days"

## 🔬 Sample Trials

The system was tested with simplified protocols including:

### CardioHealth Study
A cardiovascular trial with inclusion criteria for:
- Age ≥ 18
- Coronary artery disease (ICD-9: 414)
- eGFR > 10
- Non-smoking status

### Breast Cancer Adjuvant Therapy Trial
An oncology trial targeting:
- Age < 85
- Breast cancer diagnosis (ICD-9: 174)
- Without severe kidney disease

## 🚀 Getting Started

### Prerequisites
- Python 3.9+
- Google Cloud account with BigQuery access
- MIMIC-III dataset access credentials
- OpenAI API key

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/clinical-trial-automation.git
cd clinical-trial-automation

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
export GOOGLE_APPLICATION_CREDENTIALS="path/to/your/credentials.json"
export OPENAI_API_KEY="your-openai-api-key"

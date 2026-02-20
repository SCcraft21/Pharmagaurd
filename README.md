🧬 PharmaGuard
Pharmacogenomic Risk Prediction System
RIFT 2026 Hackathon — HealthTech Track
🚀 Live Demo

🌐 Live Application: [Add your deployed URL here]

🎥 LinkedIn Demo Video: [Add LinkedIn video link here]

📌 Problem Statement

Adverse drug reactions cause over 100,000 deaths annually in the United States. Many of these reactions are preventable through pharmacogenomic testing — analyzing how genetic variants affect drug metabolism.

PharmaGuard is an AI-powered web application that:

Parses authentic VCF (Variant Call Format) files

Identifies pharmacogenomic variants across key genes

Predicts drug-specific risk classifications

Generates clinically actionable explanations using LLMs

Aligns dosing recommendations with CPIC guidelines

🧠 Core Features
✅ VCF File Upload

Supports .vcf files (v4.2 format)

Validates file size (≤ 5MB)

Parses gene and star allele annotations

✅ Drug Risk Prediction

Supports:

CODEINE

WARFARIN

CLOPIDOGREL

SIMVASTATIN

AZATHIOPRINE

FLUOROURACIL

✅ Risk Labels

Safe

Adjust Dosage

Toxic

Ineffective

Unknown

✅ Explainable AI Layer

Uses Mistral-7B-Instruct (Hugging Face)

Generates:

Clinical summary

Biological mechanism

CPIC-aligned recommendation

Includes variant citations

✅ Structured JSON Output

Fully compliant with required hackathon schema.

🏗️ System Architecture
High-Level Flow
User Uploads VCF + Drug Input
        │
        ▼
FastAPI Backend
        │
        ├── VCF Parser
        ├── Rules Engine (CPIC-based logic)
        └── LLM Explainer (Mistral-7B)
        │
        ▼
Structured JSON Response

📂 Project Structure
backend/
│
├── main.py              # FastAPI entry point
├── vcf_parser.py        # VCF parsing logic
├── rules.py             # Risk prediction engine
├── explainer.py         # LLM explanation generation
├── models.py            # Pydantic response models
├── config.py            # Environment configuration
├── requirements.txt
└── .env                 # API keys (not committed)

⚙️ Tech Stack
Backend

Python 3.11

FastAPI

Pydantic

Requests

python-dotenv

LLM

Hugging Face Inference API

Model: mistralai/Mistral-7B-Instruct-v0.2

Deployment

Render (Backend)

Vercel (Frontend)

🧬 Supported Genes

CYP2D6

CYP2C19

CYP2C9

SLCO1B1

TPMT

DPYD

🔍 How It Works
1️⃣ VCF Parsing

Extracts:

Gene annotations

Star alleles

rsIDs

2️⃣ Phenotype Determination

Maps diplotype to:

PM (Poor Metabolizer)

IM (Intermediate Metabolizer)

NM (Normal Metabolizer)

RM (Rapid Metabolizer)

URM (Ultra-rapid Metabolizer)

3️⃣ Risk Classification

Applies CPIC-aligned logic to classify:

Drug efficacy

Toxicity risk

Dosage adjustments

4️⃣ LLM Explainability

Generates structured explanation based on:

Variant evidence

Gene function

Drug metabolism pathway

Clinical implications

📤 API Documentation
POST /analyze
Form Data:

file: VCF file

drugs: Comma-separated drug names

Example Request:
CODEINE,WARFARIN

Example Response Structure:
[
  {
    "patient_id": "PATIENT_XXX",
    "drug": "CODEINE",
    "timestamp": "ISO8601_timestamp",
    "risk_assessment": {
      "risk_label": "Ineffective",
      "confidence_score": 0.9,
      "severity": "moderate"
    },
    "pharmacogenomic_profile": {
      "primary_gene": "CYP2D6",
      "diplotype": "*4/*4",
      "phenotype": "PM",
      "detected_variants": [...]
    },
    "clinical_recommendation": {...},
    "llm_generated_explanation": {...},
    "quality_metrics": {...}
  }
]

🛠 Installation & Local Setup
1️⃣ Clone Repository
git clone <repo-url>
cd PharmaGuard/backend

2️⃣ Install Dependencies
pip install -r requirements.txt

3️⃣ Create .env
HF_API_KEY=hf_your_token_here

4️⃣ Run Backend
uvicorn main:app --reload


Visit:

http://127.0.0.1:8000/docs

🧪 Sample Test Files

Sample VCF files included for:

CODEINE (CYP2D6 PM)

WARFARIN (CYP2C9 IM)

CLOPIDOGREL (CYP2C19 PM)

SIMVASTATIN (SLCO1B1 low function)

Multi-drug test case

🔐 Security & Privacy

No genomic data is stored

No database persistence

API keys stored in .env

.env excluded from version control

Input validation enforced

🎯 Evaluation Alignment
Criteria	Implementation
Problem Clarity	Pharmacogenomic risk modeling
Technical Depth	VCF parsing + CPIC rules
Explainability	LLM-based clinical explanation
JSON Compliance	Exact schema match
Error Handling	Robust validation
Innovation	Modular LLM architecture
👥 Team

Add team member names here

🏁 Submission Checklist

✅ Live deployed backend URL

✅ Public GitHub repository

✅ Public LinkedIn demo video

✅ Complete README with documentation

✅ Working VCF upload

✅ Schema-compliant JSON output

🧠 Future Enhancements

PharmCAT integration

Copy number variation support

Real-time genotype annotation

Drug-drug interaction modeling

Clinical dashboard UI


✅ GitHub Architecture Diagram (Mermaid)
flowchart LR

    A[User Interface]
    A1[VCF File Upload]
    A2[Drug Selection]
    A --> A1
    A --> A2

    B[FastAPI Backend]

    C1[VCF Parser\nGene + Allele Extraction]
    C2[Risk Analysis Engine\nCPIC-Based Rules]
    C3[API Layer\nFastAPI]

    D[LLM Explanation\nMistral-7B-Instruct]

    E[Structured JSON Output]

    A1 --> B
    A2 --> B

    B --> C1
    C1 --> C2
    C2 --> D
    D --> E

    C3 --> C2

✅ Cleaner Professional Version (More Structured)
flowchart TD

    subgraph UI[User Interface]
        UI1[VCF Upload]
        UI2[Drug Input]
    end

    subgraph Backend[PharmaGuard Backend]
        P[VCF Parser]
        R[Risk Engine\nCPIC Rules]
        API[FastAPI Layer]
    end

    subgraph LLM[LLM Layer]
        M[Mistral-7B-Instruct\nHugging Face API]
    end

    subgraph Output[Response Layer]
        J[Structured JSON\nRisk + Explanation]
    end

    UI --> Backend
    P --> R
    R --> M
    M --> J


📜 License

MIT License

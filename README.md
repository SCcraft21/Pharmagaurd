🧬 PharmaGuard
Pharmacogenomic Risk Prediction System
RIFT 2026 Hackathon — HealthTech Track
🚀 Live Demo

🌐 Live Application: [Add your deployed URL here]

🎥 LinkedIn Demo Video: [Add LinkedIn video link here]

📌 Problem Statement

Adverse drug reactions (ADRs) cause over 100,000 deaths annually in the United States. Many of these are preventable through pharmacogenomic testing.

PharmaGuard is an AI-powered web application that:

Parses authentic VCF genomic files

Identifies pharmacogenomic variants

Predicts drug-specific risk levels

Generates explainable clinical insights using LLMs

Aligns recommendations with CPIC guidelines

🏗️ System Architecture
🔷 High-Level Architecture
flowchart LR

    subgraph UI[User Interface]
        U1[VCF File Upload]
        U2[Drug Selection Input]
    end

    subgraph Backend[PharmaGuard Backend - FastAPI]
        P[VCF Parser]
        R[Risk Analysis Engine\n(CPIC-Based Rules)]
        API[API Layer]
    end

    subgraph LLM[LLM Explanation Layer]
        M[Mistral-7B-Instruct\nHugging Face API]
    end

    subgraph Output[Response Layer]
        J[Structured JSON Output]
    end

    U1 --> Backend
    U2 --> Backend

    P --> R
    R --> M
    M --> J

🔷 Detailed Data Flow
sequenceDiagram
    participant User
    participant Frontend
    participant Backend
    participant Parser
    participant Rules
    participant LLM
    participant HF as HuggingFace API

    User->>Frontend: Upload VCF + Drug Input
    Frontend->>Backend: POST /analyze
    Backend->>Parser: Extract variants
    Parser->>Rules: Determine diplotype & phenotype
    Rules->>LLM: Send structured context
    LLM->>HF: Generate explanation
    HF-->>LLM: Return text
    LLM-->>Backend: Structured explanation
    Backend-->>Frontend: JSON Response
    Frontend-->>User: Display results

🧠 Core Components
1️⃣ VCF Parser

Extracts:

Gene symbols

Star alleles

rsIDs

Validates file structure

Handles missing annotations gracefully

2️⃣ Risk Analysis Engine

Implements CPIC-aligned pharmacogenomic logic.

Maps:

Diplotype	Phenotype	Risk
*4/*4	PM	Ineffective
*1/*3	IM	Adjust Dosage
*1/*1	NM	Safe
3️⃣ LLM Explanation Layer

Model:

mistralai/Mistral-7B-Instruct-v0.2


Generates:

Clinical summary

Biological mechanism

CPIC-aligned recommendation

4️⃣ Structured Output

The system produces JSON matching the hackathon-required schema:

{
  "patient_id": "PATIENT_XXX",
  "drug": "CODEINE",
  "timestamp": "ISO8601",
  "risk_assessment": {},
  "pharmacogenomic_profile": {},
  "clinical_recommendation": {},
  "llm_generated_explanation": {},
  "quality_metrics": {}
}

📂 Project Structure
backend/
│
├── main.py              # FastAPI entry
├── vcf_parser.py        # VCF parsing logic
├── rules.py             # CPIC rule engine
├── explainer.py         # Hugging Face LLM integration
├── models.py            # Pydantic schema models
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

Frontend

Next.js (React)

Tailwind CSS

Axios

LLM

Hugging Face Inference API

Mistral-7B-Instruct

🛠 Installation & Setup
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

🚀 Deployment
Backend → Render

Start command:

uvicorn main:app --host 0.0.0.0 --port 10000


Add environment variable:

HF_API_KEY=hf_your_token_here

Frontend → Vercel

Update API endpoint to:

https://your-backend.onrender.com/analyze


Deploy via GitHub integration.

🔐 Security Considerations

No genomic data persistence

No database storage

Environment variables secured

Input validation enforced

CORS configured for production

🎯 Hackathon Evaluation Alignment
Criterion	Implementation
Problem Clarity	Pharmacogenomic risk modeling
Technical Depth	VCF parsing + CPIC rules
Explainability	LLM-generated clinical reasoning
Innovation	Modular AI architecture
JSON Compliance	Exact schema matching
Documentation	Complete README + diagrams
🧪 Testing

Sample VCF files included for:

CODEINE (CYP2D6 PM)

WARFARIN (CYP2C9 IM)

CLOPIDOGREL (CYP2C19 PM)

SIMVASTATIN (SLCO1B1 variant)

Multi-drug cases

👥 Team

Add team member names here

📜 License

MIT License

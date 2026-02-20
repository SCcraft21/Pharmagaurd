🧬 PharmaGuard – Tech Stack
🖥️ Frontend

Framework:

Next.js (React 18)

Styling:

Tailwind CSS

HTTP Client:

Axios

Purpose:

Upload VCF file

Accept drug input

Send POST request to backend

Display structured JSON results

⚙️ Backend

Framework:

FastAPI

Language:

Python 3.11

Server:

Uvicorn (ASGI server)

Validation & Schema:

Pydantic

Environment Management:

python-dotenv

HTTP Requests (LLM calls):

requests

Core Responsibilities:

VCF file handling

Variant extraction

Pharmacogenomic rule engine

LLM explanation integration

Structured JSON output

🧬 Genomic Processing

Custom VCF parsing logic

CPIC-based pharmacogenomic rules

Gene support:

CYP2D6

CYP2C19

CYP2C9

SLCO1B1

TPMT

DPYD

🤖 AI / LLM Layer

Provider:

Hugging Face Inference API

Model:

mistralai/Mistral-7B-Instruct-v0.2

Function:

Generate:

Clinical summary

Mechanism of action

CPIC-aligned recommendation

☁️ Deployment

Frontend Hosting:

Vercel

Backend Hosting:

Render

Environment Variables:

Stored securely via platform dashboard

🔐 Security

.env file for API keys

No database persistence

No genomic data storage

CORS enabled

Input validation enforced

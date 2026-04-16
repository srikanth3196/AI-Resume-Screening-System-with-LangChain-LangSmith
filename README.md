# AI-Resume-Screening-System-with-LangChain-LangSmith

 AI Resume Screening System with Tracing

An intelligent, high-speed recruitment automation tool built with **LangChain**, **Groq (Llama 3)**, and **LangSmith**. This system evaluates resumes against job descriptions with a focus on explainability and performance monitoring.

 Project Overview
This project automates the initial screening of candidates by:
1. Extracting skills, tools, and experience levels.
2. Matching the candidate's profile against specific Job Descriptions (JD).
3. Scoring (0-100) based on objective criteria.
4. Explaining the reasoning behind the score to ensure AI transparency.

Tech Stack
- Framework: [LangChain](https://www.langchain.com/) (using LCEL)
- LLM: [Groq](https://groq.com/) (Llama-3.3-70b-versatile)
- Observability: [LangSmith](https://smith.langchain.com/) (Tracing & Debugging)
- Language: Python 3.x

Architecture
The system follows a modular **LCEL (LangChain Expression Language)** pipeline:
`Input (JD + Resume) -> PromptTemplate -> Groq LPU -> JSON Output Parser -> LangSmith Trace`

Key Features
- **Zero-Hallucination Policy:** The system is prompted to only use information explicitly stated in the resume.
- **Explainable AI (XAI):** Every score comes with a natural language justification.
- **Tracing & Monitoring:** Integrated with LangSmith to monitor latency, token usage, and logic flows.

Getting Started

1. Clone the repository
```bash
git clone https://github.com/your-username/ai-resume-screener.git
cd ai-resume-screener
```

2. Install dependencies
```bash
pip install langchain langchain-groq python-dotenv pandas
```

3. Setup Environment Variables
Create a `.env` file in the root directory:
```env
GROQ_API_KEY=your_groq_api_key
LANGCHAIN_TRACING_V2=true
LANGCHAIN_ENDPOINT="https://api.smith.langchain.com"
LANGCHAIN_API_KEY=your_langsmith_api_key
LANGCHAIN_PROJECT="Resume_Screening_Assignment"
```

4. Run the Pipeline
python main.py

LangSmith Tracing
The pipeline is fully traced. Below is a summary of the monitored runs:
- Strong Candidate: High overlap, high score, clear technical alignment.
- Average Candidate: Partial match, identified missing skill gaps.
- Weak Candidate: Zero relevance, identified by the system with low score.

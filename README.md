# 📋 Enterprise GenAI & RAG Readiness Checklist

> **Author:** Sanket Sawant | AI Solution Architect & GCP Strategist
> **Purpose:** A diagnostic framework used during the Discovery & Advisory phase to assess a client's readiness to move Generative AI (specifically RAG systems) from proof-of-concept to production on Google Cloud.

---

## 1. Business Strategy & ROI Alignment
Before selecting a model, we must define the business value and success criteria.
- [ ] **Use Case Clarity:** Is the problem knowledge-intensive, repetitive, or costly enough to justify GenAI?
- [ ] **Success Metrics (KPIs):** Are there quantifiable metrics for success (e.g., 20% reduction in support ticket resolution time, latency under 2 seconds)?
- [ ] **Stakeholder Alignment:** Is there clear ownership and buy-in from both technical and business stakeholders?
- [ ] **Cost Forecasting:** Has the cost of token usage, vector storage (Vertex AI Search), and serverless compute (Cloud Run) been modeled for production traffic?

## 2. Data Readiness & Governance
*Data chaos is the #1 blocker for enterprise AI. LLMs cannot reason over garbage data.*
- [ ] **Data Discovery:** Are the data sources required for the RAG pipeline identified and accessible?
- [ ] **Data Quality & Freshness:** Is the data normalized? How frequently is the source data updated, and how will the Vector DB sync with these updates?
- [ ] **Data Classification:** Has the data been classified? Are there strict boundaries separating public, internal, and highly confidential data?
- [ ] **Chunking & Embedding Strategy:** Is there a defined strategy for document parsing, chunk size, and embedding model selection (e.g., Google `text-multilingual-embedding`)?

## 3. Architecture & Infrastructure (GCP Ecosystem)
*Ensuring the system is scalable, modular, and cloud-native.*
- [ ] **Integration Interfaces:** Are internal APIs clean, well-documented, and ready to be consumed by an Agentic orchestration layer (like LangChain/LangGraph)?
- [ ] **Compute Strategy:** Is the infrastructure defined? (e.g., Cloud Run for stateless API endpoints, Vertex AI endpoints for model serving).
- [ ] **Search Engine:** Is the retrieval mechanism selected? (e.g., Vertex AI Vector Search vs. Hybrid Search with Keyword/BM25).
- [ ] **Environment Parity:** Are there separate Dev, Staging, and Production environments for safe model experimentation?

## 4. Security, Privacy & Guardrails
*Enterprise AI cannot be "move fast and break things."*
- [ ] **Identity & Access Management (IAM):** Are Google Cloud IAM policies defined using the principle of least privilege for APIs, Cloud Storage, and Vector DBs?
- [ ] **VPC Service Controls:** Is the RAG pipeline isolated within a secure VPC network to prevent data exfiltration?
- [ ] **PII Handling:** Is there a mechanism (like Cloud DLP) to redact sensitive PII before it hits the LLM prompt?
- [ ] **Adversarial Guardrails:** Are input/output filters in place to protect against prompt injection and jailbreaking?

## 5. LLMOps & Continuous Evaluation
*A deployed model is just the beginning.*
- [ ] **RAG Evaluation Triad:** Is there an automated testing framework to measure *Contextual Relevance*, *Faithfulness* (Groundedness), and *Answer Relevancy*?
- [ ] **Audit Logging:** Is BigQuery or Cloud Logging configured to capture user prompts, retrieved context, and LLM responses for auditability?
- [ ] **Human-in-the-Loop (HITL):** For high-risk outputs, is there a UI/workflow for humans to review or override the AI's decision?
- [ ] **Version Control:** Is there a centralized Model Registry and a CI/CD pipeline for deploying prompt changes and model updates?

# Mini AI-Based Vulnerability Analysis System

## Overview
This project is an AI-powered vulnerability analysis system that uses vector embeddings,
Pinecone, and a local Meta LLaMA GGUF model to analyze source code or security scan outputs
and generate structured security vulnerability reports.

## Objective of the System
- The main objectives of this system are:
- To automatically identify common security vulnerabilities in input data
- To retrieve relevant security knowledge using semantic similarity search
- To perform reasoning-based security analysis using a local LLM
- To generate a clear and structured vulnerability report in JSON format
- To demonstrate understanding of backend systems, LLM integration, and security concepts

## Architecture
- The system follows a Retrieval-Augmented Generation (RAG) architecture:

User Input
   ↓
Embedding Model
   ↓
Pinecone Vector Database
   ↓
Relevant Vulnerability Context
   ↓
Local LLaMA GGUF Model
   ↓
Structured Vulnerability Report

## Features
- Local LLaMA inference (no cloud LLM)
- Pinecone-based similarity search
- OWASP and CVE knowledge retrieval
- Structured JSON output
- Supports SQL Injection, XSS, Command Injection, Open Ports

## Setup Instructions
1. Install Dependencies
- The system requires specific Python libraries to support local LLM inference, vector embeddings, and vector database communication. These dependencies are         installed using Python’s package manager.
The required dependencies include:
. llama-cpp-python – for running Meta LLaMA GGUF models locally
. pinecone-client – for interacting with the Pinecone vector database
. sentence-transformers – for generating text embeddings
. These libraries enable semantic search and AI-based security vulnerability reasoning.

2. Environment Configuration
- To securely connect with Pinecone, an API key is required. The key is stored as an environment variable instead of being hardcoded, ensuring better security and
  preventing accidental exposure.
This configuration ensures:
. Secure authentication with Pinecone
. Clear separation of configuration and application logic

3. Vector Database Initialization
- A Pinecone index is created to store embeddings of vulnerability-related documents such as:
- OWASP Top 10 summaries
- Common vulnerability explanations
- Sample CVE descriptions
- If the index already exists, the system reuses it. This allows efficient semantic similarity search during analysis.

4. LLaMA Model Setup
- This project uses a local Meta LLaMA GGUF model for offline vulnerability analysis using llama-cpp-python.
- Due to GitHub file size limitations, the model file is not included in the repository.
# Download Instructions
- Download the GGUF model from Hugging Face:
. https://huggingface.co/TheBloke/Llama-2-7B-Chat-GGUF
  
- Select and download the following file:
. llama-2-7b-chat.Q4_K_M.gguf
  
- Place the downloaded model file in the project root directory.
- Once placed correctly, the application will automatically load the model for local inference.

5. Loading Vulnerability Knowledge Base
- A collection of vulnerability-related documents is stored in the data/ directory. These documents are embedded and indexed into Pinecone to create a searchable
  knowledge base.
- This enables the system to retrieve relevant security context for accurate vulnerability identification.

6. Running the Application
- After completing the setup:
. The user provides an input (code snippet, scan output, or dependency list)
. The system retrieves relevant vulnerability context using vector similarity search
. The local LLaMA model generates a structured vulnerability report

7. Validation and Testing
- Sample inputs are provided to validate system functionality. These tests verify:
- Correct vulnerability detection
- Accurate severity assessment
- Meaningful remediation recommendations
  
##  Structured Vulnerability Report
The final output is a structured JSON object:

{
  "vulnerability": "",
  "severity": "",
  "description": "",
  "impact": "",
  "remediation": []
}


This format is suitable for:
- Automated reporting
- Security dashboards
- Further processing or storage

## Security Analysis Capability
- The system is capable of identifying at least one of the following vulnerabilities:
. SQL Injection – Unsafe query construction using user input
. Cross-Site Scripting (XSS) – Unsanitized user input rendered in output
. Command Injection – Execution of system commands using user input
. Insecure Dependencies – Use of outdated or vulnerable libraries
. Open Ports / Misconfiguration – Exposed services increasing attack surface
. The analysis is performed using both retrieved knowledge and LLM reasoning.

## Conclusion
- This mini AI-based vulnerability analysis system demonstrates how modern AI techniques such as embeddings, vector databases, and local LLMs can be effectively applied to cybersecurity problem-solving. By combining semantic retrieval with reasoning-based analysis, the system provides meaningful security insights in a structured and automated manner.
- The project successfully showcases backend engineering skills, LLM integration, and security domain understanding within a practical and scalable architecture.

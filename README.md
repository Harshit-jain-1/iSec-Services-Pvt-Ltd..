# Mini AI-Based Vulnerability Analysis System

## Overview
This project is an AI-powered vulnerability analysis system that uses vector embeddings,
Pinecone, and a local Meta LLaMA GGUF model to analyze source code or security scan outputs
and generate structured security vulnerability reports.

## Architecture
User Input → Embeddings → Pinecone Vector Search → Context Retrieval →
LLaMA GGUF Analysis → JSON Vulnerability Report

## Features
- Local LLaMA inference (no cloud LLM)
- Pinecone-based similarity search
- OWASP and CVE knowledge retrieval
- Structured JSON output
- Supports SQL Injection, XSS, Command Injection, Open Ports

## Setup Instructions
1. Install dependencies:

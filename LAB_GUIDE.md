# Lab Exercise Overview

This document provides a quick reference guide to all available lab exercises in this repository.

## Lab Exercises (in recommended order)

### Lab 1: Explore Azure AI Studio
**File:** `Instructions/01-Explore-ai-studio.md`  
**Duration:** ~30 minutes  
**Description:** Learn how to organize cloud resources in Azure AI Foundry projects so that developers are set up for success when building AI solutions.

**What you'll learn:**
- How to navigate Azure AI Foundry portal
- Creating and managing AI projects
- Understanding project resources and workspace structure

---

### Lab 2: Explore Model Catalog
**File:** `Instructions/02-Explore-model-catalog.md`  
**Duration:** ~30 minutes  
**Description:** Discover and work with pre-built AI models available in the Azure AI model catalog.

**What you'll learn:**
- Browsing the model catalog
- Understanding model capabilities and benchmarks
- Deploying models for use in your projects

---

### Lab 2a: AI Foundry SDK
**File:** `Instructions/02a-AI-foundry-sdk.md`  
**Duration:** ~30 minutes  
**Description:** Learn to work with Azure AI Foundry using the SDK for programmatic access.

**What you'll learn:**
- Installing and configuring the AI Foundry SDK
- Programmatic access to AI services
- Code-first development approach

---

### Lab 3: Use Prompt Flow (Chat)
**File:** `Instructions/03-Use-prompt-flow-chat.md`  
**Duration:** ~30 minutes  
**Description:** Build chat applications using Azure AI's prompt flow capabilities.

**What you'll learn:**
- Creating chat flows
- Testing and debugging prompts
- Deploying chat applications

**Related files:**
- `labfiles/chat-app/python/chat-app.py`
- `labfiles/chat-app/python/requirements.txt`

---

### Lab 4: Use Your Own Data
**File:** `Instructions/04-Use-own-data.md`  
**Duration:** ~30 minutes  
**Description:** Learn to integrate custom data sources with Azure AI models for enhanced responses.

**What you'll learn:**
- Uploading and indexing custom data
- Configuring RAG (Retrieval-Augmented Generation)
- Testing with your own data

**Related files:**
- `data/brochures.zip`
- `labfiles/rag-app/python/rag-app.py`
- `labfiles/rag-app/python/requirements.txt`

---

### Lab 5: Finetune Model
**File:** `Instructions/05-Finetune-model.md`  
**Duration:** ~30 minutes  
**Description:** Fine-tune AI models for specific tasks and domains.

**What you'll learn:**
- Preparing training data
- Fine-tuning process
- Evaluating fine-tuned models

**Related files:**
- `data/travel-finetune.jsonl`
- `data/travel-finetune-hotel.jsonl`
- `data/travel-finetune-validation.jsonl`

---

### Lab 6: Explore Content Filters
**File:** `Instructions/06-Explore-content-filters.md`  
**Duration:** ~30 minutes  
**Description:** Implement content filtering and safety measures in AI applications.

**What you'll learn:**
- Understanding content safety categories
- Configuring content filters
- Testing filter effectiveness

---

### Lab 7: Evaluate Prompt Flow
**File:** `Instructions/07-Evaluate-prompt-flow.md`  
**Duration:** ~30 minutes  
**Description:** Learn to test and evaluate prompt flows systematically.

**What you'll learn:**
- Setting up evaluation datasets
- Running evaluations
- Analyzing results and metrics

**Related files:**
- `data/travel_evaluation_data.csv`
- `data/travel_evaluation_data.jsonl`
- `data/travel-qa.jsonl`
- `data/travel-questions.jsonl`

---

## Archived Labs

These labs are in the `Instructions/archive/` directory and may be based on older versions or different approaches:

- `03b-Use-prompt-flow-NER.md` - Named Entity Recognition with Prompt Flow
- `08-Code-first-development.md` - Code-first development approaches

---

## Data Files Reference

### Training Data
- `data/travel-finetune.jsonl` - Fine-tuning training data
- `data/travel-finetune-hotel.jsonl` - Hotel-specific training data
- `data/travel-finetune-validation.jsonl` - Validation dataset

### Evaluation Data
- `data/travel_evaluation_data.csv` - Evaluation dataset (CSV format)
- `data/travel_evaluation_data.jsonl` - Evaluation dataset (JSONL format)
- `data/travel-qa.jsonl` - Question-answer pairs
- `data/travel-questions.jsonl` - Test questions

### Sample Data
- `data/brochures.zip` - Sample brochures for RAG exercises
- `text-files/sample-text.txt` - Sample text file

---

## Application Files

### Chat Application
Location: `labfiles/chat-app/python/`
- `chat-app.py` - Main chat application
- `requirements.txt` - Python dependencies

### RAG Application
Location: `labfiles/rag-app/python/`
- `rag-app.py` - Retrieval-Augmented Generation application
- `requirements.txt` - Python dependencies

---

## Getting Started Tips

1. **Start with Lab 1** to set up your Azure environment
2. **Complete Lab 2** to understand available models
3. **Follow the labs sequentially** for the best learning experience
4. **Have an Azure subscription ready** before starting
5. **Each lab takes about 30 minutes** - plan accordingly
6. **Keep your Azure resources** between labs if you plan to complete multiple exercises

---

## Additional Resources

- [Microsoft Learn Path](https://aka.ms/mslearn-generative-ai)
- [Azure AI Foundry Documentation](https://learn.microsoft.com/azure/ai-studio/)
- [Azure AI Services](https://azure.microsoft.com/services/cognitive-services/)

---

*Last updated: October 2025*

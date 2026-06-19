# AWS Certified AI Practitioner (AIF-C01) — Complete Study Guide

> **Exam:** Amazon AWS Certified AI Practitioner (AIF-C01)  
> **Format:** ~85 questions | Multiple choice & hotspot drag-and-drop  
> **Audience:** Anyone exploring AI/ML on AWS — no coding background required

---

## Table of Contents

1. [Key Topics & Domain Breakdown](#1-key-topics--domain-breakdown)
2. [Critical Pointers & Exam Tips](#2-critical-pointers--exam-tips)
3. [AWS AI/ML Services Cheat Sheet](#3-aws-aiml-services-cheat-sheet)
4. [Core Concepts Reference](#4-core-concepts-reference)
5. [300 Practice Questions with Answers](#5-300-practice-questions-with-answers)

---

## 1. Key Topics & Domain Breakdown

### Domain 1 — Fundamentals of AI and ML (~20%)
- Types of ML: supervised, unsupervised, reinforcement learning
- ML pipeline stages: data collection → preprocessing → feature engineering → training → evaluation → deployment → monitoring
- Key algorithms: decision trees, logistic regression, k-means, neural networks, GANs, transformers
- AI vs ML vs Deep Learning distinctions
- Data types: tabular, text, image, audio, time series

### Domain 2 — Fundamentals of Generative AI (~24%)
- Foundation models (FMs) and large language models (LLMs)
- Tokens, embeddings, context windows
- Inference parameters: temperature, Top-K, Top-P, max tokens
- Prompt engineering: zero-shot, few-shot, chain-of-thought
- RAG (Retrieval Augmented Generation)
- Model customization: prompt engineering → RAG → fine-tuning → continued pre-training
- Generative AI lifecycle: data selection → model selection → fine-tuning → evaluation → deployment → monitoring
- Hallucinations, nondeterminism, bias in generative AI

### Domain 3 — Applications of Foundation Models (~28%)
- Amazon Bedrock: FMs, agents, knowledge bases, guardrails, model evaluation
- Amazon SageMaker: JumpStart, Canvas, Clarify, Ground Truth, Model Monitor, Data Wrangler
- Prompt Management, invocation logging, Provisioned Throughput
- SageMaker inference types: real-time, serverless, asynchronous, batch transform
- Amazon Nova model family: Lite, Pro, Canvas, Reel
- Vector databases: OpenSearch Service for embeddings and RAG

### Domain 4 — Guidelines for Responsible AI (~14%)
- Responsible AI pillars: fairness, transparency, explainability, robustness, privacy, security
- Bias types: sampling bias, measurement bias, observer bias, confirmation bias
- SageMaker Clarify for bias detection and explainability
- Guardrails for content moderation (hate, violence, denied topics, word filters, contextual grounding)
- Regulatory and governance concepts: data residency, data retention, data de-identification

### Domain 5 — Security, Compliance & Governance (~14%)
- AWS PrivateLink for private VPC connectivity
- IAM roles, least privilege, cross-service permissions
- AWS CloudTrail for audit logging of API calls
- AWS Artifact for compliance reports
- AWS KMS for encryption
- Amazon Macie for PII detection in S3
- Amazon Bedrock invocation logging

---

## 2. Critical Pointers & Exam Tips

### Must-Know Service Distinctions

| Need | Correct Service | Common Wrong Answers |
|------|----------------|----------------------|
| Private VPC connectivity to Bedrock | AWS PrivateLink | CloudFront, Internet Gateway |
| Content moderation / safety rules on LLM | Bedrock Guardrails | Macie, CloudTrail |
| Bias detection in training data | SageMaker Clarify | Macie, Inspector |
| Audit trail for API calls | AWS CloudTrail | Audit Manager, CloudWatch |
| Compliance reports from ISVs | AWS Artifact | Trusted Advisor, Audit Manager |
| Human-in-loop labeling (managed) | SageMaker Ground Truth Plus | Ground Truth, A2I |
| Human review of AI outputs | Amazon A2I (Augmented AI) | Ground Truth Plus |
| No-code ML model building | SageMaker Canvas | Data Wrangler, SageMaker Studio |
| Enterprise search over documents | Amazon Kendra | Comprehend, Textract |
| Recommendation systems | Amazon Personalize | Comprehend, Kendra |
| Audio-to-text transcription | Amazon Transcribe | Polly, Lex |
| Text-to-speech | Amazon Polly | Transcribe, Lex |
| Chatbot/conversational interface | Amazon Lex | Comprehend, Polly |
| Text analysis / NLP / sentiment | Amazon Comprehend | Lex, Rekognition |
| PDF / document text extraction | Amazon Textract | Comprehend, Rekognition |
| Image/video analysis | Amazon Rekognition | Textract, Comprehend |
| Data visualization / BI dashboards | Amazon QuickSight | CloudWatch, Athena |
| Developer coding assistant | Amazon Q Developer | Amazon Q Business |
| Employee internal Q&A over company data | Amazon Q Business | Q Developer, Kendra |
| Rapid generative AI prototyping (no-infra) | Amazon Bedrock PartyRock | SageMaker Studio, EC2 |

### Inference Type Selection Rules

| Scenario | Use |
|----------|-----|
| Low-latency, real-time predictions | Real-time inference |
| Large datasets (GBs), no immediate need | Batch transform |
| Large payloads (up to 1 GB), near real-time | Asynchronous inference |
| Infrequent, small-scale requests, no infra | Serverless inference |

### Model Customization — Effort Order (Least → Most)
1. **Prompt engineering** — write better prompts, zero cost
2. **RAG** — retrieval-augmented generation, no retraining
3. **Fine-tuning** — labeled data required, model weights updated
4. **Continued pre-training** — unlabeled domain data, large-scale training

### Key Inference Parameters

| Parameter | Effect | Set to 0 for… |
|-----------|--------|---------------|
| Temperature | Controls randomness/creativity | Deterministic output |
| Top-K | Limits token candidates | — |
| Top-P (nucleus) | Probability mass threshold | — |
| Max tokens | Maximum output length | — |

### Evaluation Metrics — Quick Reference

| Metric | Used For |
|--------|----------|
| Accuracy | Classification (balanced classes) |
| F1 Score | Classification (imbalanced classes) |
| Precision | Minimize false positives |
| Recall | Minimize false negatives |
| RMSE / MSE | Regression tasks |
| R-squared | Regression fit |
| ROUGE | Text summarization quality |
| BLEU | Machine translation quality |
| AUC-ROC | Binary classifier performance |

### Amazon Bedrock — Key Facts
- **Invocation costs** are driven by **number of tokens consumed**
- **On-Demand pricing** = no commitment, pay-per-use
- **Provisioned Throughput** = reserved capacity, consistent performance, required for custom models
- Custom models **require Provisioned Throughput** to be invoked
- Bedrock **never shares** customer prompts/outputs with model providers
- **Invocation logging** must be explicitly enabled to capture input/output logs

### Responsible AI — Core Pillars
- **Fairness** — detect and mitigate bias across demographic groups
- **Transparency** — explain how models make decisions
- **Explainability** — provide model cards, SHAP values (SageMaker Clarify)
- **Robustness** — model performs under unexpected inputs
- **Privacy & Security** — protect PII, use encryption, least privilege
- **Veracity** — accuracy and truthfulness of outputs

---

## 3. AWS AI/ML Services Cheat Sheet

### Amazon Bedrock
- Fully managed service for accessing FMs from multiple providers
- **Guardrails**: content filters, denied topics, word filters, contextual grounding checks, PII redaction
- **Agents**: multi-step task execution, API orchestration
- **Knowledge Bases**: RAG integration with vector stores (OpenSearch)
- **Model Evaluation**: compare multiple FMs with human or automated scoring
- **Prompt Management**: reusable, versioned prompts with tool configurations
- **PartyRock**: no-code playground for experimenting with generative AI apps

### Amazon SageMaker
- **Canvas**: no-code ML model building for non-technical users
- **Clarify**: bias detection + model explainability (SHAP feature attribution)
- **Ground Truth / Ground Truth Plus**: data labeling with human workforce
- **Model Monitor**: detects data drift and model quality degradation
- **Data Wrangler**: no-code/low-code data preparation
- **JumpStart**: deploy and fine-tune pre-built open source models with least effort
- **Feature Store**: centralized feature management
- **Model Cards**: document model transparency for audits
- **Experiments**: track and compare ML runs
- **Pipelines**: orchestrate end-to-end ML workflows

### AWS AI Services (Pre-Built)
- **Amazon Comprehend**: NLP — sentiment, entities, key phrases, topic modeling
- **Amazon Transcribe**: speech-to-text
- **Amazon Polly**: text-to-speech
- **Amazon Lex**: conversational chatbots
- **Amazon Rekognition**: image/video analysis, content moderation
- **Amazon Textract**: extract text and structured data from documents/PDFs
- **Amazon Translate**: language translation
- **Amazon Personalize**: personalized recommendations
- **Amazon Kendra**: intelligent enterprise document search
- **Amazon Q Developer**: AI coding assistant in IDE
- **Amazon Q Business**: enterprise AI assistant over internal data

### Security & Governance Services
- **AWS CloudTrail**: logs all API calls — unauthorized access detection
- **AWS PrivateLink**: private connectivity from VPC to AWS services
- **Amazon Macie**: detects PII/sensitive data in S3
- **AWS Artifact**: compliance reports and certifications
- **AWS KMS**: encryption key management
- **AWS Audit Manager**: continuous compliance assessment frameworks
- **Amazon Inspector**: vulnerability scanning for EC2/containers

---

## 4. Core Concepts Reference

### Types of Machine Learning

**Supervised Learning** — labeled data, known outputs
- Binary classification (spam/not spam, urgent/non-urgent)
- Multi-class classification (disease type, car model)
- Regression (price prediction, numerical forecasting)
- Algorithms: logistic regression, decision trees, SVM, neural networks

**Unsupervised Learning** — unlabeled data, discover patterns
- Clustering: k-means (customer segmentation)
- Dimensionality reduction: PCA
- Anomaly detection: autoencoders
- Topic modeling

**Reinforcement Learning** — agent learns via rewards/penalties
- Game playing, robotics, chatbot self-improvement (RLHF)

### Types of Bias
- **Sampling bias**: training data over/under-represents certain groups
- **Measurement bias**: incorrect or inconsistent data collection
- **Observer bias**: human labelers introduce their own prejudices
- **Confirmation bias**: model trained to confirm existing assumptions

### Overfitting vs Underfitting
- **Overfitting**: model memorizes training data, fails on new data — high training accuracy, low test accuracy
  - Fix: more training data, regularization, dropout, reduce model complexity
- **Underfitting**: model too simple, misses patterns — low accuracy on both
  - Fix: more complex model, more features, more epochs

### Generative AI Terminology
- **Token**: basic unit of text (word, subword, character) — costs are per token
- **Embedding**: numerical vector representation of text/images capturing semantic meaning
- **Context window**: maximum tokens a model can process in one prompt
- **Hallucination**: model generates plausible but factually incorrect content
- **Nondeterminism**: same input produces different outputs across invocations
- **Grounding**: connecting model outputs to verified source documents
- **RAG**: augments model with external documents at inference time — no retraining needed

### The ML Pipeline Stages
1. Define business goal
2. Data collection
3. Data preprocessing (cleaning, filtering, encoding)
4. Exploratory Data Analysis (EDA — correlation matrices, statistics, visualization)
5. Feature engineering (creating new features from raw data)
6. Model training
7. Model evaluation (accuracy, F1, ROUGE, etc.)
8. Model deployment
9. Model monitoring (data drift, model drift)

### Foundation Model Characteristics
- **Context window**: how much fits in one prompt
- **Latency**: time to generate a response
- **Concurrency**: simultaneous requests an endpoint handles
- **Throughput**: tokens/requests processed per second

### Amazon Nova Model Family
| Model | Type | Best For |
|-------|------|----------|
| Nova Lite | Multimodal (text+image) | Cost-effective multilingual tasks |
| Nova Pro | Multimodal (text+image) | Complex reasoning, high performance |
| Nova Canvas | Image generation | High-quality image creation |
| Nova Reel | Video generation | Text-to-video content creation |

### Bedrock Guardrails Filter Types
| Filter | Purpose |
|--------|---------|
| Content filters | Block hate, violence, sexual content, misconduct |
| Denied topics | Block specific subject areas |
| Word filters | Block specific words/phrases |
| PII redaction | Remove personal identifiers |
| Contextual grounding check | Block ungrounded responses |

---
## 5. 300 Practice Questions with Answers

*Questions organized by topic, medium to hard difficulty.*

---

### Section A — AWS Services & Architecture (Q1–Q60)

**Q1.** A company runs a healthcare chatbot on Amazon Bedrock. The chatbot must never reveal patient names or medical record numbers in its responses. Which Bedrock feature should be configured?

A) Model evaluation jobs | B) Invocation logging | C) Guardrails with PII redaction | D) Provisioned Throughput

**Answer: C** — Bedrock Guardrails PII redaction filters detect and remove personal identifiers from model inputs and outputs.

---

**Q2.** An AI team needs to deploy a foundation model inside a VPC without any traffic leaving the AWS network. Which service enables this?

A) Amazon CloudFront | B) AWS PrivateLink | C) Internet Gateway | D) AWS Transit Gateway

**Answer: B** — AWS PrivateLink creates private endpoints keeping traffic within the AWS network.

---

**Q3.** A company wants its LLM to only respond to product catalog topics. Which Bedrock Guardrails feature blocks off-topic requests?

A) Content filters | B) Word filters | C) Denied topics | D) Contextual grounding check

**Answer: C** — Denied topics explicitly block the model from engaging with subjects outside defined business scope.

---

**Q4.** A company needs to process 500 GB of product review text overnight for sentiment scores. Which SageMaker inference option is most appropriate?

A) Real-time inference | B) Serverless inference | C) Asynchronous inference | D) Batch transform

**Answer: D** — Batch transform is designed for large offline datasets where immediate responses are not required.

---

**Q5.** A developer needs to track which IAM user invoked an Amazon Bedrock model at 2:00 AM Tuesday. Which service provides this?

A) Amazon CloudWatch | B) AWS CloudTrail | C) AWS Audit Manager | D) Amazon Macie

**Answer: B** — CloudTrail records all API calls with timestamps, user identity, and resource details.

---

**Q6.** A startup wants to test three different foundation models on the same set of prompts before selecting one for production. Which Bedrock capability supports this?

A) Bedrock Agents | B) Bedrock Knowledge Bases | C) Bedrock Model Evaluation | D) Bedrock Prompt Management

**Answer: C** — Bedrock Model Evaluation compares multiple FMs using the same prompt sets with human or automated scoring.

---

**Q7.** A financial firm must store AI training data within a specific country's borders to comply with local regulations. Which governance concept describes this?

A) Data retention | B) Data residency | C) Data de-identification | D) Data lineage

**Answer: B** — Data residency requires that data physically remain within a defined geographic region.

---

**Q8.** A company trained a custom model on Amazon Bedrock and wants to serve it via the API. What must be configured first?

A) AWS Lambda endpoint | B) SageMaker endpoint | C) Provisioned Throughput | D) On-Demand pricing tier

**Answer: C** — Custom models on Amazon Bedrock require Provisioned Throughput before they can be invoked.

---

**Q9.** An organization needs to detect data drift in a SageMaker classification model and receive alerts. Which feature provides this?

A) SageMaker Clarify | B) SageMaker Model Monitor | C) SageMaker Data Wrangler | D) SageMaker Canvas

**Answer: B** — SageMaker Model Monitor continuously evaluates production data for drift and triggers automated alerts.

---

**Q10.** A business analyst with no coding experience wants to build a churn prediction model. Which AWS service requires the least technical effort?

A) SageMaker Studio with custom notebooks | B) SageMaker Canvas | C) SageMaker JumpStart | D) Amazon Comprehend custom classifier

**Answer: B** — SageMaker Canvas provides a fully visual, no-code interface for building ML models.

---

**Q11.** A company wants to explain why its content moderation model flagged specific text. Which SageMaker feature provides feature-level attribution?

A) SageMaker Ground Truth | B) SageMaker Feature Store | C) SageMaker Clarify | D) SageMaker Model Registry

**Answer: C** — SageMaker Clarify uses SHAP values to show how each input feature contributed to a prediction.

---

**Q12.** A law firm needs to extract structured information (dates, names, dollar amounts) from thousands of scanned contracts. Which AWS service is most appropriate?

A) Amazon Comprehend | B) Amazon Textract | C) Amazon Transcribe | D) Amazon Rekognition

**Answer: B** — Amazon Textract extracts text and structured data (forms, tables) from scanned documents and PDFs.

---

**Q13.** A company wants to automatically tag product images with labels like "shoes" or "handbag." Which AWS service handles this without custom code?

A) Amazon Textract | B) Amazon Comprehend | C) Amazon Rekognition | D) Amazon Personalize

**Answer: C** — Amazon Rekognition detects and classifies objects in images, supporting label detection.

---

**Q14.** A streaming service wants to show movie recommendations based on viewing history. Which AWS service is purpose-built for this?

A) Amazon Kendra | B) Amazon Comprehend | C) Amazon Personalize | D) Amazon Forecast

**Answer: C** — Amazon Personalize is a managed ML service for building real-time personalized recommendation systems.

---

**Q15.** A company needs its HR chatbot to search through 10,000 policy documents. Which AWS service provides intelligent enterprise document search?

A) Amazon Comprehend | B) Amazon Kendra | C) Amazon Lex | D) Amazon OpenSearch

**Answer: B** — Amazon Kendra is an enterprise intelligent search service supporting natural language queries over large document sets.

---

**Q16.** A call center stores customer recordings in S3 and wants to detect PII such as Social Security numbers. Which service provides this?

A) Amazon Macie | B) Amazon Inspector | C) AWS Artifact | D) AWS CloudTrail

**Answer: A** — Amazon Macie uses ML to automatically discover and classify sensitive data including PII in Amazon S3.

---

**Q17.** An AI application on Amazon Bedrock must log all model inputs and outputs for compliance auditing. Which action enables this?

A) Enable AWS CloudTrail API logging | B) Configure AWS Audit Manager | C) Enable invocation logging in Amazon Bedrock | D) Set up Amazon EventBridge rules

**Answer: C** — Amazon Bedrock has a built-in invocation logging setting that captures model input/output data.

---

**Q18.** A company wants to build a voice-enabled customer service application. Which TWO AWS services are needed for speech understanding and intent routing?

A) Amazon Polly | B) Amazon Transcribe | C) Amazon Lex | D) Amazon Comprehend | E) Amazon Rekognition

**Answer: B, C** — Transcribe converts speech to text; Lex handles intent detection and routing to backend systems.

---

**Q19.** A model on Amazon Bedrock needs to read from an S3 bucket with SSE-S3 encryption but fails. What is the most likely fix?

A) Make the S3 bucket publicly accessible | B) Disable SSE-S3 encryption | C) Ensure the Bedrock execution role has s3:GetObject permission | D) Use Amazon Macie to allow access

**Answer: C** — The Bedrock service role must have the correct IAM permissions to read from the encrypted bucket.

---

**Q20.** A data science team wants to quickly deploy a pre-trained Llama 2 open source model with minimum setup. Which service offers one-click deployment?

A) SageMaker Canvas | B) SageMaker Clarify | C) SageMaker JumpStart | D) SageMaker Feature Store

**Answer: C** — SageMaker JumpStart provides a hub of pre-trained open source models deployable with minimal effort.

---

**Q21.** A retail company's Bedrock model sometimes generates content about competitor brands. Which Bedrock feature prevents this?

A) Contextual grounding check | B) Denied topics | C) Content filters | D) Word filters

**Answer: B** — Denied topics allows prohibiting specific subjects (like competitor brands) from model outputs.

---

**Q22.** A company collects sensor readings every minute for two years to predict equipment failures. What type of data is this?

A) Tabular data | B) Image data | C) Time series data | D) Text data

**Answer: C** — Sensor readings at regular intervals constitute time series data, ideal for predictive maintenance models.

---

**Q23.** A company wants Amazon Bedrock API calls completely private. Which solution meets this requirement?

A) Enable CloudFront caching | B) Use AWS PrivateLink with a VPC endpoint | C) Configure an S3 bucket policy | D) Use Amazon Route 53 private hosted zones

**Answer: B** — AWS PrivateLink creates a private interface endpoint routing all Bedrock API calls through the AWS internal network.

---

**Q24.** A healthcare company needs AI model predictions for clinical decisions to be explained to doctors. Which SageMaker tool generates model explanation reports?

A) SageMaker Pipelines | B) SageMaker Model Monitor | C) SageMaker Clarify | D) SageMaker Experiments

**Answer: C** — SageMaker Clarify produces explainability reports showing SHAP feature importance values.

---

**Q25.** A team wants to build a prototype AI app that answers questions about uploaded PDFs, without writing any infrastructure code. Which offering is best?

A) SageMaker Studio | B) Amazon Bedrock PartyRock | C) Amazon EC2 with GPU | D) AWS Lambda with Bedrock SDK

**Answer: B** — PartyRock is a no-code playground for building generative AI apps without provisioning any infrastructure.

---

**Q26.** An organization needs to download its AWS SOC 2 report to share with a client. Which AWS service hosts this?

A) AWS Trusted Advisor | B) AWS Security Hub | C) AWS Audit Manager | D) AWS Artifact

**Answer: D** — AWS Artifact is the self-service portal for AWS compliance reports and agreements.

---

**Q27.** A company processes 800 MB transcription files through an LLM, taking 45 minutes each. Results don't need to be instant. Which SageMaker inference type fits?

A) Real-time inference | B) Serverless inference | C) Asynchronous inference | D) Batch transform

**Answer: C** — Asynchronous inference handles payloads up to 1 GB with processing times up to 1 hour.

---

**Q28.** A bank needs to document decision-making logic, training sources, and fairness metrics for its loan approval model for external audit. Which AWS resource stores this?

A) SageMaker Pipelines | B) SageMaker Model Card | C) SageMaker Experiments | D) SageMaker Feature Store

**Answer: B** — SageMaker Model Cards document model details, intended use, training information, and fairness metrics.

---

**Q29.** A company's AI content pipeline must route AI-generated product descriptions for human marketing review before publication. Which service manages this?

A) Amazon SageMaker Ground Truth Plus | B) Amazon Augmented AI (A2I) | C) Amazon SageMaker Clarify | D) Amazon Rekognition

**Answer: B** — Amazon A2I provides built-in workflows for integrating human review into AI prediction pipelines.

---

**Q30.** A software engineer wants AI assistance to explain code, suggest unit tests, and flag open-source license risks inside an IDE. Which AWS service provides this?

A) Amazon Q Business | B) Amazon CodeGuru | C) Amazon Q Developer | D) AWS Lambda

**Answer: C** — Amazon Q Developer integrates into IDEs to provide code explanations, test generation, and license tracking.

---

**Q31.** A company uses Amazon Comprehend for support ticket categorization and wants an alert when "billing issue" tickets exceed 100/hour. Which service monitors this?

A) AWS CloudTrail | B) Amazon CloudWatch | C) AWS Config | D) Amazon Inspector

**Answer: B** — Amazon CloudWatch tracks custom metrics and triggers alarms based on defined thresholds.

---

**Q32.** SageMaker Model Monitor flagged data drift in a deployed model. What is the correct remediation?

A) Restart the SageMaker endpoint | B) Increase monitoring frequency | C) Retrain the model with fresh, current data | D) Adjust model hyperparameters

**Answer: C** — Retraining with fresh data is the standard remediation when Model Monitor detects drift.

---

**Q33.** A team wants Bedrock to access proprietary product documentation that changes weekly, without retraining. Which architecture to use?

A) Fine-tune the model weekly | B) Use Bedrock Knowledge Bases with RAG | C) Increase max tokens per invocation | D) Use continued pre-training monthly

**Answer: B** — Bedrock Knowledge Bases with RAG retrieves the latest documents dynamically at inference time.

---

**Q34.** A developer wants identical outputs for the same prompt every time. What single change achieves deterministic output?

A) Increase max_tokens to 2000 | B) Set temperature to 0 | C) Set Top-P to 1.0 | D) Enable response streaming

**Answer: B** — Setting temperature to 0 eliminates randomness, always selecting the highest-probability token.

---

**Q35.** A company wants to use generative AI to extract action items and summarize decisions from meeting transcripts. Which generative AI use case is this?

A) Translation | B) Classification | C) Summarization | D) Image generation

**Answer: C** — Summarization uses LLMs to condense and extract key information from long documents.

---

**Q36.** A Bedrock-powered chatbot returns information not supported by reference documents. Which Guardrails feature addresses this?

A) Content filters | B) Word filters | C) Denied topics | D) Contextual grounding check

**Answer: D** — Contextual grounding check blocks model responses not grounded in provided source documents.

---

**Q37.** A team is storing feature vectors for millions of products to power similarity search. Which AWS database service supports vector storage and nearest-neighbor search?

A) Amazon DynamoDB | B) Amazon RDS for PostgreSQL | C) Amazon OpenSearch Service | D) Amazon Redshift

**Answer: C** — Amazon OpenSearch Service supports k-NN vector search for similarity search over high-dimensional embeddings.

---

**Q38.** A company wants its AI development team to build fair AI systems. What training should they prioritize?

A) Advanced coding skills | B) Data encryption techniques | C) Bias awareness and responsible AI | D) AWS networking fundamentals

**Answer: C** — Training on bias awareness and responsible AI equips teams to identify and reduce bias in data and models.

---

**Q39.** A company needs to process 10 million customer reviews for sentiment classification within 12 hours. Which approach is most cost-effective?

A) Real-time inference endpoint | B) Serverless inference | C) SageMaker Batch Transform | D) Asynchronous inference

**Answer: C** — Batch transform is optimized for large-scale offline processing at the lowest cost when immediate results are not needed.

---

**Q40.** A company needs an AI assistant that can query a CRM API, check inventory, and compose a response in one user interaction. Which Bedrock feature enables this?

A) Bedrock Knowledge Bases | B) Bedrock Guardrails | C) Bedrock Agents | D) Bedrock Prompt Management

**Answer: C** — Bedrock Agents orchestrate multi-step workflows, call external APIs, and reason over intermediate results.

---

**Q41.** A retailer wants to prevent users from asking its chatbot about topics unrelated to retail (politics, medical advice). Which Guardrails component is used?

A) Denied topics | B) Content filters (violence, hate) | C) Word filters | D) PII redaction

**Answer: A** — Denied topics restrict the model to only respond within defined subject areas.

---

**Q42.** A company plans to use Amazon Nova Lite for multilingual text and image processing on a tight budget. Why is Nova Lite the best choice?

A) It supports video generation | B) It is the highest-accuracy Nova model | C) It is a multimodal model with the lowest cost among Nova models | D) It requires no configuration

**Answer: C** — Nova Lite is a multimodal model supporting text and images across multiple languages at the lowest cost in the Nova family.

---

**Q43.** A company needs to generate short videos from text descriptions for product marketing. Which Amazon Nova model supports this?

A) Nova Lite | B) Nova Pro | C) Nova Canvas | D) Nova Reel

**Answer: D** — Amazon Nova Reel is the video generation model in the Nova family.

---

**Q44.** Which Amazon Nova model is purpose-built for high-quality image generation from text prompts?

A) Nova Lite | B) Nova Pro | C) Nova Canvas | D) Nova Reel

**Answer: C** — Amazon Nova Canvas is the image generation model in the Nova family.

---

**Q45.** A company runs 10,000 Bedrock invocations per day and wants consistent, low-latency responses at lower per-call costs. Which pricing model is best?

A) On-Demand | B) Spot pricing | C) Provisioned Throughput | D) Free tier

**Answer: C** — Provisioned Throughput reserves model capacity, providing consistent latency and lower per-token costs at high volumes.

---

**Q46.** A company trained a confidential model on Amazon Bedrock. They realize the model may expose pricing formulas in outputs. What must they do?

A) Enable Bedrock invocation logging | B) Use Guardrails with word filters | C) Delete and retrain the model without the confidential data | D) Use KMS encryption on model weights

**Answer: C** — If sensitive data was included in training, removing it and retraining from scratch is the only reliable solution.

---

**Q47.** A company needs to use Amazon Q Business securely. Which TWO steps are required?

A) Enable AWS KMS encryption for the Amazon Q Business index | B) Allow public access to the index | C) Configure cross-account access | D) Configure IAM for authentication | E) Disable access logging

**Answer: A, D** — KMS encryption secures data at rest; IAM authentication ensures only authorized users access the index.

---

**Q48.** A company wants to track every tool call and reasoning step its Bedrock agents take. Which logging feature is required?

A) Amazon CloudWatch container insights | B) Bedrock model invocation logging | C) AWS CloudTrail data events | D) Amazon OpenSearch access logs

**Answer: B** — Bedrock invocation logging captures detailed input/output data including agent traces and tool call steps.

---

**Q49.** A company processes audio meeting recordings into summaries. What is the correct service sequence?

A) Polly → Bedrock → S3 | B) Transcribe → Bedrock → S3 | C) Lex → Comprehend → S3 | D) Rekognition → Bedrock → S3

**Answer: B** — Transcribe converts audio to text; Bedrock summarizes the text; S3 stores files.

---

**Q50.** An insurance company wants to show which input variables most influence fraud predictions. Which SageMaker tool provides feature importance reports?

A) SageMaker Pipelines | B) SageMaker Clarify | C) SageMaker Canvas | D) SageMaker Experiments

**Answer: B** — SageMaker Clarify provides feature importance reports (via SHAP) showing how each input drives a model's prediction.

---

**Q51.** Which SageMaker feature automates and orchestrates an entire ML pipeline from preprocessing through deployment?

A) SageMaker JumpStart | B) SageMaker Canvas | C) SageMaker Pipelines | D) SageMaker Feature Store

**Answer: C** — SageMaker Pipelines is the workflow orchestration service for automating multi-step ML workflows.

---

**Q52.** What data format is required for fine-tuning a foundation model on Amazon Bedrock?

A) CSV file with tabular data | B) Unstructured .txt file | C) JSON file with labeled prompt-completion pairs | D) XML file with annotations

**Answer: C** — Bedrock fine-tuning requires a JSON file containing pairs of "prompt" and "completion" fields.

---

**Q53.** A company needs to measure the direct business impact of their Bedrock-powered shopping assistant on sales. Which metric is most relevant?

A) Model perplexity | B) Response latency | C) Conversion rate of users who purchase after AI interactions | D) Tokens per session

**Answer: C** — Conversion rate links AI interactions to actual purchase outcomes, directly quantifying business impact.

---

**Q54.** A company wants to generate product images in various artistic styles with fine control over texture and detail. Which model type is most suitable?

A) Transformer-based LLM | B) Diffusion model | C) Embedding model | D) Recurrent neural network

**Answer: B** — Diffusion models excel at stylistically controllable, high-quality image generation.

---

**Q55.** A company's RAG-based chatbot uses Bedrock Knowledge Bases. Documents are updated daily in S3. Does the model need retraining?

A) Yes, the model must be fine-tuned after each update | B) No, Knowledge Bases with RAG retrieves updated documents at inference time | C) Yes, continued pre-training is required weekly | D) No, but the endpoint must be restarted

**Answer: B** — RAG with Bedrock Knowledge Bases fetches the most current documents at inference time, no retraining needed.

---

**Q56.** A company wants to evaluate whether its model produces fair outputs across demographic groups before deploying. Which tool provides fairness metrics?

A) SageMaker Model Monitor | B) SageMaker Clarify | C) SageMaker Ground Truth | D) AWS Audit Manager

**Answer: B** — SageMaker Clarify provides pre-training and post-training bias metrics across demographic groups.

---

**Q57.** A company wants to block prompt injection attacks on user inputs before they reach the Bedrock model. Which feature handles input-level filtering?

A) Invocation logging | B) Guardrails applied to input prompts | C) Provisioned Throughput | D) Model evaluation

**Answer: B** — Bedrock Guardrails can be applied to both input prompts and outputs, filtering adversarial content before it reaches the model.

---

**Q58.** A company acquires ISO 42001 accreditation. What does this indicate?

A) All AI systems are individually certified | B) Individual developers are ISO certified | C) The organization's AI management framework meets ISO standards | D) AWS services used are ISO 42001 compliant

**Answer: C** — ISO accreditation reflects that the company's development processes and framework, not individual systems or people, meet the ISO standard.

---

**Q59.** A company needs to process scanned insurance claim PDFs into machine-readable text. Which AWS service is most appropriate?

A) Amazon Comprehend | B) Amazon Rekognition | C) Amazon Textract | D) Amazon Translate

**Answer: C** — Amazon Textract extracts printed and handwritten text, forms, and tables from scanned documents including PDFs.

---

**Q60.** A company uses SageMaker to train models on datasets that contain more examples of some classes than others. They want to measure how well the model balances detecting all classes. Which metric should they use?

A) Accuracy | B) Recall | C) Precision | D) F1 score

**Answer: D** — The F1 score is the harmonic mean of precision and recall, ideal for evaluating model performance on imbalanced class datasets.

---

### Section B — Generative AI Concepts & Prompt Engineering (Q61–Q120)

**Q61.** A developer sets temperature to 0.9 for a creative writing assistant. What effect does this have?

A) Output becomes more deterministic and focused | B) Output becomes more creative and varied | C) Output length increases significantly | D) Output latency decreases

**Answer: B** — Higher temperature increases the probability of selecting less-likely tokens, producing more diverse outputs.

---

**Q62.** A company wants to use an LLM to generate SQL queries from natural language typed by non-technical users. Which model type is most suitable?

A) WaveNet | B) Residual neural network | C) Generative pre-trained transformer (GPT) | D) Support vector machine

**Answer: C** — GPT-style transformers excel at natural language understanding and code generation including SQL.

---

**Q63.** An LLM-powered product description generator creates compelling text with incorrect product specifications. Which AI problem is this?

A) Overfitting | B) Data leakage | C) Hallucination | D) Sampling bias

**Answer: C** — Hallucination occurs when an LLM generates plausible-sounding but factually incorrect content.

---

**Q64.** A Bedrock chatbot produces different answers every time the same question is asked. Which parameter should be adjusted to minimize this?

A) Increase max tokens | B) Reduce Top-K to 1 | C) Set temperature to 0 | D) Enable streaming mode

**Answer: C** — Temperature 0 ensures the model consistently chooses the most probable next token.

---

**Q65.** A company provides 10 labeled examples of positive and negative reviews in the prompt before asking the LLM to classify a new review. Which technique is this?

A) Zero-shot prompting | B) Few-shot prompting | C) Chain-of-thought prompting | D) Directional stimulus prompting

**Answer: B** — Few-shot prompting includes labeled examples within the prompt to guide the model's behavior.

---

**Q66.** A researcher asks a model: "Think step by step: how many windows are in the Empire State Building?" Which technique is this?

A) Zero-shot prompting | B) Few-shot prompting | C) Chain-of-thought prompting | D) Retrieval-augmented prompting

**Answer: C** — Chain-of-thought prompting asks the model to reason through a problem step by step.

---

**Q67.** A company instructs its LLM: "Classify the following text as Sports, Politics, or Entertainment: [input]." No examples provided. Which technique is this?

A) Few-shot prompting | B) Zero-shot prompting | C) Chain-of-thought prompting | D) Prompt chaining

**Answer: B** — Zero-shot prompting provides only the task instruction with no examples.

---

**Q68.** An AI image generation system uses negative prompts like "no watermarks, no text overlays." What is the purpose of a negative prompt?

A) Increase image resolution | B) Reduce generation cost | C) Specify elements to exclude from the generated image | D) Define the image aspect ratio

**Answer: C** — Negative prompts tell image generation models what elements to avoid.

---

**Q69.** A company uses few-shot prompting with 15 examples per daily LLM call. Monthly costs are high. Most cost-effective optimization without losing quality?

A) Increase examples to 30 | B) Fine-tune so fewer examples are needed in the prompt | C) Increase temperature | D) Switch to Provisioned Throughput

**Answer: B** — Fine-tuning teaches the model required behavior so fewer in-prompt examples are needed, reducing token usage.

---

**Q70.** An LLM consistently produces outputs not matching the company's formal, professional tone. Most appropriate fix without retraining?

A) Reduce temperature to 0 | B) Increase max_tokens | C) Refine the system prompt to specify tone explicitly | D) Switch to a larger foundation model

**Answer: C** — Adjusting the prompt to explicitly describe desired style guides the model to match expectations.

---

**Q71.** A research company's RAG chatbot should only answer from its internal research papers and refuse when context is insufficient. Which Bedrock Guardrails feature enforces this?

A) Content filters | B) Denied topics | C) Contextual grounding check | D) PII redaction

**Answer: C** — Contextual grounding check blocks responses not supported by provided reference documents.

---

**Q72.** A developer builds an application where the LLM must call a weather API before answering. Which Bedrock Prompt Management feature enables calling external APIs?

A) Prompt variables | B) Tools configuration | C) Stop sequences | D) Special tokens

**Answer: B** — Tools configuration in Bedrock Prompt Management allows prompts to define and invoke external APIs.

---

**Q73.** A company wants LLM responses consistently under 100 words. Which parameter directly limits output length?

A) Temperature | B) Top-P | C) Max tokens | D) Top-K

**Answer: C** — The max_tokens parameter caps the number of tokens in the model's output.

---

**Q74.** An AI model trained for general purposes performs poorly on cybersecurity-specific queries lacking domain vocabulary. What technique should be applied?

A) Zero-shot prompting | B) Domain adaptation fine-tuning | C) Increasing the context window | D) Reducing temperature

**Answer: B** — Domain adaptation fine-tuning trains the model on cybersecurity terminology and context.

---

**Q75.** A company wants to customize a foundation model using 50,000 unlabeled internal documents. Which customization technique is appropriate?

A) Supervised fine-tuning | B) RLHF | C) Continued pre-training | D) RAG

**Answer: C** — Continued pre-training uses unlabeled text to further train a model without requiring labeled data.

---

**Q76.** An LLM produces different output every time the same prompt is used due to random token sampling. What is the correct term?

A) Hallucination | B) Data drift | C) Nondeterminism | D) Underfitting

**Answer: C** — Nondeterminism is the property where identical inputs produce different outputs due to sampling randomness.

---

**Q77.** A company wants its LLM to write product descriptions in a friendly casual tone mentioning key features. What is the first thing they should do?

A) Fine-tune the model on existing product descriptions | B) Adjust the prompt template with explicit style and content instructions | C) Increase temperature to maximize creativity | D) Set max tokens to 500

**Answer: B** — Refining the prompt to specify tone, style, and content is the simplest lowest-cost first step.

---

**Q78.** A company needs to generate product descriptions in French, German, Spanish, and Japanese. Which model characteristic is most critical to assess?

A) Latency | B) Multilingual support | C) Model size (parameters) | D) Image generation capability

**Answer: B** — Multilingual support is the most critical evaluation criterion for multilingual output requirements.

---

**Q79.** What is the primary purpose of embeddings in AI applications?

A) Controlling LLM output length | B) Representing text, images, or data as numerical vectors capturing semantic meaning | C) Setting model temperature values | D) Storing training labels

**Answer: B** — Embeddings convert data into dense numerical vector representations capturing semantic relationships.

---

**Q80.** A product search application needs to match sentences like "comfortable running shoes for wide feet" to product embeddings. Which database capability is needed?

A) Full-text keyword search | B) Nearest-neighbor vector search | C) Relational joins | D) OLAP analytical queries

**Answer: B** — Nearest-neighbor vector search compares query embeddings to product embeddings for semantic matches.

---

**Q81.** What does the context window size determine in an LLM?

A) How many training examples the model saw | B) The maximum tokens the model can process in a single prompt plus response | C) The model's accuracy score | D) How many API calls can be made per second

**Answer: B** — The context window is the total token capacity (prompt + response) for a single inference call.

---

**Q82.** An LLM is asked to translate text from English to Hindi with no examples provided. Which prompting technique is being applied?

A) Few-shot | B) Chain-of-thought | C) Zero-shot | D) Retrieval-augmented

**Answer: C** — Translating without examples relies on the model's pre-trained capabilities — zero-shot prompting.

---

**Q83.** A company provides three example email drafts with specific style, then asks the LLM to generate a new email in the same style. Which prompting technique?

A) Zero-shot prompting | B) Chain-of-thought prompting | C) Few-shot prompting | D) Directional stimulus prompting

**Answer: C** — Providing multiple examples before the new task is the definition of few-shot prompting.

---

**Q84.** A model is configured with Top-P = 0.9. What does this mean?

A) The model outputs at most 90 tokens | B) The model samples from the smallest token set whose cumulative probability is 90% | C) The model uses the top 90 most probable tokens | D) The model achieves 90% accuracy

**Answer: B** — Top-P (nucleus sampling) selects from the minimum set of tokens whose combined probability reaches 90%.

---

**Q85.** Which component of a RAG architecture stores vectorized document representations for similarity retrieval?

A) LLM inference endpoint | B) Vector database (e.g., OpenSearch) | C) Amazon S3 | D) AWS Lambda

**Answer: B** — The vector database stores document embeddings and supports nearest-neighbor queries for RAG.

---

**Q86.** A company wants to prevent its Bedrock chatbot from discussing competitors' products. Which guardrail type should be configured?

A) Word filters (specific competitor names) | B) Content filters (violence/hate category) | C) Denied topics (competitor-related subjects) | D) Contextual grounding check

**Answer: C** — Denied topics block entire subject areas, not just specific words.

---

**Q87.** An AI chatbot reveals detailed harmful instructions when a user asks an indirect question designed to bypass safety. Which type of attack is this?

A) Data poisoning | B) Model inversion | C) Prompt injection | D) Adversarial data drift

**Answer: C** — Prompt injection manipulates the model through crafted inputs to bypass safety constraints.

---

**Q88.** A company wants the LLM to stop generating once it produces a sentence ending with a period and newline. Which parameter controls this?

A) Max tokens | B) Stop sequence | C) Temperature | D) Top-K

**Answer: B** — Stop sequences are special tokens or strings that signal the model to halt generation when encountered.

---

**Q89.** What is the key difference between fine-tuning and RAG?

A) Fine-tuning changes model weights; RAG retrieves context at inference time without changing the model | B) RAG requires more compute than fine-tuning | C) Fine-tuning uses unlabeled data; RAG uses labeled data | D) They are interchangeable

**Answer: A** — Fine-tuning permanently adjusts model weights. RAG dynamically retrieves external documents without model weight changes.

---

**Q90.** A company finds its LLM-based contract summarizer misses key legal clauses. They have 2,000 labeled contract summaries. Which approach most likely improves performance?

A) Add more examples to the prompt | B) Supervised fine-tuning on the labeled contract summaries | C) Increase context window size | D) Reduce temperature

**Answer: B** — Supervised fine-tuning on domain-specific labeled data teaches the model which clauses are important.

---

**Q91.** A company wants to use an LLM for 50-category ticket classification with in-context examples. Which approach provides best accuracy?

A) Zero-shot with clear category descriptions | B) Chain-of-thought reasoning | C) Few-shot with at least one example per category | D) Continued pre-training

**Answer: C** — For multi-category tasks, providing examples per category (few-shot) significantly outperforms zero-shot.

---

**Q92.** A company's LLM for legal document analysis frequently makes up case citations that don't exist. Most effective architectural mitigation?

A) Increase model's max tokens | B) Implement RAG so the model cites only from provided legal corpus | C) Set temperature to 1.0 | D) Use zero-shot prompting

**Answer: B** — RAG grounds model responses in verified source documents, dramatically reducing hallucinated citations.

---

**Q93.** A generative AI image tool keeps including unwanted text overlays. Which prompt configuration removes them?

A) Positive prompt emphasizing product features | B) Higher resolution setting | C) Negative prompt specifying "no text, no watermarks" | D) Lower temperature

**Answer: C** — Negative prompts explicitly instruct image generation models to exclude specific visual elements.

---

**Q94.** What prompt component holds persistent instructions (persona, context) sent with every LLM invocation but hidden from users?

A) User prompt | B) Completion | C) System prompt | D) Stop sequence

**Answer: C** — The system prompt contains hidden instructions, persona definitions, and behavioral constraints.

---

**Q95.** Which inference parameter directly limits candidate tokens to a fixed count at each generation step?

A) Temperature | B) Top-K | C) Top-P | D) Max tokens

**Answer: B** — Top-K limits the candidate pool to the K most probable next tokens, directly controlling vocabulary diversity.

---

**Q96.** A company's LLM is configured with temperature = 0 but users find responses robotic. What parameter adjustment adds natural variety?

A) Set temperature to 2.0 | B) Set temperature to 0.3–0.5 | C) Maximize Top-K | D) Set max tokens to unlimited

**Answer: B** — Temperature in the 0.3–0.5 range adds natural variety while maintaining coherence.

---

**Q97.** A company wants an LLM to generate structured JSON output every time. Which is most effective?

A) Set temperature to 0 only | B) Explicit JSON schema instructions in system prompt + example output | C) Increase max tokens | D) Use zero-shot prompting

**Answer: B** — Explicit format instructions with examples consistently enforce structured output formats.

---

**Q98.** An LLM is asked to estimate piano tuners in Chicago. The user wants to see the reasoning process. Which technique?

A) Zero-shot prompting | B) Few-shot prompting | C) Chain-of-thought prompting | D) RAG

**Answer: C** — Chain-of-thought prompting asks the model to show each reasoning step, ideal for estimation problems.

---

**Q99.** A company has a knowledge base of 100,000 support articles. When a user asks a question, the system retrieves top 5 articles and passes them to the LLM as context. This architecture is:

A) Supervised fine-tuning | B) Retrieval-Augmented Generation (RAG) | C) Continued pre-training | D) Chain-of-thought prompting

**Answer: B** — RAG retrieves relevant documents and passes them as context to the LLM at inference time.

---

**Q100.** What is the benefit of using Amazon Bedrock's managed API over self-hosted open-source models on EC2 for a production application?

A) Lower per-token costs in all scenarios | B) No need to manage infrastructure, security patching, or model scaling | C) Full access to model weights | D) No content filtering applied

**Answer: B** — Amazon Bedrock is fully managed, eliminating infrastructure management, security, and scaling overhead.

---

**Q101.** An LLM generates marketing copy containing false claims about a competitor. Which responsible AI principle does this most directly violate?

A) Robustness | B) Veracity and truthfulness | C) Data residency | D) Model latency

**Answer: B** — Veracity is the responsible AI principle requiring that model outputs be truthful and grounded in fact.

---

**Q102.** A company builds an AI system using Amazon Bedrock that must call external APIs. Which Bedrock feature handles multi-step API orchestration?

A) Knowledge Bases | B) Guardrails | C) Agents | D) Prompt Management

**Answer: C** — Bedrock Agents orchestrate multi-step workflows and call external APIs.

---

**Q103.** A medical imaging company wants to create synthetic X-ray images for training diagnostic models without using real patient data. Which model type is most suitable?

A) Transformer-based LLM | B) BERT-based model | C) Generative Adversarial Network (GAN) | D) Decision tree

**Answer: C** — GANs are specifically designed for generating realistic synthetic data including images.

---

**Q104.** What does a model trained on tabular customer data with a binary target column ("will_churn: yes/no") represent?

A) Unsupervised clustering | B) Regression | C) Supervised binary classification | D) Reinforcement learning

**Answer: C** — A binary target column with labeled training data describes supervised binary classification.

---

**Q105.** A company wants to evaluate quality of AI-generated customer support responses by comparing to human gold-standard responses using an automated text overlap metric. Which metric is most appropriate?

A) Accuracy | B) F1 Score | C) ROUGE | D) RMSE

**Answer: C** — ROUGE measures n-gram overlap between generated and reference texts, suitable for evaluating text generation quality.

---

**Q106.** A developer wants to ensure a Bedrock chatbot never outputs the phrase "I don't know." Which Guardrails feature handles specific phrase blocking?

A) Content filters | B) Denied topics | C) Word filters | D) PII redaction

**Answer: C** — Word filters block specific words, phrases, or expressions from appearing in model outputs.

---

**Q107.** A company needs to build a product search application where a user describes what they want in natural language and receives matching products. Which combined capability is needed?

A) Textract + Comprehend | B) Bedrock embedding model + OpenSearch vector search | C) Rekognition + Lex | D) Transcribe + Polly

**Answer: B** — An embedding model converts the user query to a vector; OpenSearch performs nearest-neighbor search against product embeddings.

---

**Q108.** What is the primary reason Amazon Bedrock is preferred over building a custom ML pipeline for most generative AI use cases?

A) It always has the most advanced models | B) No infrastructure to manage — fully managed access to multiple FMs with built-in security | C) It is cheaper than all alternatives | D) It never hallucinates

**Answer: B** — Bedrock's fully managed nature eliminates the infrastructure burden and provides enterprise-grade security and compliance.

---

**Q109.** A company wants to use SageMaker to share computed features (like customer average spend) across five different ML projects. Which SageMaker feature enables this?

A) SageMaker Canvas | B) SageMaker Feature Store | C) SageMaker Ground Truth | D) SageMaker Clarify

**Answer: B** — SageMaker Feature Store is a centralized repository for sharing computed features across ML projects.

---

**Q110.** A company's Bedrock chatbot sometimes generates responses about sensitive topics it should avoid. Which component combination best prevents this?

A) Temperature = 0 + invocation logging | B) Denied topics + content filters | C) PII redaction + word filters | D) Contextual grounding + max tokens reduction

**Answer: B** — Denied topics block subject-level avoidance; content filters block unsafe content categories — together they provide broad topic and content safety.

---

**Q111.** A company processes customer feedback in 12 different languages using Amazon Comprehend. What AWS service handles translation before analysis?

A) Amazon Lex | B) Amazon Transcribe | C) Amazon Translate | D) Amazon Polly

**Answer: C** — Amazon Translate provides neural machine translation to standardize multi-language content before NLP processing.

---

**Q112.** A company's AI application needs to remember what a user said in message 3 when responding to message 15. Which Bedrock feature enables this?

A) Bedrock Knowledge Bases | B) Bedrock Guardrails | C) Bedrock Agents with conversation history | D) Bedrock Model Evaluation

**Answer: C** — Bedrock Agents maintain conversation history (memory) within a session for context-aware multi-turn interactions.

---

**Q113.** A company wants to detect when its daily Bedrock inference costs spike abnormally. Which monitoring tool should they configure?

A) SageMaker Clarify | B) AWS Budgets + CloudWatch billing alerts | C) Amazon Macie | D) AWS Config

**Answer: B** — AWS Budgets with CloudWatch billing alerts automatically notifies when spend exceeds defined thresholds.

---

**Q114.** A generative AI content platform wants human editors to review and optionally edit AI outputs before they go live. Which AWS service supports this workflow?

A) Amazon SageMaker Ground Truth | B) Amazon Augmented AI (A2I) | C) SageMaker Clarify | D) Amazon Rekognition

**Answer: B** — Amazon A2I provides built-in workflows for human review of AI prediction outputs before they are acted upon.

---

**Q115.** An e-commerce company wants to translate product listings from English into 30 languages automatically. Which AWS service handles this at scale?

A) Amazon Transcribe | B) Amazon Comprehend | C) Amazon Translate | D) Amazon Lex

**Answer: C** — Amazon Translate provides fully managed neural machine translation supporting numerous language pairs.

---

**Q116.** A company uses few-shot prompting but notices the LLM ignores the style of the examples. What prompt engineering adjustment helps?

A) Add a system prompt clarifying to follow the examples' style | B) Increase temperature | C) Reduce max tokens | D) Switch to zero-shot

**Answer: A** — A system prompt explicitly instructing the model to match the style of the examples improves adherence.

---

**Q117.** An organization's Bedrock model responds well to English prompts but produces low-quality outputs for Spanish prompts. What should they investigate first?

A) Increasing max tokens | B) Whether the selected model has strong multilingual support | C) Setting temperature to 0 for Spanish | D) Enabling invocation logging

**Answer: B** — Multilingual capability varies across models; checking and selecting a model with strong Spanish support is the first step.

---

**Q118.** A company wants to build a chatbot that extracts patient symptoms from free-text conversation and populates a structured form. Which NLP task does this require?

A) Sentiment analysis | B) Named entity recognition (NER) | C) Topic modeling | D) Text summarization

**Answer: B** — Named entity recognition identifies and extracts specific entities (symptoms, medications, dates) from free text.

---

**Q119.** A developer wants the LLM to always output JSON with specific keys. They include a JSON example in the system prompt. Which prompt engineering technique is this?

A) Zero-shot prompting | B) Output format specification via few-shot example | C) Chain-of-thought prompting | D) Temperature control

**Answer: B** — Providing a format example in the system prompt is a form of few-shot output format specification.

---

**Q120.** A company has deployed a Bedrock-based assistant. They want to measure whether the AI is reducing human agent workload. Which metric best captures this?

A) ROUGE score | B) Token consumption per session | C) Percentage of conversations resolved without human escalation (containment rate) | D) Model perplexity

**Answer: C** — Containment rate directly measures the AI's ability to resolve issues without human intervention.

---

### Section C — Machine Learning Concepts (Q121–Q180)

**Q121.** A model achieves 98% accuracy on training data but only 62% on test data. Which problem does this indicate?

A) Underfitting | B) Overfitting | C) Data leakage | D) Concept drift

**Answer: B** — A large gap between training and test performance is the hallmark of overfitting.

---

**Q122.** A company wants to cluster 5 million customers into groups based on purchasing behavior without predefined categories. Which ML paradigm?

A) Supervised learning | B) Reinforcement learning | C) Unsupervised learning | D) Semi-supervised learning

**Answer: C** — Clustering unlabeled data to discover groups is a classic unsupervised learning task.

---

**Q123.** Which algorithm is ideal for discovering customer segments based on shared purchasing and demographic characteristics?

A) Logistic regression | B) K-means clustering | C) Decision tree | D) Support vector machine

**Answer: B** — K-means clustering groups data points into K clusters based on similarity, ideal for customer segmentation.

---

**Q124.** A bank's loan approval model must be explainable to regulators. Which algorithm best balances predictive performance and interpretability?

A) Deep neural network | B) Random forest | C) Logistic regression | D) XGBoost

**Answer: C** — Logistic regression provides clear, interpretable coefficients satisfying regulatory transparency requirements.

---

**Q125.** A model evaluated on a 95%/5% imbalanced dataset predicts class A for everything and achieves 95% accuracy. Which metric better captures actual performance?

A) Accuracy | B) R-squared | C) F1 Score | D) RMSE

**Answer: C** — F1 Score balances precision and recall, exposing the model's failure to detect the minority class.

---

**Q126.** A hospital wants to detect rare diseases. Missing a positive case is far more costly than a false alarm. Which metric should be maximized?

A) Precision | B) Accuracy | C) Recall (Sensitivity) | D) Specificity

**Answer: C** — Maximizing recall minimizes false negatives, critical when missing a positive has severe consequences.

---

**Q127.** A gene classification model must document how each input feature contributes to its prediction. Which algorithm best satisfies this interpretability requirement?

A) Neural network | B) K-means | C) Decision tree | D) Autoencoder

**Answer: C** — Decision trees produce a transparent structure showing exactly how each feature and threshold contributes to decisions.

---

**Q128.** A recommendation model trained 18 months ago has gradually declining performance as user preferences shifted. What type of drift is this?

A) Data drift only | B) Concept drift | C) Sampling drift | D) Label noise

**Answer: B** — Concept drift occurs when the underlying relationship between inputs and target variable changes over time.

---

**Q129.** A fraud detection model has 1,000 fraud cases and 99,000 non-fraud cases. The model predicts "no fraud" for everything and achieves 99% accuracy. What technique improves fraud detection?

A) Reduce the number of features | B) Increase training epochs | C) Apply class rebalancing (oversampling fraud or undersampling non-fraud) | D) Switch to linear regression

**Answer: C** — Class rebalancing adjusts the training distribution so the model learns to detect the minority class.

---

**Q130.** Which evaluation metric is most appropriate for a regression model predicting house prices?

A) Accuracy | B) F1 Score | C) RMSE (Root Mean Squared Error) | D) Recall

**Answer: C** — RMSE measures average prediction error for continuous output regression tasks.

---

**Q131.** A manufacturing company wants to detect defective products using images without labeled defect categories. Which unsupervised approach works best?

A) Binary classification with labeled examples | B) Autoencoder-based anomaly detection | C) K-means clustering with predefined clusters | D) Random forest classifier

**Answer: B** — Autoencoders trained on normal images flag defective images through high reconstruction error.

---

**Q132.** A data scientist creates a correlation matrix, calculates descriptive statistics, and plots histograms for a new dataset. Which ML pipeline stage is this?

A) Feature engineering | B) Data preprocessing | C) Exploratory data analysis (EDA) | D) Hyperparameter tuning

**Answer: C** — EDA involves exploring data through statistics, visualization, and correlation analysis.

---

**Q133.** A model trained on historical loan data unfairly rejects applicants from minority groups. Which bias type caused this?

A) Observer bias | B) Sampling bias | C) Measurement bias | D) Confirmation bias

**Answer: B** — If historical training data under-represented certain groups, sampling bias was introduced.

---

**Q134.** A company has a dataset with 50 highly correlated features causing a slow, unstable model. Which preprocessing step helps?

A) Data augmentation | B) Principal Component Analysis (PCA) | C) Label encoding | D) Data balancing

**Answer: B** — PCA reduces correlated features into uncorrelated principal components, improving training speed.

---

**Q135.** A company trains a customer lifetime value model. During feature engineering, they create "average_order_value" from total spend / number of orders. Which ML step is this?

A) Data preprocessing | B) Feature engineering | C) EDA | D) Model evaluation

**Answer: B** — Feature engineering creates new informative features from raw data to improve model performance.

---

**Q136.** A company wants to train a model to play a video game by rewarding it for points and penalizing it for lost lives. Which ML paradigm?

A) Supervised learning | B) Unsupervised learning | C) Reinforcement learning | D) Transfer learning

**Answer: C** — Reinforcement learning trains agents through reward/penalty signals from their environment.

---

**Q137.** A company has a text classification model trained on English. They want to adapt it to French without training from scratch. Which technique?

A) Zero-shot prompting | B) Transfer learning with fine-tuning on French data | C) Continued pre-training on unrelated data | D) K-means clustering on French text

**Answer: B** — Transfer learning leverages an existing model's knowledge and adapts it via fine-tuning.

---

**Q138.** A company trains a classification model. The confusion matrix shows high numbers in the off-diagonal cells. What does this indicate?

A) High model accuracy | B) Many misclassifications | C) Zero false positives | D) Model is overfitting

**Answer: B** — Off-diagonal cells represent misclassifications; high numbers indicate poor performance.

---

**Q139.** A model predicts whether a customer will buy. Precision = 0.70, recall = 0.95. The company has a limited marketing budget. What adjustment is needed?

A) Optimize for higher recall | B) Optimize for higher precision (reduce false positives) | C) Switch to regression | D) Increase training data

**Answer: B** — With a limited budget, false positives (marketing to non-buyers) waste resources; higher precision ensures outreach targets likely buyers.

---

**Q140.** An autonomous driving AI needs to perform reliably in rain, fog, and night conditions underrepresented in training. Which responsible AI principle most directly addresses this?

A) Fairness | B) Robustness | C) Transparency | D) Explainability

**Answer: B** — Robustness ensures AI systems perform reliably across diverse and unexpected conditions.

---

**Q141.** A company applies L2 regularization to their neural network. What is the primary purpose?

A) Speed up training | B) Reduce overfitting by penalizing large model weights | C) Improve model interpretability | D) Handle class imbalance

**Answer: B** — L2 regularization penalizes large weights, discouraging overly complex models and reducing overfitting.

---

**Q142.** A company trains an NLP model to identify financial fraud patterns. It has precision = 0.40 and recall = 0.99. What does this mean operationally?

A) The model catches almost all fraud but flags many legitimate transactions | B) The model only catches 40% of actual fraud | C) The model has overfit | D) The model performs well on both detection and false positive control

**Answer: A** — High recall means most fraud is detected; low precision means many legitimate transactions are incorrectly flagged.

---

**Q143.** An ML pipeline ingests streaming transaction data for real-time fraud detection requiring predictions under 200ms. Which inference architecture?

A) Batch transform | B) Asynchronous inference | C) Real-time inference endpoint | D) Serverless inference

**Answer: C** — Real-time inference endpoints are optimized for low-latency synchronous predictions.

---

**Q144.** A company has 1 million unlabeled product images. They want to group visually similar products without manual labeling. Which algorithm?

A) Supervised convolutional neural network | B) K-means clustering on image embeddings | C) Random forest classifier | D) Logistic regression

**Answer: B** — K-means on image embeddings groups visually similar products without any labels.

---

**Q145.** A company trains an image segmentation model on satellite imagery with 90% urban and 10% rural coverage. The model performs poorly on rural imagery. Which bias type?

A) Confirmation bias | B) Measurement bias | C) Sampling bias | D) Observer bias

**Answer: C** — The training dataset under-represents rural areas, resulting in sampling bias.

---

**Q146.** A data science team is removing duplicates, handling missing values, and standardizing column formats. Which ML pipeline stage?

A) Model evaluation | B) Feature engineering | C) Exploratory data analysis | D) Data preprocessing

**Answer: D** — Data preprocessing involves cleaning, formatting, and preparing raw data.

---

**Q147.** A company's neural network is very accurate but takes 8 seconds to respond. Business requires sub-second latency. Which optimization reduces inference latency?

A) Fine-tuning with more data | B) Model quantization (reducing precision from 32-bit to 8-bit) | C) Increasing model depth | D) Increasing training epochs

**Answer: B** — Model quantization reduces weight precision, dramatically decreasing model size and inference time.

---

**Q148.** A company's model performance degrades each month. Model Monitor detects distribution changes in input features. What is this?

A) Overfitting | B) Model drift / data drift | C) Underfitting | D) Label noise

**Answer: B** — Data drift occurs when input feature distributions change over time, causing trained models to become less accurate.

---

**Q149.** A company trains an NLP model. During evaluation, precision = 0.88, recall = 0.88, and F1 = 0.88. This balanced result suggests:

A) Severe class imbalance | B) Appropriate balance between precision and recall | C) Model is overfitting | D) Needs more training data

**Answer: B** — Equal precision and recall with high F1 indicates well-balanced performance.

---

**Q150.** A company builds a model to classify insurance claims. After 6 months, Model Monitor reports data drift. Which SageMaker service should they use to confirm accuracy degradation?

A) SageMaker Data Wrangler | B) SageMaker Ground Truth | C) SageMaker Model Monitor | D) SageMaker Feature Store

**Answer: C** — SageMaker Model Monitor evaluates deployed models against quality baselines and reports drift metrics.

---
### Section D — Responsible AI & Governance (Q151–Q220)

**Q151.** A company uses a hiring algorithm that consistently rates female candidates lower than equally qualified male candidates. Which responsible AI principle is violated?

A) Robustness | B) Transparency | C) Fairness | D) Privacy

**Answer: C** — Fairness requires that AI systems treat individuals and groups equitably without discrimination.

---

**Q152.** A company's AI loan model denies a customer and cannot explain why. Which responsible AI principle is violated?

A) Fairness | B) Transparency / Explainability | C) Robustness | D) Privacy

**Answer: B** — Explainability requires AI systems to provide understandable reasons for decisions in high-stakes domains.

---

**Q153.** A company wants to comply with GDPR by ensuring the AI model does not output personal identifiers like names or email addresses. Which approach satisfies this?

A) Use Amazon Macie for S3 scanning | B) Enable Bedrock Guardrails with PII redaction filters | C) Increase model max tokens | D) Use CloudTrail for API logging

**Answer: B** — Bedrock Guardrails PII redaction filters automatically detect and remove personal identifiers from inputs and outputs.

---

**Q154.** An organization wants defined policies for how long data is kept and when it must be deleted. Which governance practice describes this?

A) Data de-identification | B) Data residency | C) Data retention policy | D) Model versioning

**Answer: C** — Data retention policies define how long data is stored and when it must be deleted.

---

**Q155.** A company builds an AI employment application screener. An applicant challenges the decision. The company must provide a legally compliant explanation. Which AI property is required?

A) Robustness | B) Explainability | C) Scalability | D) Availability

**Answer: B** — Many regulations (EU AI Act, GDPR) require that automated decisions affecting individuals be explainable upon request.

---

**Q156.** A generative AI model produces news article summaries that subtly favor certain political viewpoints due to biased training data. Which bias type is this?

A) Sampling bias from non-representative training data | B) Measurement bias | C) Observer bias | D) Overfitting bias

**Answer: A** — If training data over-represents politically biased sources, the model learns and replicates that bias.

---

**Q157.** A company's AI security camera disproportionately flags individuals from a specific ethnic group. Which corrective action most directly addresses this?

A) Increase model training epochs | B) Audit and rebalance training data to ensure diverse representation | C) Reduce model complexity | D) Add more cameras

**Answer: B** — Auditing for demographic imbalance and rebalancing the dataset is the most direct corrective action for sampling bias.

---

**Q158.** A company uses an AI model for medical diagnoses but does not disclose the decisions are AI-generated. Which responsible AI principle does this violate?

A) Robustness | B) Transparency | C) Fairness | D) Privacy

**Answer: B** — Transparency requires that users and stakeholders know when AI is making decisions affecting them.

---

**Q159.** A company develops an AI loan approval application. What should be the FIRST action following responsible AI principles?

A) Deploy the model and monitor for issues post-launch | B) Conduct a bias and fairness assessment of training data before model development | C) Maximize model accuracy regardless of fairness | D) Use the most complex model available

**Answer: B** — Responsible AI practices should start with assessing training data for bias before model development begins.

---

**Q160.** A company wants to ensure its clinical trials AI is robust against unexpected patient data inputs. How should robustness be tested?

A) Evaluate on standard validation sets only | B) Test with adversarial examples, edge cases, and out-of-distribution inputs | C) Maximize accuracy on training dataset | D) Deploy and wait for user complaints

**Answer: B** — Robustness testing deliberately challenges the model with unusual, adversarial, and out-of-distribution inputs.

---

**Q161.** A company labels training data for a content moderation model using 20 annotators per image. What responsible AI benefit does this provide?

A) Reduces training time | B) Reduces observer/labeler bias through consensus | C) Increases accuracy on all categories | D) Reduces storage costs

**Answer: B** — Multiple annotators reduce individual bias by using consensus or majority vote for final labels.

---

**Q162.** A bank's AI credit scoring model consistently disadvantages rural applicants. Which governance action should be taken?

A) Deploy as-is and monitor for complaints | B) Conduct a fairness audit, identify rural representation gaps, and retrain with balanced data | C) Add rural postcode as a feature | D) Switch to a simpler model

**Answer: B** — A fairness audit identifies disadvantaged groups; retraining with balanced data corrects the bias.

---

**Q163.** A company deploys an AI chatbot without informing users they are interacting with AI. Which responsible AI principle is violated?

A) Fairness | B) Robustness | C) Transparency | D) Privacy

**Answer: C** — Transparency requires that users are aware they are interacting with an AI system.

---

**Q164.** Which AWS service helps companies continuously demonstrate compliance with SOC 2, ISO 27001, and PCI DSS for AI applications?

A) AWS Artifact | B) Amazon Inspector | C) AWS Audit Manager | D) Amazon Macie

**Answer: C** — AWS Audit Manager automates evidence collection for continuous compliance against industry frameworks.

---

**Q165.** A loan default model was trained without including "race" as a feature, yet still produces racially biased predictions. What explains this?

A) The model is underfitting | B) Proxy variables correlated with race (e.g., zip code) carry the bias | C) The model has too many parameters | D) Training data was too small

**Answer: B** — Proxy variables that correlate with protected attributes can re-introduce bias even when the attribute is excluded.

---

**Q166.** A company wants to ensure no PII enters Bedrock model prompts. Which service scans and classifies PII in stored data?

A) Amazon Inspector | B) Amazon Macie | C) AWS CloudTrail | D) AWS Artifact

**Answer: B** — Amazon Macie uses ML to automatically discover and classify sensitive data including PII in Amazon S3.

---

**Q167.** A responsible AI team wants to document all known limitations, intended use cases, and evaluation metrics for a new credit scoring model. Which AWS resource?

A) SageMaker Experiments | B) SageMaker Feature Store | C) SageMaker Model Card | D) SageMaker Canvas

**Answer: C** — SageMaker Model Cards are documentation tools for capturing model details, limitations, and performance metrics.

---

**Q168.** An AI system's predictions change significantly based on small irrelevant changes to input. Which responsible AI concern does this raise?

A) Privacy | B) Fairness | C) Robustness | D) Transparency

**Answer: C** — Robustness requires AI systems to produce stable outputs when inputs change in ways that shouldn't affect the prediction.

---

**Q169.** A company wants customers to evaluate its AI product summaries for accuracy and helpfulness. Which AWS service supports human evaluation of AI outputs?

A) Amazon SageMaker Ground Truth | B) Amazon Augmented AI (A2I) | C) SageMaker Clarify | D) Amazon Rekognition

**Answer: B** — Amazon A2I integrates human review workflows into AI prediction pipelines.

---

**Q170.** A bank's AI is audited and found to consistently outperform for high-income applicants but underperform for low-income ones. Best action?

A) Add income as an explicit feature | B) Ensure training data represents all income brackets and retrain with fairness constraints | C) Deploy a separate model for low-income applicants | D) Reduce model complexity

**Answer: B** — Balanced representation and fairness-aware training is the most principled approach.

---

**Q171.** An organization wants to implement AI governance and ensure team members understand ethical responsibilities. What is the most foundational action?

A) Deploy monitoring dashboards | B) Establish an AI ethics policy and train all team members on responsible AI principles | C) Increase model accuracy thresholds | D) Implement more encryption

**Answer: B** — An AI ethics policy with training provides the foundation for all governance activities.

---

**Q172.** A company uses AI for employee performance assessments. An employee objects to a discriminatory assessment. The obligation to provide a human-understandable explanation reflects which principle?

A) Privacy | B) Robustness | C) Explainability | D) Scalability

**Answer: C** — Explainability requires that AI-driven decisions affecting people can be explained in understandable terms.

---

**Q173.** A company's AI content filter blocks 30% of legitimate user requests. What trade-off is being poorly managed?

A) Precision vs. recall | B) Safety vs. over-refusal / false positive rate | C) Latency vs. accuracy | D) Training cost vs. inference cost

**Answer: B** — The tension between content safety and over-refusal is a key responsible AI design challenge.

---

**Q174.** Which BEST describes the principle of "privacy by design" in AI systems?

A) Encrypting model outputs before storing | B) Incorporating privacy protections into AI system architecture from the beginning | C) Allowing users to opt out of data collection | D) Deleting user data after 30 days

**Answer: B** — Privacy by design means privacy considerations are embedded from the start, not added later.

---

**Q175.** A doctor always approves AI medical diagnosis recommendations without independent assessment. Which risk does this create?

A) Model drift | B) Automation bias (over-reliance on AI) | C) Data privacy breach | D) Model overfitting

**Answer: B** — Automation bias occurs when humans defer excessively to AI recommendations without independent judgment.

---

**Q176.** A company must ensure that its AI model treats applicants from different age groups equally. Which AWS tool detects age-based disparities?

A) Amazon Rekognition | B) SageMaker Model Monitor | C) SageMaker Clarify | D) Amazon Comprehend

**Answer: C** — SageMaker Clarify provides fairness metrics detecting statistical disparities across demographic groups.

---

**Q177.** A pharmaceutical company wants AI models only used by approved researchers on approved datasets. Which governance mechanism enforces this?

A) Data augmentation | B) IAM roles and resource-level policies with least privilege access | C) Model quantization | D) High temperature settings

**Answer: B** — IAM roles with least privilege ensure only authorized users can access specific models and datasets.

---

**Q178.** A company's AI for parole decisions shows racial disparities. What first step should the company take?

A) Shut down the AI system immediately | B) Conduct a disparate impact analysis and bias audit of the model and training data | C) Add more features | D) Deploy a second model to override the first

**Answer: B** — A disparate impact analysis and bias audit is the first principled step to understand the source and extent of discriminatory outcomes.

---

**Q179.** A model predicts loan defaults. Sensitive attribute "race" was excluded, yet racial bias remains. The most likely cause is:

A) Overfitting | B) Proxy variables (e.g., zip code) correlated with race | C) Too many features | D) Insufficient training data

**Answer: B** — Proxy variables correlated with protected attributes transmit bias even when the protected attribute is excluded.

---

**Q180.** A company wants to comply with EU AI Act for a high-risk AI application. Which TWO activities are required?

A) Minimize model parameters | B) Maintain comprehensive risk and technical documentation | C) Conduct regular human oversight and monitoring | D) Use only open-source models | E) Maximize training dataset size

**Answer: B, C** — The EU AI Act requires high-risk AI systems to have comprehensive documentation and ongoing human oversight.

---

**Q181.** A company wants to ensure that generated images for its platform can be traced back to the AI system that created them. Which responsible AI mechanism addresses this?

A) PII redaction | B) AI content watermarking or provenance tracking | C) Content filter for violence | D) Contextual grounding check

**Answer: B** — AI content watermarking or provenance tracking allows tracing the origin of generated content, helping combat misinformation.

---

**Q182.** An AI practitioner builds a customer support bot that escalates to a human when AI confidence is below a threshold. Which responsible AI principle does this implement?

A) Fairness | B) Privacy | C) Human oversight and controllability | D) Transparency

**Answer: C** — Human oversight ensures AI systems have clear escalation paths for uncertain or high-stakes situations.

---

**Q183.** A company's AI recommendation system maximizes engagement, inadvertently amplifying polarizing content. Which responsible AI principle is compromised?

A) Privacy | B) Transparency | C) Safety and societal impact | D) Robustness

**Answer: C** — Safety and societal impact requires AI systems to consider broader social consequences, not just immediate optimization metrics.

---

**Q184.** A company deployed an AI credit scoring model. By June, its Gini coefficient declined from 0.85 to 0.65 for a specific demographic. What does this indicate?

A) The model has become more fair | B) The model's discriminative performance degraded for that demographic | C) The model has improved overall | D) No significant change

**Answer: B** — A declining Gini coefficient indicates reduced model discriminative performance, which may signal demographic-specific model drift or growing unfairness.

---

**Q185.** A company wants to use customer interaction logs from S3 to improve its chatbot. What is the compliant approach?

A) Continuously fine-tune with raw logs including PII | B) Anonymize/de-identify logs, obtain consent, then use sanitized data for periodic fine-tuning | C) Use raw logs directly | D) Share logs with the LLM provider

**Answer: B** — Responsible use of customer data requires de-identification, consent, and privacy compliance before training.

---

**Q186.** A company's AI content generation system must not reproduce copyrighted material. Which responsible AI mechanism prevents this?

A) Increasing temperature | B) Training data curation to exclude copyrighted materials + output monitoring | C) Setting max tokens low | D) Using RAG only

**Answer: B** — Preventing copyright violations requires both upstream (training data curation) and downstream (output monitoring) controls.

---

**Q187.** A company uses AI to generate job postings. The system consistently uses gendered language despite no explicit gender instructions. Most likely cause?

A) Underfitting | B) Gendered language patterns learned from biased training data | C) Overfitting to training data format | D) High temperature setting

**Answer: B** — If the training corpus contained predominantly gendered language, the model learned and reproduces those patterns.

---

**Q188.** A company built a document Q&A system using RAG. Users report the system returns the same document chunks regardless of their question. What is the likely problem?

A) Temperature is too low | B) The embedding model is not capturing query semantics well | C) LLM context window is too large | D) Guardrails are too restrictive

**Answer: B** — If the same documents are always retrieved, the embedding model is failing to distinguish different query semantics.

---

**Q189.** A company is concerned about its neural network credit approval model being a "black box." They want feature contribution scores per decision. Which technique provides this?

A) Confusion matrix analysis | B) Cross-validation | C) SHAP (SHapley Additive exPlanations) values | D) PCA

**Answer: C** — SHAP values provide per-prediction feature attribution showing how each input influenced the specific decision.

---

**Q190.** A company wants to prevent its Bedrock financial advice AI from generating content implying guaranteed investment returns (both inaccurate and potentially illegal). Which Bedrock feature blocks this?

A) Word filters for specific financial terms | B) Denied topics covering guaranteed investment advice | C) Content filters for violence | D) Contextual grounding check

**Answer: B** — Denied topics prevent the subject of guaranteed investment returns from being generated.

---

**Q191.** A company builds an AI system making medical diagnoses. Regulators ask them to demonstrate bias testing across genders, ages, and ethnicities before deployment. Which document records this?

A) SageMaker Pipelines execution log | B) Model Card with bias evaluation results | C) AWS CloudTrail API log | D) Amazon S3 data lake metadata

**Answer: B** — Model Cards are the standard documentation artifact for recording pre-deployment bias evaluations.

---

**Q192.** A company's NLP model for resume screening is significantly less likely to recommend female candidates for engineering roles. Which action has the most lasting impact?

A) Increase temperature to introduce randomness | B) Add gender as an explicit feature | C) Audit and rebalance training data, retrain with fairness constraints, and implement ongoing monitoring | D) Reduce model complexity

**Answer: C** — Comprehensive bias remediation requires fixing the data, retraining with fairness constraints, and continuous monitoring.

---

**Q193.** An AI system for content recommendations risks creating "filter bubbles" where users only see confirming content. Which responsible AI principle is being addressed?

A) Privacy | B) Diversity, fairness, and non-manipulation | C) Explainability | D) Robustness

**Answer: B** — Avoiding filter bubbles is related to fairness, non-manipulation, and ensuring diverse content exposure.

---

**Q194.** A company has deployed a multi-modal AI system. A user submits a competitor's product image and asks the AI to compare it unfavorably. Which Bedrock combination blocks this?

A) Denied topics (competitor comparisons) + content filters (misleading content) | B) Word filters + PII redaction | C) Contextual grounding + invocation logging | D) Temperature = 0 + max tokens reduction

**Answer: A** — Denied topics prevents competitor comparisons; content filters block false comparative claims.

---

**Q195.** A company's AI generates marketing emails with false health claims. Which compliance action is most critical?

A) Reduce max tokens | B) Implement denied topics for health claims + human review before sending | C) Switch to zero-shot prompting | D) Use batch transform

**Answer: B** — Denying health claim topics prevents generation; human review provides a final compliance check.

---

**Q196.** A company discovers their LLM can be prompted to reveal information about specific individuals from training data. What privacy attack is this?

A) Model evasion | B) Data poisoning | C) Membership inference attack | D) Prompt injection

**Answer: C** — Membership inference attacks exploit a model's tendency to memorize training data, allowing inference about specific individuals.

---

**Q197.** A company's AI generates personalized content. Users complain AI decisions feel arbitrary. Which design change best addresses this?

A) Increase temperature for more variety | B) Implement an explanation feature showing top reasons for each recommendation | C) Switch to batch inference | D) Reduce model size

**Answer: B** — Providing explanations for AI recommendations satisfies the transparency and explainability principles of responsible AI.

---

**Q198.** A company uses Amazon Bedrock Guardrails for content safety. After deployment, users complain about legitimate requests being blocked. What is the likely issue?

A) Temperature too high | B) Over-aggressive guardrail settings causing false positives | C) Insufficient Provisioned Throughput | D) Wrong model selected

**Answer: B** — Over-aggressive guardrails block legitimate requests (over-refusal), requiring tuning to balance safety and utility.

---

**Q199.** A company uses SageMaker to deploy a healthcare diagnostic model. They want to ensure the model does not discriminate between insured and uninsured patients. Which tool to use?

A) SageMaker Feature Store | B) SageMaker Clarify with group fairness metrics | C) SageMaker Canvas | D) SageMaker JumpStart

**Answer: B** — SageMaker Clarify provides group fairness metrics to detect and measure discrimination across defined groups.

---

**Q200.** Which practice BEST prevents sensitive customer data from being embedded into a fine-tuned Bedrock model?

A) Encrypt all customer data with KMS | B) Remove PII from training data before fine-tuning, using de-identification techniques | C) Use AWS CloudTrail to monitor data access | D) Enable invocation logging

**Answer: B** — Removing PII from training data before fine-tuning is the most direct way to prevent sensitive data from being memorized in model weights.

---

**Q201.** A company's RAG-based assistant provides incorrect answers despite retrieving relevant documents. Where is the failure in the RAG pipeline?

A) Embedding model quality | B) Vector database configuration | C) LLM generation step (not the retrieval) | D) Query preprocessing

**Answer: C** — If retrieval is working (relevant documents found) but answers are wrong, the problem lies in the LLM's generation — it may be hallucinating despite correct context.

---

**Q202.** A company wants to implement conversational AI that remembers context from earlier in a session. Which Bedrock feature provides session-level memory?

A) Bedrock Knowledge Bases | B) Bedrock Agents with conversation history | C) Bedrock Guardrails | D) Bedrock Model Evaluation

**Answer: B** — Bedrock Agents maintain conversation history within a session for context-aware multi-turn interactions.

---

**Q203.** A company discovers its Bedrock API calls traverse the public internet. What configuration change prevents this?

A) Enable Bedrock Guardrails | B) Configure a VPC endpoint (PrivateLink) for Amazon Bedrock | C) Enable invocation logging | D) Switch to On-Demand pricing

**Answer: B** — A VPC endpoint using AWS PrivateLink routes Bedrock API traffic through the private AWS network.

---

**Q204.** A company uses Amazon Bedrock for a customer-facing app. They want to track every model input/output for compliance auditing. Which action is needed?

A) Enable AWS CloudTrail for all API calls | B) Configure Amazon Inspector | C) Enable Bedrock invocation logging | D) Set up Amazon EventBridge

**Answer: C** — Bedrock invocation logging must be explicitly enabled to capture model input/output data.

---

**Q205.** A company provides Amazon Bedrock access to 5,000 engineers. They want to control which teams use which models and track usage per team. Which features achieve this?

A) One shared API key + invocation logging | B) IAM roles per team with model-specific permissions + CloudTrail logging | C) Multiple AWS accounts + Route 53 | D) Bedrock Guardrails + KMS

**Answer: B** — IAM roles enforce access control; CloudTrail logs API calls per IAM identity enabling per-team tracking.

---

**Q206.** A company's Bedrock model for customer service must respond professionally without slang. Most targeted configuration approach?

A) Set temperature to 0 | B) Add explicit style and tone guidelines to the system prompt | C) Enable Guardrails word filters for slang terms | D) Fine-tune the model on formal responses

**Answer: B** — The system prompt with explicit tone guidelines is the quickest, most flexible way to enforce professional language.

---

**Q207.** A company's LLM application costs $200/month. After fine-tuning, they reduce few-shot examples from 20 to 5 per call. Cost drops to $80/month. What produced this saving?

A) Prompt compression | B) Fine-tuning reducing prompt length requirements | C) Switching to On-Demand pricing | D) Using batch transform

**Answer: B** — Fine-tuning teaches task-specific behavior, reducing the need for lengthy few-shot examples and directly lowering token costs.

---

**Q208.** A company generates 10,000 AI images daily for marketing. They need automated moderation of each generated image. Which service integrates into the workflow?

A) Amazon SageMaker Model Monitor | B) Amazon Rekognition Content Moderation | C) Amazon Macie | D) AWS CloudTrail

**Answer: B** — Amazon Rekognition Content Moderation API automatically analyzes images for inappropriate content at scale.

---

**Q209.** An AI company wants to estimate environmental impact before training a large custom model on EC2 GPU instances. Which instance type minimizes carbon footprint for ML training?

A) P5 (NVIDIA H100) | B) G5 (NVIDIA A10G) | C) Trn1 (AWS Trainium) | D) C6i (Intel Ice Lake)

**Answer: C** — AWS Trainium (Trn1) instances are purpose-built for ML training with the best performance-per-watt energy efficiency.

---

**Q210.** A company wants AI governance frameworks in place so developers understand ethical responsibilities. What is the MOST foundational first step?

A) Deploy monitoring dashboards immediately | B) Establish an AI ethics policy and conduct responsible AI training for all team members | C) Maximize all model accuracy metrics | D) Implement encryption on all data

**Answer: B** — An AI ethics policy with team training is the foundation that all other governance activities build upon.

---

### Section E — Mixed Advanced Scenarios (Q211–Q300)

**Q211.** A company builds an app where customers upload a photo of damaged car and receive an instant repair estimate. Which AWS service combination?

A) Amazon Transcribe + Amazon Comprehend | B) Amazon Rekognition + Amazon Bedrock | C) Amazon Textract + Amazon Lex | D) Amazon Polly + Amazon Translate

**Answer: B** — Rekognition analyzes the damage image; Bedrock uses detected damage details to generate a cost estimate.

---

**Q212.** A company uses BERT to fill missing words in product descriptions where database errors introduced gaps. Why is BERT appropriate?

A) BERT generates images from text | B) BERT uses bidirectional context (left and right of the missing word) to predict fill-ins | C) BERT is optimized for regression | D) BERT provides real-time streaming

**Answer: B** — BERT's bidirectional training allows it to use context from both sides of a masked token for fill-in tasks.

---

**Q213.** A company has high-frequency stock trading data updated every millisecond. They need anomaly detection for unusual patterns in real time. Best ML approach?

A) Batch transform with weekly model updates | B) Real-time inference with streaming anomaly detection | C) Zero-shot LLM prompting | D) K-means clustering on historical data

**Answer: B** — Real-time inference with streaming data analysis enables millisecond-level anomaly detection.

---

**Q214.** A user asks an LLM about Federal Reserve interest rate changes. The LLM was trained in 2023. Best architectural solution for current information?

A) Increase max tokens | B) Fine-tune the model monthly | C) Implement RAG with a real-time news API as retrieval source | D) Use chain-of-thought prompting

**Answer: C** — RAG with a real-time API allows the LLM to access current information without model retraining.

---

**Q215.** A company needs to provide "Why was I denied?" explanations to loan applicants. Which combination of tools enables this?

A) Amazon Comprehend + AWS CloudTrail | B) SageMaker Clarify (SHAP) + SageMaker Model Cards | C) SageMaker Canvas + Amazon Rekognition | D) Amazon Bedrock Guardrails + Amazon Macie

**Answer: B** — Clarify provides SHAP feature attribution for the decision; Model Cards document the model's behavior for stakeholder communication.

---

**Q216.** A company's chatbot is configured with Top-K = 5. What does this mean for output generation?

A) The model generates 5 complete responses and picks the best | B) At each step, only the 5 most probable tokens are considered for sampling | C) The model limits responses to 5 sentences | D) The model processes only 5 input tokens

**Answer: B** — Top-K = 5 means only the 5 highest-probability tokens are considered at each generation step.

---

**Q217.** A retail AI shopping assistant must never discuss political topics AND must log all customer interactions. Which TWO Bedrock configurations are required?

A) Denied topics (political content) + invocation logging enabled | B) Content filters (violence) + Provisioned Throughput | C) RAG with news API + Bedrock Agents | D) Word filters + SageMaker Model Monitor

**Answer: A** — Denied topics blocks political content; invocation logging captures all interaction data for review.

---

**Q218.** A company discovers its LLM outputs contain PII from training data even without user prompting. What is this security risk?

A) Prompt injection | B) Hallucination | C) Training data memorization / data leakage | D) Concept drift

**Answer: C** — LLMs can memorize and reproduce sensitive information from training data — a privacy risk called training data memorization.

---

**Q219.** Two models for binary fraud classification: Model A has AUC-ROC = 0.92, Model B has AUC-ROC = 0.74. Which is better?

A) Model B, because it is simpler | B) Model A, because higher AUC-ROC indicates better discrimination | C) They are equivalent | D) Model B, because lower AUC means more conservative predictions

**Answer: B** — Higher AUC-ROC (closer to 1.0) indicates better ability to distinguish between positive and negative classes.

---

**Q220.** A company has two models: Model A uses logistic regression (interpretable), Model B uses deep neural network (+2% accuracy). Which should a regulated healthcare company choose for clinical diagnosis?

A) Model B — higher accuracy is paramount | B) Model A — interpretability and regulatory compliance outweigh marginal accuracy gain | C) Both deployed simultaneously | D) Neither without fine-tuning

**Answer: B** — In regulated healthcare, explainability and regulatory compliance often outweigh small accuracy improvements.

---

**Q221.** A company's employee onboarding chatbot gives incorrect answers about the updated parental leave policy. Most efficient fix?

A) Fine-tune the LLM with the new policy | B) Update knowledge base documents in Bedrock Knowledge Base; RAG retrieves updated content automatically | C) Retrain from scratch | D) Add policy details in system prompt

**Answer: B** — Updating source documents in the Bedrock Knowledge Base causes RAG to retrieve current information at query time.

---

**Q222.** A company builds an AI system that recommends social media content. The algorithm maximizes engagement, inadvertently amplifying polarizing content. Which responsible AI principle is compromised?

A) Privacy | B) Transparency | C) Safety and societal impact | D) Robustness

**Answer: C** — Safety and societal impact principles require considering broader social consequences, not just optimization metrics.

---

**Q223.** A company wants to evaluate which foundation model produces the most factually accurate summaries for financial documents. Most reliable comparison approach?

A) Compare ROUGE scores on generic benchmark | B) Use human finance professionals to evaluate summaries with custom financial prompts | C) Choose the model with lowest latency | D) Select the model with most parameters

**Answer: B** — Domain-specific human evaluation by finance professionals using custom prompts provides the most reliable factual accuracy assessment.

---

**Q224.** A company wants to reduce their Bedrock inference costs by 40%. Which TWO tactics are most effective?

A) Fine-tune to reduce prompt length + choose a smaller model appropriate for the task | B) Increase temperature + increase max tokens | C) Enable Guardrails + use Provisioned Throughput | D) Switch to batch transform + add more few-shot examples

**Answer: A** — Fine-tuning reduces few-shot example needs (fewer input tokens); a smaller capable model reduces per-token costs.

---

**Q225.** A company needs to classify incoming insurance claims into 15 categories. They have 10,000 labeled examples per category. Which approach produces the best accuracy?

A) Zero-shot classification with an LLM | B) Few-shot classification with 5 examples per category | C) Supervised fine-tuning of a pre-trained text classification model | D) K-means clustering

**Answer: C** — With 150,000 labeled examples, supervised fine-tuning fully leverages the data to maximize classification accuracy.

---

**Q226.** A company processes customer returns data. Returns spike every holiday season. The model was trained on 3 years of uniform data and underestimates holiday returns. Best training strategy?

A) Remove holiday data as outliers | B) Ensure training data includes sufficient representation of holiday period data | C) Increase model complexity | D) Use batch transform instead of real-time inference

**Answer: B** — Including adequate holiday patterns in training data allows the model to learn seasonal return behavior.

---

**Q227.** A company wants to implement risk-based AI governance, classifying AI systems by risk level before applying controls. Which framework guides this?

A) NIST AI Risk Management Framework | B) AWS Well-Architected Framework | C) OWASP Top 10 | D) ISO 9001

**Answer: A** — The NIST AI RMF provides a structured approach to identifying, assessing, and managing AI risks including risk-tiered governance.

---

**Q228.** A company's LLM application generates different-quality responses for different departments. Which approach identifies which department-specific topics cause degradation?

A) Random sampling of all outputs | B) Segment evaluation metrics by department topic category | C) Increase temperature for all departments | D) Switch to zero-shot prompting

**Answer: B** — Segmenting evaluation metrics by topic category isolates which specific subjects the model handles poorly.

---

**Q229.** A company's Bedrock model processes multi-page contracts and users hit token limit errors. Best solution?

A) Reduce temperature | B) Select a model with larger context window or implement document chunking with RAG | C) Increase max tokens beyond the model's limit | D) Switch to batch transform

**Answer: B** — A larger context window model or chunking + RAG (splitting document into segments) handles large documents within token limits.

---

**Q230.** A company's RAG pipeline retrieves irrelevant documents when users ask ambiguous questions. Which architecture improvement helps most?

A) Increase LLM temperature | B) Improve query expansion and reranking in the retrieval pipeline | C) Reduce retrieved documents to 1 | D) Switch from OpenSearch to DynamoDB

**Answer: B** — Query expansion and reranking are the primary techniques for improving RAG retrieval quality for ambiguous queries.

---

**Q231.** A company builds an AI-powered legal assistant with RAG. They want the assistant to cite exact source documents for every answer. Which prompt engineering approach enables reliable citation?

A) Zero-shot with citation request | B) System prompt instructing the model to always cite retrieved document titles + include source metadata in retrieved chunks | C) Increase temperature for citation variety | D) Use chain-of-thought without explicit citation instruction

**Answer: B** — Explicit system prompt instructions plus source metadata in retrieved chunks enable reliable, traceable citations.

---

**Q232.** A company's SageMaker Batch Transform job is processing 2 TB of data weekly. They want to automatically retrain the model when accuracy drops below 85%. Which combination achieves this?

A) CloudWatch + Lambda to trigger SageMaker training job when metric threshold is breached | B) CloudTrail + Macie | C) S3 lifecycle policies + Rekognition | D) GuardDuty + Inspector

**Answer: A** — CloudWatch monitors the accuracy metric; Lambda triggers a SageMaker training job automatically when the threshold is breached.

---

**Q233.** A company wants to automatically generate alt-text descriptions for product images to improve accessibility. Which combination achieves this?

A) Amazon Textract + Amazon Comprehend | B) Amazon Rekognition (label detection) + Amazon Bedrock (text generation) | C) Amazon Transcribe + Amazon Polly | D) Amazon Translate + Amazon Lex

**Answer: B** — Rekognition detects image labels; Bedrock generates natural-language alt-text descriptions from those labels.

---

**Q234.** A company's AI assistant for financial decisions must not take autonomous actions without human approval. Which design pattern enforces this?

A) Autonomous agent with no oversight | B) Human-in-the-loop with AI recommendations requiring human approval before execution | C) Batch inference without monitoring | D) High temperature for creative decision-making

**Answer: B** — Human-in-the-loop requires human approval before AI recommendations are executed in high-stakes scenarios.

---

**Q235.** A company wants to use SageMaker to track hyperparameters, metrics, and artifacts across multiple training runs. Which SageMaker service manages this?

A) SageMaker Feature Store | B) SageMaker Experiments | C) SageMaker Canvas | D) SageMaker Ground Truth

**Answer: B** — SageMaker Experiments tracks and compares ML experiments, recording hyperparameters, metrics, and artifacts.

---

**Q236.** A company's Bedrock Knowledge Base assistant sometimes cites the wrong document. They want the model to acknowledge when context is insufficient. Which technique helps?

A) Increase temperature | B) Add system prompt instructions to indicate uncertainty when context is insufficient | C) Reduce number of documents retrieved | D) Enable invocation logging

**Answer: B** — System prompt instructions explicitly telling the model to acknowledge insufficient context calibrate responses.

---

**Q237.** A company wants to allow its legal team to query 50,000 internal contracts using natural language. Most operationally efficient approach?

A) Build a custom BERT-based model | B) Use Amazon Kendra with document ingestion | C) Fine-tune an LLM on contract summaries | D) Use SageMaker Canvas

**Answer: B** — Amazon Kendra is purpose-built for intelligent enterprise document search with minimal configuration.

---

**Q238.** An AI application receives an image + a text question about the image ("What's wrong with this photo of my order?"). Which model capability is required?

A) Text-only transformer | B) Multi-modal model accepting both text and image inputs | C) Image generation model | D) Embedding-only model

**Answer: B** — A multi-modal model processes both text and image inputs simultaneously.

---

**Q239.** A company uses Bedrock Agents to handle customer orders. They want to track every tool call and reasoning step. Which logging feature to enable?

A) Amazon CloudWatch container insights | B) Bedrock model invocation logging | C) AWS CloudTrail data events | D) Amazon OpenSearch access logs

**Answer: B** — Bedrock invocation logging captures detailed input/output data including agent traces and tool call steps.

---

**Q240.** A company uses a foundation model for customer service. Responses sometimes are not grounded in provided support documentation. Which technique ensures all responses are traceable to source documents?

A) Increase in-context examples | B) Implement RAG with source citation in the prompt template | C) Use higher temperature | D) Reduce retrieval k value to 1

**Answer: B** — RAG with source citation instructions grounds all responses in retrieved documents and makes sources traceable.

---

**Q241.** A company's Bedrock chatbot occasionally reveals information from its system prompt when users ask "What are your instructions?" Which defense prevents this?

A) Setting temperature to 0 | B) Including explicit instructions in the system prompt to never reveal internal instructions | C) Using few-shot examples | D) Reducing max tokens

**Answer: B** — Explicitly instructing the model via system prompt to refuse revealing its internal configuration is the standard defense.

---

**Q242.** A company wants to build a model predicting customer subscription conversion. They have 2M rows of behavioral data (clicks, session duration, pages visited) with a binary label. Which combination of steps leads to the best model?

A) EDA → feature engineering → logistic regression | B) EDA → feature engineering → gradient boosting (e.g., XGBoost) with hyperparameter tuning | C) Direct clustering without labels | D) Fine-tune an LLM on the behavioral data

**Answer: B** — For large tabular binary classification with rich features, gradient boosting with hyperparameter tuning typically achieves the best performance.

---

**Q243.** A company builds a multi-modal AI application processing medical scans (images) and clinical notes (text) simultaneously. Which Amazon Bedrock model capability is required?

A) Text-only LLM with high max_tokens | B) Multi-modal model accepting both image and text inputs | C) Image generation model | D) Embedding-only model

**Answer: B** — Simultaneous processing of image and text requires a multi-modal model.

---

**Q244.** A company runs weekly SageMaker Batch Transform jobs for churn prediction. The model was trained 8 months ago. Model Monitor reports feature distribution shifts. Primary risk?

A) Inference latency will increase | B) Model will produce increasingly inaccurate predictions due to data drift | C) S3 storage costs will increase | D) IAM permissions will expire

**Answer: B** — Data drift means the model is applied to data with different characteristics than training, degrading prediction quality.

---

**Q245.** A company wants to compare total cost of ownership between self-hosting an open source LLM on EC2 vs. Amazon Bedrock for a low-volume workload. What makes Bedrock more cost-effective?

A) Bedrock has lower per-token costs at all scales | B) EC2 has 24/7 fixed costs even when idle; Bedrock charges only for tokens used | C) Bedrock provides free fine-tuning | D) EC2 cannot run LLMs

**Answer: B** — For low-volume workloads, Bedrock's pay-per-token pricing avoids paying for always-on GPU instances that sit idle.

---

**Q246.** A company wants to build a Q&A bot over product manuals updated quarterly. Most maintainable architecture?

A) Fine-tune the LLM quarterly | B) RAG with the product manual in Bedrock Knowledge Bases (re-index when manual changes) | C) Hard-code answers in system prompt | D) Continued pre-training quarterly

**Answer: B** — RAG with Knowledge Bases requires only re-indexing the updated manual document — no model retraining needed.

---

**Q247.** An AI-based security system must detect threats in real time with under 50ms latency on live video from 1,000 cameras. Which infrastructure is appropriate?

A) Batch transform on S3 stored video | B) Real-time inference endpoints with GPU acceleration | C) Serverless inference | D) Asynchronous inference

**Answer: B** — Real-time GPU-accelerated inference provides the sub-50ms latency required for live video threat detection.

---

**Q248.** A company's generative AI marketing copy pipeline must comply with copyright law and not reproduce protected material. Which mechanism prevents this?

A) Increasing temperature | B) Training data curation excluding copyrighted materials + output monitoring/filtering | C) Setting max tokens low | D) Using RAG only

**Answer: B** — Preventing copyright violations requires both upstream (training data curation) and downstream (output monitoring) controls.

---

**Q249.** A manufacturing company wants real-time quality defect detection on a high-speed assembly line using computer vision. Which combination achieves this?

A) Amazon Textract + batch processing | B) Amazon Rekognition Custom Labels + real-time inference | C) Amazon Comprehend + SageMaker Canvas | D) Amazon Lex + Amazon Polly

**Answer: B** — Rekognition Custom Labels trains a model on defect images; real-time inference enables millisecond detection on the assembly line.

---

**Q250.** A company wants to generate product descriptions in a very specific format: exactly 3 sentences, always mentioning price and material. Which parameter combination best enforces this?

A) High temperature, high max_tokens | B) Low temperature + explicit format instructions in prompt + stop sequence after third sentence | C) Zero Top-K, unlimited max_tokens | D) Increase batch size

**Answer: B** — Low temperature ensures consistency; explicit format instructions enforce structure; stop sequence terminates after the third sentence.

---

**Q251.** A company trains a document classification model. They achieve excellent cross-validation results but poor performance on real-world data. Likely cause?

A) Underfitting | B) Data leakage between training and validation sets | C) Overfitting | D) High variance in labels

**Answer: B** — Data leakage (e.g., future data included in training) causes artificially inflated validation scores that don't hold in production.

---

**Q252.** A company wants to build a prototype AI app with no AWS infrastructure setup. Which service requires the least setup?

A) SageMaker Studio notebooks | B) Amazon Bedrock PartyRock | C) EC2 GPU instances | D) AWS Lambda with Bedrock SDK

**Answer: B** — PartyRock is a web-based playground requiring no AWS account for basic experimentation — the lowest-friction entry point.

---

**Q253.** A company uses ML to predict equipment failure 24 hours in advance from sensor readings every 5 minutes. Which task type?

A) Binary classification (fail/no fail within 24h) on time series features | B) Clustering | C) Named entity recognition | D) Dimensionality reduction

**Answer: A** — Predicting whether failure will occur within a time window using time series features is binary classification.

---

**Q254.** A company has a model with precision = 0.85 and recall = 0.60 for detecting high-value customers. What does this indicate?

A) The model misses 40% of actual high-value customers and 15% of positive predictions are incorrect | B) The model has 85% overall accuracy | C) The model has zero false negatives | D) The model is underfitting

**Answer: A** — Recall 0.60 means 40% of high-value customers are missed; precision 0.85 means 15% of predictions are false positives.

---

**Q255.** A company wants to detect when its daily Bedrock inference token consumption increases by more than 20% compared to the daily average. Which tool provides this monitoring?

A) SageMaker Clarify | B) Amazon CloudWatch with custom metric alerts | C) AWS CloudTrail | D) Amazon Macie

**Answer: B** — CloudWatch can monitor custom metrics (token consumption) and trigger alerts when defined thresholds are exceeded.

---

**Q256.** A company has a healthcare AI that makes predictions with 99% specificity but only 70% sensitivity. What does this mean clinically?

A) The model correctly identifies 99% of patients who need attention | B) The model misses 30% of patients who actually need immediate attention | C) The model has 99% overall accuracy | D) The model has zero false positives

**Answer: B** — Sensitivity (recall) of 70% means 30% of patients who need attention are missed — clinically dangerous.

---

**Q257.** A company deploys Bedrock in a financial context. Users occasionally try to extract information about the model's internal system prompt. Which defense applies?

A) Reduce max tokens | B) Explicit system prompt instruction to never reveal internal configuration + input validation | C) Increase temperature | D) Disable invocation logging

**Answer: B** — Explicit system prompt instructions to resist override attempts plus input validation are the primary defenses against prompt injection.

---

**Q258.** A company wants to measure the 6-month business impact of their Bedrock-powered feature on customer loyalty. Which metric should they track?

A) ROUGE score of AI responses | B) Token consumption per user | C) Customer retention rate compared to pre-deployment baseline | D) Model inference latency

**Answer: C** — Retention rate compared to a pre-deployment baseline directly measures the business impact on customer loyalty.

---

**Q259.** A company is evaluating whether to use Amazon Bedrock or self-host an open-source LLM on SageMaker for a new AI project. Which factor most strongly favors Bedrock?

A) Full control over model weights | B) Lowest possible per-token cost at all scales | C) No infrastructure management, faster time-to-market, built-in security | D) Ability to use custom training data without restrictions

**Answer: C** — Bedrock's managed infrastructure, built-in security, and multiple FM access enable faster time-to-market without self-management overhead.

---

**Q260.** A company processes 800 MB documents through a Bedrock model. Processing takes 45 minutes per document. Results don't need to be instant. Which SageMaker inference type?

A) Real-time inference | B) Serverless inference | C) Asynchronous inference | D) Batch transform

**Answer: C** — Asynchronous inference handles payloads up to 1 GB with processing times up to 1 hour.

---

**Q261.** A company's NLP model was trained on English formal text but performs poorly on informal social media slang. Root cause?

A) Overfitting to formal language patterns causing poor generalization to slang | B) Model underfitting | C) Measurement bias in labels | D) Concept drift

**Answer: A** — The model overfit to formal language, failing to generalize to different text distributions.

---

**Q262.** A company builds a real-time fraud detection API. The model was trained on transaction data from 2021. It is now 2026. The fraud patterns have evolved significantly. What is required?

A) Increase API timeout | B) Retrain the model with recent fraud pattern data | C) Add more API endpoints | D) Increase model max tokens

**Answer: B** — Retraining with recent data is required when fraud patterns have evolved, causing concept drift in the production model.

---

**Q263.** A company wants to provide personalized product recommendations AND send personalized marketing emails. Which AWS services respectively handle each task?

A) Amazon Personalize (recommendations) + Amazon SES with Bedrock-generated content (emails) | B) Amazon Kendra (recommendations) + Amazon Transcribe (emails) | C) Amazon Lex (recommendations) + Amazon Polly (emails) | D) Amazon Comprehend (recommendations) + Amazon Rekognition (emails)

**Answer: A** — Amazon Personalize handles recommendations; Amazon SES with Bedrock-generated personalized content handles marketing emails.

---

**Q264.** A company trains a model to classify 100 animal species. They only have 50 images per species. Which technique produces the best results?

A) Training a full CNN from scratch | B) Transfer learning: fine-tuning a pre-trained image classification model | C) Clustering images with k-means | D) Using logistic regression on raw pixels

**Answer: B** — Transfer learning reuses a pre-trained model's feature extraction, requiring far less data than training from scratch.

---

**Q265.** A company wants to use SageMaker Canvas to build a demand forecasting model. After building, how do they integrate predictions into their ERP system?

A) Export the Canvas model to SageMaker Endpoints for API-based predictions | B) Retrain in SageMaker Studio | C) Manually run predictions and export to CSV | D) Move the model to Amazon Redshift

**Answer: A** — SageMaker Canvas models can be deployed as SageMaker endpoints, exposing them as REST APIs callable by the ERP system.

---

**Q266.** A company's customer service AI achieves high ROUGE and BLEU scores on automated evaluation, but customers report it is unhelpful. What does this suggest?

A) The automated metrics perfectly predict customer satisfaction | B) Automated text-overlap metrics don't fully capture helpfulness; human evaluation should supplement automated metrics | C) The model is overfitting | D) The temperature is too low

**Answer: B** — Automated metrics like ROUGE and BLEU measure text similarity, not perceived helpfulness — human evaluation is needed for user satisfaction assessment.

---

**Q267.** A company built a conversational AI. The model answers "What is the capital of France?" with "Paris" and then answers "What about Germany?" with "Berlin." What AI capability enables this context tracking?

A) Retrieval-augmented generation | B) Multi-turn conversation history (context window memory) | C) Chain-of-thought reasoning | D) Fine-tuning on geography data

**Answer: B** — Multi-turn conversation history allows the model to understand "What about Germany?" as referring to the capital question from earlier.

---

**Q268.** A company wants to dynamically inject {customer_name} and {account_balance} into a reusable Bedrock prompt at invocation time. Which feature enables this?

A) Tools configuration | B) Prompt variables | C) Stop sequences | D) Special tokens

**Answer: B** — Prompt variables (using {placeholder} syntax) allow dynamic injection of context-specific values into reusable prompt templates.

---

**Q269.** A company's employees use a Bedrock-powered Q&A bot. Some employees from Department A can see answers based on Department B's confidential documents. What architecture change prevents this?

A) Create separate Bedrock Knowledge Bases per department with IAM-restricted access | B) Use a single knowledge base with higher temperature | C) Implement word filters for department names | D) Increase the retrieval k value

**Answer: A** — Separate knowledge bases with IAM-enforced access controls ensure each department only retrieves from authorized documents.

---

**Q270.** A company needs to process IoT sensor data at 1-second intervals to detect chemical plant anomalies without labeled anomaly data. Most appropriate approach?

A) Supervised binary classification | B) K-means clustering with anomaly scoring | C) LSTM autoencoder for anomaly detection | D) Random forest classifier

**Answer: C** — LSTM autoencoders learn temporal normal patterns in time-series data; high reconstruction error signals anomalous behavior without labels.

---

**Q271.** A company deploys Bedrock for internal use and discovers employees enter competitive intelligence queries, potentially exposing sensitive business information. Which capability detects this?

A) Amazon Inspector | B) Bedrock invocation logging to S3 + monitoring/alerting for sensitive terms | C) Amazon Macie on S3 training data | D) SageMaker Model Monitor

**Answer: B** — Bedrock invocation logging captures all user inputs; monitoring logs for sensitive terms detects inappropriate queries.

---

**Q272.** A company stores feature computations (customer average spend, days since purchase) shared across 5 different ML projects to avoid redundant computation. Which SageMaker feature?

A) SageMaker Canvas | B) SageMaker Feature Store | C) SageMaker Ground Truth | D) SageMaker Clarify

**Answer: B** — SageMaker Feature Store allows teams to share, discover, and reuse computed features across multiple ML projects.

---

**Q273.** A company generates synthetic product profiles for testing ML models without real customer PII. Which model type is designed for synthetic structured data generation?

A) Transformer LLM | B) Generative Adversarial Network (GAN) | C) BERT | D) Decision tree

**Answer: B** — GANs are specifically designed for generating synthetic data that statistically resembles real-world distributions.

---

**Q274.** A company's AI generates job postings. They want to ensure postings use gender-neutral language. Quickest configuration approach?

A) Fine-tune the model on gender-neutral postings | B) Add explicit instruction in system prompt to use gender-neutral language and avoid gendered pronouns | C) Use word filters for specific pronouns | D) Increase temperature for more variety

**Answer: B** — A system prompt instruction explicitly requiring gender-neutral language is the quickest and most flexible approach.

---

**Q275.** A company processes weekly reports using an LLM. The reports are 50,000 words each — exceeding the model's context window. Best solution?

A) Select a model with 100K token context window | B) Implement document chunking + RAG to process relevant sections | C) Summarize the report first using another model | D) Both A and B are valid depending on requirements

**Answer: D** — Both selecting a larger context window model AND chunking + RAG are valid solutions; the best choice depends on whether the full document or selective retrieval is needed.

---

**Q276.** A company uses Amazon Bedrock to power a legal document assistant. The assistant sometimes provides incorrect legal interpretations despite relevant documents being retrieved. Which is most likely?

A) The embedding model is failing | B) The retrieved documents are irrelevant | C) The LLM is hallucinating interpretations even with correct context | D) The vector database is corrupted

**Answer: C** — If retrieval is working but interpretations are wrong, the LLM is generating incorrect reasoning despite having the right source material.

---

**Q277.** A company has a model that predicts whether a customer will subscribe. Precision = 0.70, recall = 0.95. With limited marketing budget, what adjustment is needed?

A) Optimize for higher recall | B) Optimize for higher precision to reduce false positives (wasted outreach) | C) Switch to regression | D) Increase training data

**Answer: B** — High recall but low precision wastes budget on non-converters; higher precision focuses spend on likely subscribers.

---

**Q278.** A company builds an AI system for parole recommendations. The system must be able to describe in plain language why it recommends or denies parole. Which model property is critical?

A) High accuracy | B) Low latency | C) Interpretability / explainability | D) Scalability

**Answer: C** — In decisions affecting human freedom, interpretability is non-negotiable for legal, ethical, and regulatory compliance.

---

**Q279.** A company uses Amazon Bedrock for content generation. They observe that costs tripled last month. They need to diagnose whether the increase came from longer prompts or higher volume. Which metrics to analyze?

A) Tokens per invocation (input + output) AND invocation count | B) Model latency and RMSE | C) F1 score and precision | D) ROUGE score and BLEU score

**Answer: A** — Since Bedrock costs are token-driven, tracking tokens per invocation alongside invocation count isolates whether cost growth comes from longer prompts or higher volume.

---

**Q280.** A company wants to use SageMaker for an ML pipeline that includes data preprocessing, model training, evaluation, and deployment — all automated. Which SageMaker feature?

A) SageMaker JumpStart | B) SageMaker Canvas | C) SageMaker Pipelines | D) SageMaker Feature Store

**Answer: C** — SageMaker Pipelines is the workflow orchestration service for automating multi-step ML pipelines.

---

**Q281.** A company's fraud detection model flags 5% of legitimate transactions as fraudulent (false positive rate). Business analysts spend 2 hours reviewing each false positive. Which metric directly measures the operational cost of this?

A) Recall | B) AUC-ROC | C) False positive rate (1 - specificity) | D) F1 score

**Answer: C** — False positive rate directly measures how often legitimate transactions are incorrectly flagged, driving analyst review workload.

---

**Q282.** A company trains a recommendation model but discovers it over-recommends popular items, ignoring niche products. Likely data issue?

A) Underfitting | B) Class imbalance — popular items have far more training examples | C) Data drift | D) Label noise

**Answer: B** — Class imbalance in training data (many examples for popular items, few for niche) causes the model to bias toward majority examples.

---

**Q283.** A company wants to fine-tune an open-source LLM using their proprietary dataset with minimum operational overhead. Which service is best?

A) Create a custom training job in PartyRock | B) Use Amazon SageMaker JumpStart | C) Use a custom script on SageMaker AI | D) Create a Jupyter notebook on EC2

**Answer: B** — SageMaker JumpStart provides pre-built, validated training configurations for fine-tuning open-source models with minimal setup.

---

**Q284.** A company's AI system processes insurance claims. Over time, claim descriptions have changed in vocabulary and style. The model performance has declined. What type of drift is this?

A) Sampling bias | B) Concept drift | C) Data/covariate drift | D) Label noise

**Answer: C** — When input feature distributions change (claim descriptions evolve in vocabulary) while the underlying relationship remains stable, it's data/covariate drift.

---

**Q285.** A company wants its AI assistant to ONLY answer from their internal knowledge base and explicitly say "I don't have information on this" for out-of-scope questions. Which TWO components achieve this?

A) Bedrock Knowledge Bases (RAG) for grounded answers + contextual grounding guardrail to block ungrounded responses | B) Content filters + word filters | C) Provisioned Throughput + invocation logging | D) PII redaction + denied topics

**Answer: A** — Knowledge Bases (RAG) retrieves relevant answers; the contextual grounding guardrail ensures responses not supported by the knowledge base are blocked.

---

**Q286.** A company's AI image generator produces copyrighted artistic styles when prompted with specific artist names. Which responsible AI concern?

A) Privacy | B) Intellectual property rights and copyright | C) Accuracy | D) Robustness

**Answer: B** — Reproducing a specific artist's recognizable style may constitute copyright or intellectual property violations.

---

**Q287.** A medical company trains a classification model. During evaluation, precision = 0.75, recall = 0.92, F1 = 0.83. What is the correct interpretation?

A) The model catches 92% of positive cases but some predictions are false positives (25% of positive predictions are wrong) | B) The model has 75% accuracy | C) The model is overfitting | D) The model misses 25% of positive cases

**Answer: A** — Recall 0.92 means 92% of positives are caught; precision 0.75 means 25% of positive predictions are false positives.

---

**Q288.** A company uses AI to generate product recommendation letters. The model sometimes includes incorrect customer details from hallucination. Best architecture fix?

A) Set temperature to 1.0 | B) Use a template-based prompt with verified customer data explicitly injected as variables | C) Use zero-shot prompting | D) Increase max tokens

**Answer: B** — Injecting verified customer data as explicit template variables ensures factual accuracy and prevents hallucinated details.

---

**Q289.** A company wants to evaluate multiple foundation models for a customer support chatbot, scoring them on accuracy, relevance, tone, and hallucination rates. Which service provides this?

A) Amazon SageMaker Canvas | B) Amazon Bedrock model evaluation | C) Amazon Rekognition | D) AWS Audit Manager

**Answer: B** — Bedrock model evaluation offers structured scoring including accuracy, coherence, safety, and hallucination detection for comparing LLMs.

---

**Q290.** A company's AI assistant sometimes generates offensive content despite content filters being enabled. They want the most comprehensive protection. Which approach?

A) Increase temperature to reduce repetition | B) Layer guardrails: content filters + denied topics + word filters, and test with red-teaming | C) Only use word filters | D) Set max tokens to 50

**Answer: B** — Layering multiple guardrail types with adversarial red-teaming provides the most comprehensive content protection.

---

**Q291.** A company uses a SageMaker model for real-time inventory optimization. The model predictions are used by 20 downstream systems. Which monitoring approach is most comprehensive?

A) Monitor only the SageMaker endpoint metrics | B) Monitor endpoint metrics + data quality + model quality + bias drift using SageMaker Model Monitor | C) Manually review predictions weekly | D) Only monitor error rates in downstream systems

**Answer: B** — SageMaker Model Monitor provides comprehensive monitoring: endpoint health, data quality, model performance, and bias drift.

---

**Q292.** A company wants to add personality and context to every LLM call without including them in user-visible messages. What prompt component holds persistent behavioral instructions?

A) User prompt | B) Completion | C) System prompt | D) Stop sequence

**Answer: C** — The system prompt contains persistent instructions prepended to every conversation, hidden from users.

---

**Q293.** A company's AI generates thousands of unique product titles daily. Which type of model is most operationally efficient for this at scale?

A) Transformer-based LLM with batch inference | B) K-means clustering model | C) Autoencoder | D) Support vector machine

**Answer: A** — Transformer-based LLMs with batch inference process large volumes of text generation tasks efficiently at scale.

---

**Q294.** A company wants to detect abnormal patterns in IoT sensor data without labeled anomaly examples. Which ML approach?

A) Supervised binary classification | B) Autoencoder-based anomaly detection | C) Random forest | D) Linear regression

**Answer: B** — Autoencoders learn normal patterns unsupervised; deviations produce high reconstruction error, flagging anomalies.

---

**Q295.** A company uses Amazon Bedrock and wants to know how much each individual input feature contributed to a specific model prediction. Which tool provides this?

A) Amazon CloudWatch | B) SageMaker Model Monitor | C) SageMaker Clarify with SHAP values | D) Amazon Textract

**Answer: C** — SageMaker Clarify with SHAP values provides per-prediction feature attribution for individual decisions.

---

**Q296.** A company wants to build a text summarization model. They have 10,000 articles with human-written summaries. Which approach produces the best summarization quality?

A) Zero-shot summarization with a pre-trained LLM | B) Few-shot with 5 examples per call | C) Supervised fine-tuning of a pre-trained LLM on the 10,000 article-summary pairs | D) K-means clustering of articles

**Answer: C** — With 10,000 labeled article-summary pairs, supervised fine-tuning directly teaches the model to summarize in the desired style.

---

**Q297.** A company's Bedrock AI assistant mentions a competitor's product in a positive light. Which Guardrails configuration prevents this?

A) Content filter for violence | B) Denied topics for competitor mentions | C) Word filter for the company's own brand name | D) PII redaction

**Answer: B** — Denied topics configured with competitor-related subjects prevents the model from generating content about competitors.

---

**Q298.** A company's SageMaker model predicts customer churn. They want to identify which customers are most likely to respond positively to a retention discount (high churn risk but price-sensitive). Which ML concept describes targeting this group?

A) Anomaly detection | B) Uplift modeling / treatment effect targeting | C) Time series forecasting | D) Named entity recognition

**Answer: B** — Uplift modeling identifies individuals who will respond positively to a treatment (discount), combining churn risk with price sensitivity.

---

**Q299.** A company has a Bedrock-powered assistant that must handle both English and Spanish queries. They test it and find Spanish query quality is significantly lower. What is the most likely fix?

A) Increase temperature for Spanish queries | B) Select a model with stronger multilingual support or add few-shot Spanish examples in system prompt | C) Reduce max tokens for Spanish queries | D) Use word filters for Spanish terms

**Answer: B** — Selecting a model with stronger multilingual support or providing Spanish examples improves multilingual quality.

---

**Q300.** A company wants to implement end-to-end responsible AI governance for a new foundation model deployment. Which is the MOST comprehensive approach?

A) Deploy, monitor, and fix issues reactively | B) Pre-deployment: bias audit + Model Card + safety testing. During deployment: Guardrails + invocation logging + Model Monitor. Post-deployment: periodic fairness audits + human review + continuous monitoring. | C) Enable content filters only | D) Use the most accurate model and trust it implicitly

**Answer: B** — Comprehensive responsible AI governance covers the full lifecycle: pre-deployment assessment, deployment safeguards, and ongoing post-deployment monitoring and auditing.

---

## Quick Reference Summary

### Top 10 "Always Remember" Rules

1. **Inference costs** = driven by **number of tokens** (input + output)
2. **Custom Bedrock models** require **Provisioned Throughput** before use
3. **CloudTrail** = API audit log | **Bedrock invocation logging** = model I/O log
4. **Overfitting** = great training, poor test | **Underfitting** = poor on both
5. **RAG** = no retraining, retrieves at inference | **Fine-tuning** = updates model weights
6. **Temperature = 0** = deterministic | **Temperature > 1** = high creativity/randomness
7. **F1 Score** = best metric for imbalanced classification problems
8. **ROUGE** = text summarization quality | **BLEU** = translation quality
9. **SageMaker Clarify** = bias detection + SHAP explainability
10. **Bedrock Denied Topics** = block subjects | **Word Filters** = block specific terms

### Exam Day Tips

- For "LEAST effort / operational overhead" → choose the most managed AWS service
- For "private connectivity" → always choose **AWS PrivateLink**
- For "content safety on LLM" → default to **Bedrock Guardrails**
- For "audit trail of who did what" → **AWS CloudTrail**
- For "no-code ML" → **SageMaker Canvas**
- For "document text extraction" → **Amazon Textract**
- For "speech to text" → **Amazon Transcribe** | "text to speech" → **Amazon Polly**
- For "recommendations" → **Amazon Personalize**
- For "enterprise search" → **Amazon Kendra**
- When a model "performs well on training but poorly on new data" → **overfitting**
- When a model "generates plausible but incorrect information" → **hallucination**
- When "same input produces different outputs" → **nondeterminism**
- For "human review of AI outputs" → **Amazon A2I**
- For "bias detection + explainability" → **SageMaker Clarify**
- For "compliance reports/certifications" → **AWS Artifact**

---

*Good luck on your AWS Certified AI Practitioner (AIF-C01) exam!*

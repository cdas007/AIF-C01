# 🎓 AWS Certified AI Practitioner (AIF-C01) — 15-Day Study Roadmap

> **Goal:** Pass the AIF-C01 exam in 15 days, studying **3 focused hours/day (45 hours total)**.
> **Format reminder:** ~85 questions, multiple choice & multi-response/hotspot, 90 minutes, scaled score 100–1000, passing ≈ 700.
> **Source material:** This roadmap is built directly from your uploaded `AIF-C01-Study-Guide.md` (300 practice Qs + cheat sheets) and the VCE practice exam PDF. Keep both open alongside this guide.

---

## How to Use This Guide

Each day follows the same 3-hour rhythm so your brain builds a habit:

| Block | Time | Activity |
|---|---|---|
| 🧠 Block 1 | 60 min | **Learn** — read concept explanations + deep insights below |
| 🛠️ Block 2 | 60 min | **Apply** — work through the cheat-sheet tables, map services to scenarios out loud |
| 📝 Block 3 | 60 min | **Test** — do the day's quiz from the 300-question bank (cited by Q-number), grade yourself, log weak spots |

**Rule of thumb for exam day logic:** AIF-C01 questions are scenario-based. The skill you're training isn't memorization — it's *pattern matching*: "this scenario screams PrivateLink," "this scenario screams Guardrails." Every quiz below is chosen to drill that reflex.

Keep a **"Mistake Log"** — one running note of every question you got wrong and *why*. Day 14–15 review is built entirely from this log.

---

## 📅 The 15-Day Roadmap at a Glance

| Day | Domain Focus | Topic | Weight |
|---|---|---|---|
| 1 | D1 | AI/ML/DL foundations, data types | 20% |
| 2 | D1 | Supervised / Unsupervised / Reinforcement learning, algorithms | 20% |
| 3 | D1 | ML pipeline stages, evaluation metrics | 20% |
| 4 | D2 | Foundation models, tokens, embeddings, context windows | 24% |
| 5 | D2 | Prompt engineering, inference parameters | 24% |
| 6 | D2 | RAG, model customization spectrum | 24% |
| 7 | D2 | Gen AI lifecycle, hallucination/bias/nondeterminism + **Mini Review** | 24% |
| 8 | D3 | Amazon Bedrock deep dive | 28% |
| 9 | D3 | Amazon SageMaker deep dive | 28% |
| 10 | D3 | AWS pre-built AI services (Comprehend, Textract, Rekognition, etc.) | 28% |
| 11 | D4 | Responsible AI pillars, bias types, Clarify, Guardrails | 14% |
| 12 | D4 | Governance & regulatory concepts | 14% |
| 13 | D5 | Security, Compliance & Governance services | 14% |
| 14 | All | **Full timed practice exam #1** + review | — |
| 15 | All | **Full timed practice exam #2** + final cram + exam-day strategy | — |

---

## DAY 1 — Foundations of AI, ML, and Deep Learning
**Domain 1 (20%)**

### 🧠 Concept Explanation
AI is the umbrella; ML is a subset of AI where systems learn patterns from data rather than following hard-coded rules; Deep Learning is a subset of ML using multi-layer neural networks. Think nested circles: **AI ⊃ ML ⊃ Deep Learning**.

Data types you must recognize on sight:
- **Tabular** — rows/columns (spreadsheets, CSVs) → classic ML
- **Text** — NLP, tokens, embeddings
- **Image/Video** — CNNs, Rekognition
- **Audio** — Transcribe/Polly
- **Time series** — forecasting, sequential dependence

### 💡 Deep Insight
The exam loves to test whether you can tell **AI vs ML vs Deep Learning** apart using a scenario, not a definition. If the scenario mentions "neural network with many layers," "image recognition," or "transformer" → Deep Learning. If it says "the system improves by learning from historical data" generically → ML. If it just says "machine behaves intelligently" with no learning mechanic implied → broader AI.

Also memorize: **GANs** = generate synthetic data (two networks competing); **Transformers** = the backbone of modern LLMs (self-attention mechanism, NOT sequential like RNNs — this is *why* they parallelize and scale).

### 🛠️ Apply
Walk through this table out loud, service-to-scenario style (you'll use this skill all 15 days):

| Data Type | Example Use Case | Likely AWS Tool |
|---|---|---|
| Tabular | Customer churn prediction | SageMaker |
| Text | Sentiment of reviews | Comprehend |
| Image | Damage detection in photos | Rekognition |
| Audio | Call center transcription | Transcribe |
| Time series | Demand forecasting | Forecast / SageMaker |

### 📝 Quiz (Day 1)
Use the study guide — Section A & relevant foundational Qs. Try these without peeking, then check answers in your guide:
1. What distinguishes Deep Learning from traditional ML? *(layered neural networks learning hierarchical features)*
2. What are GANs primarily used for? *(generating synthetic/realistic data via generator-discriminator competition)*
3. Why are transformers preferred over RNNs for language modeling? *(parallel processing via self-attention instead of sequential token-by-token processing)*
4. Classify: predicting house prices from square footage, location, age → which ML category? *(supervised regression)*
5. Classify: grouping customers into unlabeled segments → which ML category? *(unsupervised clustering)*

**Mistake Log reminder:** note anything you got wrong before moving on.

---

## DAY 2 — Supervised, Unsupervised & Reinforcement Learning
**Domain 1 (20%)**

### 🧠 Concept Explanation
- **Supervised** = labeled data, known outputs. Sub-types: binary classification, multi-class classification, regression. Algorithms: logistic regression, decision trees, SVM, neural networks.
- **Unsupervised** = unlabeled data, find structure. Sub-types: clustering (k-means), dimensionality reduction (PCA), anomaly detection (autoencoders), topic modeling.
- **Reinforcement Learning (RL)** = agent learns via rewards/penalties through trial and error. Used in robotics, game-playing, and **RLHF** (Reinforcement Learning from Human Feedback) — the exact technique behind aligning chatbots like Claude/ChatGPT.

### 💡 Deep Insight
The exam frequently disguises the learning type inside a business story. Anchor phrase mapping:
- "no labeled data," "find hidden patterns," "segment customers" → **Unsupervised**
- "predict a number," "predict a category," "we have historical outcomes" → **Supervised**
- "agent," "reward," "trial and error," "game," "optimize a policy over time" → **Reinforcement Learning**
- "detect abnormal patterns with no labeled anomalies" → **Autoencoder-based anomaly detection** (a specific unsupervised technique, not just generic "unsupervised")

A subtle trap: **uplift modeling** (targeting customers who'll respond positively to a treatment, like a discount) sounds like classification but is its own concept — combines prediction with causal reasoning about *response to an action*.

### 🛠️ Apply
Drill this decision tree mentally:
```
Is there a labeled outcome?
 ├─ Yes → Supervised
 │     ├─ Predicting a category → Classification
 │     └─ Predicting a number → Regression
 └─ No → 
       ├─ Is there a reward signal over time? → Reinforcement Learning
       └─ No reward signal → Unsupervised (clustering/anomaly/dim. reduction)
```

### 📝 Quiz (Day 2)
From the practice bank, drill questions involving: churn prediction, customer segmentation, anomaly detection in IoT data (Q294 style), uplift modeling (Q298 style), RLHF concepts. Self-test:
1. A company has labeled spam/not-spam emails. What ML category and sub-type? *(supervised, binary classification)*
2. A company detects abnormal IoT sensor readings with no labeled anomaly examples. *(unsupervised — autoencoder-based anomaly detection)*
3. What technique aligns chatbot behavior to human preferences through reward signals? *(RLHF)*
4. Why is k-means unsupervised? *(no labels — it discovers groupings from distance/similarity alone)*
5. Identifying price-sensitive, high-churn-risk customers to target with discounts is called? *(uplift modeling / treatment effect targeting)*

---

## DAY 3 — The ML Pipeline & Evaluation Metrics
**Domain 1 (20%)**

### 🧠 Concept Explanation
**Pipeline stages:** define business goal → data collection → preprocessing → EDA → feature engineering → training → evaluation → deployment → monitoring.

**Metrics — match the metric to the job:**

| Metric | Used For |
|---|---|
| Accuracy | Classification, balanced classes |
| F1 Score | Classification, **imbalanced** classes |
| Precision | Minimize false positives |
| Recall | Minimize false negatives |
| RMSE/MSE | Regression |
| R² | Regression fit |
| ROUGE | Summarization quality |
| BLEU | Translation quality |
| AUC-ROC | Binary classifier performance |

**Overfitting** = great on training, poor on test (model memorized noise). Fix: more data, regularization, dropout, simplify model.
**Underfitting** = poor on both. Fix: more complex model, more features, more training.

### 💡 Deep Insight
This is one of the highest-yield memorization blocks on the exam because it's tested with near-identical scenario wording every time. Internalize this single sentence: **"Precision protects against false alarms; Recall protects against missed cases."** A fraud-detection system that absolutely cannot miss fraud → optimize **recall**. A spam filter where false positives (blocking real email) are unacceptable → optimize **precision**.

Q287 in your guide is the canonical example: precision=0.75, recall=0.92 → 92% of actual positives caught, but 25% of *predicted* positives are wrong. Don't confuse the denominators — this single confusion is the #1 trap on metric questions.

### 🛠️ Apply
Say out loud, for each metric, one real scenario where it's the *correct* choice and one where it's a *trap answer*. This forces active recall instead of passive recognition.

### 📝 Quiz (Day 3)
1. Medical diagnostic model has high recall but lower precision — what does that mean practically? *(catches almost all sick patients, but generates some false alarms)*
2. Dataset is 99% non-fraud / 1% fraud. Why is accuracy a poor metric here? *(a model predicting "no fraud" always would score 99% accuracy while being useless — imbalance distorts accuracy)*
3. Which metric evaluates summarization output quality? *(ROUGE)*
4. Model scores 98% on training data, 60% on test data — diagnosis and two fixes? *(overfitting; more data / regularization / reduce complexity)*
5. Which stage comes right after data preprocessing in the standard pipeline? *(Exploratory Data Analysis)*

---

## DAY 4 — Generative AI Foundations: FMs, Tokens, Embeddings, Context Windows
**Domain 2 (24%)**

### 🧠 Concept Explanation
- **Foundation Model (FM)**: large model pre-trained on broad data, adaptable to many downstream tasks.
- **LLM**: a foundation model specialized in/applied to text.
- **Token**: the basic billing + processing unit (word/subword/character) — **inference cost scales with tokens, input + output combined.**
- **Embedding**: numeric vector capturing semantic meaning — the foundation of search/RAG/similarity.
- **Context window**: max tokens a model can "see" in one call — long documents that exceed it must be chunked.

### 💡 Deep Insight
A frequent exam trap is making you think latency, cost, or quality is driven by something exotic — it's almost always **tokens**. If a question describes ballooning Bedrock bills, the answer involves reducing **token volume** (shorter prompts, summarized context, smaller max_tokens) — not "switch regions" or "use a bigger instance."

Also internalize: embeddings aren't unique to generative AI — they're the bridge between *traditional ML similarity search* and *modern RAG*. The same concept (vector representation) powers Personalize-style recommendation, semantic search, and RAG retrieval.

### 🛠️ Apply
Map vocabulary to a real conversation with an LLM:
```
[System prompt - hidden instructions]
[User prompt - tokens counted]
   ↓ embedded + processed within context window ↓
[Completion - tokens counted, billed]
```

### 📝 Quiz (Day 4)
1. What determines Amazon Bedrock invocation cost? *(number of tokens consumed — input + output)*
2. What's the difference between a foundation model and an LLM? *(LLM is a text-specialized type of FM; FM is the broader category, can be multimodal)*
3. A document is too long to fit in one prompt — what's the underlying limitation? *(context window size)*
4. What does an embedding represent? *(a vector capturing semantic meaning, enabling similarity comparison)*
5. Q292-style: Where do you put persistent behavioral instructions hidden from the end user? *(system prompt)*

---

## DAY 5 — Prompt Engineering & Inference Parameters
**Domain 2 (24%)**

### 🧠 Concept Explanation
**Prompting techniques:**
- Zero-shot — no examples given
- Few-shot — a handful of examples to steer format/style
- Chain-of-thought — ask the model to reason step by step before answering

**Inference parameters:**

| Parameter | Effect |
|---|---|
| Temperature | Randomness/creativity; **0 = deterministic** |
| Top-K | Limits the candidate token pool by count |
| Top-P (nucleus) | Limits candidate pool by cumulative probability mass |
| Max tokens | Caps output length |

### 💡 Deep Insight
Exam scenarios test whether you know **which lever to pull**. "Model gives different answers each time we ask the same question, and we need consistency" → set **temperature to 0**, not "use a different model." "Output is being cut off mid-sentence" → increase **max tokens**, not "switch to a bigger model." Don't overthink these — they're usually a direct 1:1 parameter mapping disguised in a sentence of business fluff.

A subtler trap from your guide (Q288): hallucinated customer details in generated letters. The fix is *not* a parameter tweak — it's **architecture**: inject verified data via template variables instead of letting the model "remember" facts. This teaches the broader exam pattern: **if the problem is factual accuracy, look beyond parameters to architecture (RAG, templates, grounding) — parameters control style, not truth.**

### 🛠️ Apply
For each of these symptoms, say the fix out loud:
- Repetitive/boring output → increase temperature
- Need exact same output every run → temperature = 0
- Need the model to show its reasoning → chain-of-thought prompting
- Output cut off too early → increase max tokens
- Model needs to learn a brand-new output format from a couple examples → few-shot prompting

### 📝 Quiz (Day 5)
1. What does setting temperature to 0 guarantee (practically)? *(deterministic, repeatable output)*
2. Asking the model to "think step by step" before giving a final answer is which technique? *(chain-of-thought prompting)*
3. A model invents incorrect customer info in generated letters — best fix? *(inject verified data via template variables, not a parameter change)*
4. What's the difference between Top-K and Top-P? *(Top-K limits by token count; Top-P limits by cumulative probability mass)*
5. Few-shot prompting is most useful when? *(you need to demonstrate a specific format/style with limited examples, without fine-tuning)*

---

## DAY 6 — RAG & the Model Customization Spectrum
**Domain 2 (24%)**

### 🧠 Concept Explanation
**Effort order, least → most:**
1. Prompt engineering (zero cost, no data)
2. **RAG** — retrieves relevant docs at inference time, no retraining, uses vector DB + embeddings
3. **Fine-tuning** — needs labeled data, updates model weights
4. **Continued pre-training** — unlabeled domain data, large-scale, most expensive

RAG architecture: query → embed → retrieve from vector store (e.g., OpenSearch) → augment prompt with retrieved context → generate grounded answer.

### 💡 Deep Insight
The single most exam-tested judgment call in Domain 2: **"the model needs up-to-date or proprietary knowledge it wasn't trained on" → RAG, not fine-tuning.** Fine-tuning teaches *behavior/style*, RAG supplies *facts*. If the scenario says "always reflect the latest product catalog" → RAG (facts change constantly, retraining each time is wasteful). If it says "the model should always respond in our brand's tone/format" → fine-tuning (a stable behavioral pattern).

From your guide, Q296: 10,000 article/summary pairs available → **supervised fine-tuning**, because you have labeled input-output pairs specifically teaching a *task pattern* (how to summarize), not just facts to recall.

### 🛠️ Apply
Sort these scenarios into RAG vs Fine-tuning vs Continued pre-training vs Prompt engineering:
- "Make answers cite our latest internal wiki" → RAG
- "Make the model consistently respond in legal disclaimers format" with labeled examples → Fine-tuning
- "Teach the model an entirely new domain language (e.g., a foreign legal corpus) with no labels" → Continued pre-training
- "Improve answers with no new data at all" → Prompt engineering

### 📝 Quiz (Day 6)
1. Why choose RAG over fine-tuning for frequently changing data? *(no retraining needed — retrieval happens at inference time)*
2. What vector store is repeatedly referenced for Bedrock Knowledge Bases / RAG? *(Amazon OpenSearch Service)*
3. With 10,000 labeled article-summary pairs, what's the best approach to specialize a model? *(supervised fine-tuning)*
4. Rank model customization options from least to most effort. *(prompt engineering → RAG → fine-tuning → continued pre-training)*
5. What does "grounding" mean in a RAG context? *(connecting model outputs to verified retrieved source documents)*

---

## DAY 7 — Gen AI Lifecycle, Risks & ✅ Mini Review
**Domain 2 (24%)**

### 🧠 Concept Explanation
**Gen AI lifecycle:** data selection → model selection → fine-tuning (optional) → evaluation → deployment → monitoring.

**Core risk vocabulary:**
- **Hallucination** — plausible but false output
- **Nondeterminism** — same input, different output across calls
- **Bias** — systematic skew from data/labeling/training
- Model evaluation (Bedrock) scores models on accuracy, coherence, safety, hallucination rate when comparing candidates (Q289).

### 💡 Deep Insight
Mid-course checkpoint: by now you should be able to **instantly classify any AIF-C01 scenario into one of three buckets** — (1) a *concept* question (ML theory, metrics), (2) a *Gen AI mechanics* question (tokens/RAG/fine-tuning/parameters), or (3) a *service-mapping* question (which AWS tool). Days 8–13 are entirely service-mapping; the speed you build this week determines your exam pace.

### 🛠️ Apply — Mini Review Quiz (15 mixed questions, Domains 1 & 2)
Pull 15 random questions from Sections covering Domain 1/2 topics in your 300-question bank (tokens, RAG, metrics, ML types, bias terminology). Time yourself: **15 minutes**. Target: 12/15 or better before moving to Domain 3. If below that, spend an extra hour tonight revisiting your Mistake Log from Days 1–6 instead of starting Day 8.

### 📝 Self-Check
- Can you explain, without notes, the difference between fine-tuning and continued pre-training?
- Can you name all 4 inference parameters and their effect from memory?
- Can you state the ML pipeline stages in order?

If "no" to any — that's tonight's extra 20 minutes, not tomorrow's problem.

---

## DAY 8 — Amazon Bedrock Deep Dive
**Domain 3 (28%)**

### 🧠 Concept Explanation
Bedrock = managed access to multiple FM providers via one API. Key components:
- **Guardrails** — content filters, denied topics, word filters, PII redaction, contextual grounding checks
- **Agents** — multi-step task execution, API orchestration
- **Knowledge Bases** — RAG integration with vector stores
- **Model Evaluation** — compare FMs with human/automated scoring
- **Prompt Management** — versioned, reusable prompts
- **PartyRock** — no-code gen AI playground

**Key facts:**
- Custom models **require Provisioned Throughput**
- Pricing: On-Demand (pay-per-use) vs Provisioned Throughput (reserved capacity, required for custom models)
- Bedrock **never shares** customer prompts/outputs with model providers
- Invocation logging must be **explicitly enabled**

### 💡 Deep Insight
"Guardrails" is the single most-tested Bedrock feature, and the exam loves layering scenarios to test *which* guardrail sub-feature applies:

| Need | Guardrail Feature |
|---|---|
| Block hate/violence/sexual content | Content filters |
| Block an entire subject area (e.g., competitor mentions, off-topic) | Denied topics |
| Block specific words/phrases | Word filters |
| Remove personal identifiers | PII redaction |
| Block factually ungrounded responses vs source docs | Contextual grounding check |

Q297 (denied topics for competitor mentions) and Q290 (layering multiple guardrail types + red-teaming for "most comprehensive" protection) show the exam's favorite move: when a question asks for the **MOST comprehensive** solution, the answer is almost always "layer multiple controls together," not a single feature.

### 🛠️ Apply
Recite the Guardrails table from memory 3x today until it's automatic.

### 📝 Quiz (Day 8)
1. What must be configured before invoking a custom Bedrock model? *(Provisioned Throughput)*
2. Which Bedrock feature blocks an LLM from responding to off-topic subjects? *(Denied topics)*
3. Does Bedrock share customer data with model providers? *(No — never)*
4. What's needed to capture full input/output logs of model calls? *(explicitly enable invocation logging)*
5. "Most comprehensive content protection" scenario — what's the pattern answer? *(layer multiple guardrail types + adversarial red-teaming)*
6. Which feature lets you score multiple FMs side-by-side on the same prompts? *(Bedrock Model Evaluation)*

---

## DAY 9 — Amazon SageMaker Deep Dive
**Domain 3 (28%)**

### 🧠 Concept Explanation

| SageMaker Feature | Purpose |
|---|---|
| **Canvas** | No-code ML model building |
| **Clarify** | Bias detection + explainability (SHAP) |
| **Ground Truth / Ground Truth Plus** | Human-labeling workforce (Plus = fully managed) |
| **Model Monitor** | Detects data/model drift |
| **Data Wrangler** | No/low-code data prep |
| **JumpStart** | Deploy/fine-tune pre-built OSS models, least effort |
| **Feature Store** | Centralized feature management |
| **Model Cards** | Document model transparency for audits |
| **Pipelines** | Orchestrate ML workflows end-to-end |

**Inference types:**

| Scenario | Inference Type |
|---|---|
| Low-latency, real-time predictions | Real-time |
| Large datasets, no immediate need | Batch transform |
| Large payloads, near real-time | Asynchronous |
| Infrequent/small requests, no infra mgmt | Serverless |

### 💡 Deep Insight
The exam's favorite SageMaker confusion pairs:
- **Ground Truth vs Ground Truth Plus**: Ground Truth = you manage the labeling workforce; Ground Truth Plus = AWS manages it fully (human-in-loop labeling *managed*).
- **Ground Truth Plus vs Amazon A2I**: Ground Truth Plus = labeling *training data*. A2I = human review of *live model outputs/predictions* in production. These get swapped as wrong-answer bait constantly.
- **Clarify vs Model Monitor**: Clarify = bias/explainability *analysis* (often pre-deployment or on-demand). Model Monitor = continuous *production drift monitoring*.

For inference types, anchor on the *size + urgency* matrix: big+not urgent = batch; big+near-real-time = async; small+rare = serverless; needs-it-now = real-time.

### 🛠️ Apply
Say this sentence 3 times until automatic: **"Labeling training data → Ground Truth/Plus. Reviewing live predictions → A2I. Bias and explainability → Clarify. Drift in production → Model Monitor."**

### 📝 Quiz (Day 9)
1. Which feature provides SHAP-based per-prediction feature attribution? *(SageMaker Clarify)*
2. 500 GB of data needs processing overnight, no urgency — which inference type? *(Batch transform)*
3. Which is fully managed human labeling, requiring the least operational overhead? *(Ground Truth Plus)*
4. A model's production predictions need periodic human review for quality assurance — which service? *(Amazon A2I)*
5. Non-technical analyst wants to build a model with zero code — which tool? *(SageMaker Canvas)*
6. Which monitors for data drift and model quality degradation post-deployment? *(SageMaker Model Monitor)*

---

## DAY 10 — AWS Pre-Built AI Services
**Domain 3 (28%)**

### 🧠 Concept Explanation

| Service | Function |
|---|---|
| Amazon Comprehend | NLP — sentiment, entities, key phrases, topics |
| Amazon Transcribe | Speech → text |
| Amazon Polly | Text → speech |
| Amazon Lex | Conversational chatbots |
| Amazon Rekognition | Image/video analysis, moderation |
| Amazon Textract | Extract text/structured data from documents |
| Amazon Translate | Language translation |
| Amazon Personalize | Personalized recommendations |
| Amazon Kendra | Enterprise intelligent document search |
| Amazon Q Developer | AI coding assistant (IDE) |
| Amazon Q Business | Enterprise AI assistant over internal data |

### 💡 Deep Insight
This domain is almost pure **pattern matching speed** — the exam gives you a one-line scenario, you must instantly emit the service name. Build muscle memory with these near-identical pairs that are deliberately confusable:

- **Comprehend (text understanding) vs Textract (text extraction from documents/images)** — Comprehend analyzes meaning in text you already have; Textract *pulls* text out of scanned/structured documents.
- **Kendra (search) vs Personalize (recommend)** — both feel like "smart suggestions," but Kendra answers "find the document," Personalize answers "what will this user like."
- **Q Developer (for engineers, in the IDE) vs Q Business (for employees, over company knowledge)** — role is the tell, not capability.
- **Lex (chat interface/dialog management) vs Comprehend (analyzing what was said)** — Lex builds the conversation flow; Comprehend extracts insight from text/utterances.

### 🛠️ Apply
Flashcard drill — cover the right column, say the service from memory, then check:

| Scenario | Service |
|---|---|
| Extract dollar amounts from scanned contracts | Textract |
| Tag images "shoes," "handbag" | Rekognition |
| Show movie recommendations from viewing history | Personalize |
| Search 10,000 HR policy docs in natural language | Kendra |
| Detect PII in call recordings | Amazon Macie (on S3-stored data) |
| Build a customer support chatbot interface | Lex |

### 📝 Quiz (Day 10)
1. Service for extracting structured data (tables/forms) from scanned PDFs? *(Textract)*
2. Service purpose-built for personalized recommendations? *(Personalize)*
3. Difference between Q Developer and Q Business in one sentence? *(Developer = coding assistant for engineers in IDE; Business = enterprise assistant over internal company data for all employees)*
4. Which service handles sentiment/entity/key-phrase extraction from text? *(Comprehend)*
5. Enterprise document search with natural-language queries? *(Kendra)*

---

## DAY 11 — Responsible AI: Pillars, Bias, Clarify, Guardrails
**Domain 4 (14%)**

### 🧠 Concept Explanation
**Responsible AI pillars:** Fairness, Transparency, Explainability, Robustness, Privacy & Security, Veracity.

**Bias types:**
- Sampling bias — training data over/under-represents groups
- Measurement bias — inconsistent data collection
- Observer bias — human labeler prejudice
- Confirmation bias — model reinforces existing assumptions

### 💡 Deep Insight
The exam distinguishes **Transparency vs Explainability** subtly: Transparency = *being open about how the system works generally* (model cards, documentation). Explainability = *specific, technical justification of an individual decision* (SHAP values via Clarify). If the question mentions "why did the model flag THIS specific transaction" → explainability/Clarify. If it says "publish documentation of how our model was built and what data it uses" → transparency/Model Cards.

Bias-type questions are usually solved by asking **"where in the pipeline did the skew enter?"** — collection stage skew = sampling bias; labeling-stage human skew = observer bias; the act of measuring itself being flawed (e.g., a faulty sensor) = measurement bias.

### 🛠️ Apply
For each pillar, name the AWS feature that operationalizes it:
- Fairness/Bias → SageMaker Clarify
- Explainability → SageMaker Clarify (SHAP) + Model Cards
- Privacy → Macie, KMS, Guardrails PII redaction
- Robustness → testing/red-teaming, Model Monitor
- Security → IAM, KMS, PrivateLink

### 📝 Quiz (Day 11)
1. A model treats two demographic groups differently due to underrepresentation in training data — which bias type? *(sampling bias)*
2. What's the AWS tool for both bias detection AND per-prediction explainability? *(SageMaker Clarify)*
3. Publishing documentation about a model's training data and intended use is which pillar? *(Transparency)*
4. A human labeler's personal assumptions skew the dataset — bias type? *(observer bias)*
5. Name all 6 Responsible AI pillars from memory.

---

## DAY 12 — Governance & Regulatory Concepts
**Domain 4 (14%)**

### 🧠 Concept Explanation
- **Data residency** — data must physically stay within a defined geography
- **Data retention** — rules on how long data is kept
- **Data de-identification** — removing/masking identifying details
- **Model Cards** — standardized documentation for audits/transparency

### 💡 Deep Insight
These terms sound interchangeable but are tested as exact synonyms-to-definitions matches — there's no clever scenario trick here, just precision vocabulary. The trap is usually offering "data lineage" or "data sovereignty" as decoys for "data residency" — know that **residency = physical location**, while **lineage = tracking data's origin/transformations over time** (a related but distinct governance concept).

Tie this day directly to Day 13's services: residency pairs with PrivateLink/region selection; de-identification pairs with Macie + Guardrails PII redaction; retention pairs with S3 lifecycle policies and CloudTrail log retention settings.

### 🛠️ Apply
Match each governance term to its enabling AWS control:
- Data residency → region selection + PrivateLink (no data leaving network)
- De-identification → Macie (detect) + Guardrails PII redaction (remove)
- Retention → S3 lifecycle policies / log retention configs
- Audit/compliance reporting → AWS Artifact

### 📝 Quiz (Day 12)
1. A financial firm must keep AI training data within national borders — which concept? *(data residency)*
2. What's the difference between data residency and data lineage? *(residency = physical location requirement; lineage = tracking origin/transformation history)*
3. Standardized documentation of a model for audit purposes is called? *(Model Cards)*
4. Removing personally identifying details from a dataset is called? *(data de-identification)*

---

## DAY 13 — Security, Compliance & Governance Services
**Domain 5 (14%)**

### 🧠 Concept Explanation

| Need | Service |
|---|---|
| Private VPC connectivity to AWS services | **AWS PrivateLink** |
| Least-privilege access control | **IAM** |
| Audit trail of API calls | **AWS CloudTrail** |
| Compliance reports/certifications | **AWS Artifact** |
| Encryption key management | **AWS KMS** |
| PII detection in S3 | **Amazon Macie** |
| Continuous compliance assessment | **AWS Audit Manager** |
| Vulnerability scanning (EC2/containers) | **Amazon Inspector** |

### 💡 Deep Insight
The #1 confusion pair on the entire exam: **CloudTrail vs Audit Manager vs Bedrock invocation logging.**
- **CloudTrail** = logs *who called which API, when* (the management-plane "who did what" record).
- **Bedrock invocation logging** = logs the actual *model input/output content* — separate, opt-in feature.
- **Audit Manager** = ongoing *compliance framework assessment* (mapping controls to standards like HIPAA/PCI), not a raw log.
- **AWS Artifact** = pre-packaged *compliance certificates/reports* AWS itself provides (e.g., SOC reports) — you don't generate these, you *download* them.

If a question asks "who invoked this model at 2 AM" → CloudTrail. If it asks "what did the model actually say in that 2 AM call" → Bedrock invocation logging. If it asks "are we continuously meeting HIPAA requirements" → Audit Manager. If it asks "give me AWS's SOC 2 report for our auditor" → Artifact.

### 🛠️ Apply
Say out loud: **"CloudTrail = who/when called an API. Invocation logging = what was said. Audit Manager = ongoing framework compliance. Artifact = AWS's own pre-built compliance reports."**

### 📝 Quiz (Day 13)
1. Track which IAM user invoked Bedrock at a specific time — which service? *(CloudTrail)*
2. See the actual prompt/response content of a Bedrock call — which feature? *(Bedrock invocation logging, explicitly enabled)*
3. Need AWS's official SOC/compliance certification documents for an external auditor — which service? *(AWS Artifact)*
4. Continuously assess whether your environment meets a named compliance framework — which service? *(AWS Audit Manager)*
5. Deploy a model inside a VPC with zero traffic touching the public internet — which service? *(AWS PrivateLink)*
6. Detect Social Security numbers sitting in an S3 bucket — which service? *(Amazon Macie)*

---

## DAY 14 — Full Timed Practice Exam #1 + Review
**All Domains**

### 🧠 Plan
1. **Hour 1:** Take a 45-question timed practice set pulled evenly across all 5 domains from your 300-question bank (roughly: 9 from D1, 11 from D2, 13 from D3, 6 from D4, 6 from D5). No notes. Simulate real conditions.
2. **Hour 2:** Grade yourself. For every wrong answer, write in your Mistake Log: *(a) the correct answer, (b) the exact reasoning, (c) which "trap pattern" caught you* (e.g., "confused CloudTrail with invocation logging").
3. **Hour 3:** Re-teach yourself each missed concept from this guide's relevant day, then re-attempt only the missed questions cold (no answer visible) to confirm retention.

### 💡 Deep Insight
By this point your error pattern reveals your true weak domain — not the one you *feel* weakest in. Trust the data over your gut. If 4 of 6 misses are Domain 3 service-mapping, that's tonight's extra study, not Domain 1 (even if Domain 1 felt hardest on Day 1).

### 📝 Target
≥ 80% (36/45) before proceeding to Day 15. Below that, repeat Hour 3's re-teaching tonight before sleeping — spaced repetition right before rest measurably improves retention.

---

## DAY 15 — Full Timed Practice Exam #2 + Final Cram + Exam-Day Strategy
**All Domains**

### 🧠 Plan
1. **Hour 1:** Take a second 45-question timed set, different questions than Day 14, same domain distribution. Treat it exactly like exam day — same room, same time pressure.
2. **Hour 2:** Final cram pass. Read through the **Quick Reference Summary** below twice, out loud once. Re-skim your full Mistake Log from Days 1–14 — focus only on patterns that repeated across multiple days.
3. **Hour 3:** Light review only — re-read the "Top 10 Always Remember Rules" below, do 10 random questions as a confidence check, then **stop studying** at least a few hours before any planned rest. Cramming new material in the final hours has negative returns; consolidation matters more than new exposure now.

### 🎯 Exam-Day Strategy
- Read each question stem for the **constraint word**: "LEAST effort," "MOST comprehensive," "private," "real-time," "no-code." That word usually points straight at the answer.
- If two answers both seem technically correct, pick the **more managed/more comprehensive** one — AWS exams consistently reward the option requiring least operational overhead or layering more safeguards.
- Flag and skip anything taking more than ~90 seconds; the ~85-question, 90-minute pace leaves no room for rabbit holes.
- Don't second-guess your first instinct on vocabulary-recall questions (governance terms, metric definitions) — those are usually correct on first pass; over-analysis hurts more than helps there.

---

## 📋 Quick Reference Summary (Final Cram Sheet)

### Top 10 "Always Remember" Rules
1. **Inference costs** = driven by **number of tokens** (input + output)
2. **Custom Bedrock models** require **Provisioned Throughput** before use
3. **CloudTrail** = API audit log | **Bedrock invocation logging** = model I/O content log
4. **Overfitting** = great training, poor test | **Underfitting** = poor on both
5. **RAG** = no retraining, retrieves at inference | **Fine-tuning** = updates model weights
6. **Temperature = 0** = deterministic | **Temperature > 1** = high creativity/randomness
7. **F1 Score** = best metric for imbalanced classification problems
8. **ROUGE** = summarization quality | **BLEU** = translation quality
9. **SageMaker Clarify** = bias detection + SHAP explainability
10. **Bedrock Denied Topics** = block subjects | **Word Filters** = block specific terms

### Exam Day Reflexes
- "LEAST effort/operational overhead" → most managed AWS service
- "Private connectivity" → AWS PrivateLink
- "Content safety on LLM" → Bedrock Guardrails
- "Audit trail of who did what" → AWS CloudTrail
- "No-code ML" → SageMaker Canvas
- "Document text extraction" → Amazon Textract
- "Speech to text" → Transcribe | "Text to speech" → Polly
- "Recommendations" → Amazon Personalize
- "Enterprise search" → Amazon Kendra
- "Performs well on training, poorly on new data" → overfitting
- "Plausible but incorrect info" → hallucination
- "Same input, different outputs" → nondeterminism
- "Human review of AI outputs" → Amazon A2I
- "Bias detection + explainability" → SageMaker Clarify
- "Compliance reports/certifications" → AWS Artifact

---

## 🗂️ Mistake Log Template (copy this for daily use)

```
Date:       Day #:
Question:   [paste or summarize]
My answer:  
Correct:    
Why I got it wrong (trap pattern):
Concept to re-study:
```

---

*This roadmap was generated from your uploaded `AIF-C01-Study-Guide.md`. Good luck — you've got 15 days, 45 hours, and a 300-question bank. That's more than enough if you trust the process and keep the Mistake Log honest.* 🚀

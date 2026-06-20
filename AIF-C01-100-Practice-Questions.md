# AIF-C01 — 100 Topic-Based Practice Questions (Socratic Explanations)

Each explanation walks through the reasoning as a chain of questions before landing on the answer — the goal is to build the *instinct*, not just memorize the fact. Distribution matches official exam weighting: Domain 1 (20Q), Domain 2 (24Q), Domain 3 (28Q), Domain 4 (14Q), Domain 5 (14Q).

---

## Domain 1: Fundamentals of AI and ML (Q1–Q20)

**Q1.** A system adjusts its internal weights after seeing thousands of labeled images, gradually improving its predictions. What is this process called?
A) Inferencing B) Training C) Tokenizing D) Chunking
**Answer:** B
**Explanation:** If the system already had its weights fixed and was just producing an output for new input, what would we call that? That's inferencing. But here, the weights themselves are *changing* in response to data — that adjustment process is training.

**Q2.** Which best describes the relationship between AI, ML, and deep learning?
A) Three unrelated fields B) Deep learning ⊃ ML ⊃ AI C) AI ⊃ ML ⊃ Deep learning D) ML ⊃ AI ⊃ Deep learning
**Answer:** C
**Explanation:** Ask yourself: can you have AI without ML (e.g., hard-coded rules)? Yes. Can you have ML without deep learning (e.g., a simple decision tree)? Yes. So which is the broadest container, and which is the most specific? AI is the umbrella; deep learning is the narrowest, most specific layer inside it.

**Q3.** A model groups customer transactions into clusters with no pre-existing labels. Which learning type is this?
A) Supervised B) Unsupervised C) Reinforcement D) Semi-supervised
**Answer:** B
**Explanation:** Is there a "correct answer" provided for each transaction beforehand? No. So what is the model relying on instead — similarity in the data itself? That's the signature of unsupervised learning.

**Q4.** An agent learns to play a game by receiving points for good moves and penalties for bad ones. Which learning type is this?
A) Supervised B) Unsupervised C) Reinforcement learning D) Transfer learning
**Answer:** C
**Explanation:** Is there a labeled dataset of "correct moves" here, or is the agent discovering good behavior through trial, error, and reward signals over time? That trial-and-reward loop is the defining feature of reinforcement learning.

**Q5.** Which type of data would a stock price history over time be classified as?
A) Tabular B) Time-series C) Unstructured text D) Image
**Answer:** B
**Explanation:** Does the order of the data points matter, and is each point tied to a specific moment? If sequence and timing are essential to the meaning, what category does that point to? Time-series.

**Q6.** A hospital wants to predict patient readmission risk as a percentage probability. Which ML technique fits best?
A) Clustering B) Classification (probability output) C) Regression for a continuous price D) Unsupervised anomaly detection
**Answer:** B
**Explanation:** Is the hospital trying to discover unknown groupings, or are they trying to predict a known outcome category (readmitted vs. not) with a confidence score? That's classification — even though the output looks like a number, it's a probability of belonging to a class.

**Q7.** Which scenario is a case where an ML solution might NOT be appropriate?
A) Forecasting next month's sales B) A legal requirement demands one exact, auditable answer every time, not a prediction C) Detecting spam emails D) Recommending products to a user
**Answer:** B
**Explanation:** If a regulation requires the *same, explainable, deterministic answer* every single time — does a probabilistic model that can vary or be hard to fully explain fit that requirement, or fight against it? When certainty and auditability outweigh the benefit of a learned prediction, ML may not be the right tool.

**Q8.** Real-time inferencing is best suited for which scenario?
A) Processing a year of historical logs overnight B) A chatbot that must respond within milliseconds during a live conversation C) A monthly batch report D) Training a new model from scratch
**Answer:** B
**Explanation:** Does the chatbot have the luxury of waiting minutes or hours for an answer? If the answer is needed immediately, while the user waits, what inferencing mode does that demand?

**Q9.** Which AWS service would you use to convert spoken audio into text?
A) Amazon Polly B) Amazon Transcribe C) Amazon Translate D) Amazon Comprehend
**Answer:** B
**Explanation:** Polly turns text into speech — the opposite direction. If you need audio going IN and text coming OUT, which direction does that flow, and which service name evokes "writing down what was said"?

**Q10.** Which is a component of the ML pipeline that happens BEFORE model training?
A) Model monitoring B) Hyperparameter tuning C) Exploratory data analysis (EDA) D) Deployment
**Answer:** C
**Explanation:** Can you tune hyperparameters or deploy a model that doesn't exist yet? No — those all assume training has already started or finished. EDA, by contrast, is about understanding your data before you ever touch the model. What must logically come first?

**Q11.** A model performs very well on training data but poorly on new, unseen data. What is this called?
A) Underfitting B) Overfitting C) Bias D) High recall
**Answer:** B
**Explanation:** If the model excels on data it has already memorized but fails on anything new, has it learned general patterns, or just memorized noise specific to the training set? That's overfitting.

**Q12.** Which metric is most appropriate when your dataset has 95% negative cases and 5% positive cases?
A) Accuracy B) F1 score C) Mean squared error D) R-squared
**Answer:** B
**Explanation:** If a model that always predicts "negative" would score 95% accuracy while catching zero positives, does accuracy actually tell you anything useful here? F1 balances precision and recall, which matters far more under imbalance.

**Q13.** What does "fit" refer to in an ML model context?
A) The size of the training dataset B) How well a model's predictions match the actual underlying data patterns C) The hardware used for training D) The number of features
**Answer:** B
**Explanation:** When we say a model is a "good fit," are we describing its hardware, or how closely its learned patterns track the true relationships in the data? Fit describes that match — too tight a fit (overfitting) or too loose (underfitting) are both problems.

**Q14.** Which of these is an example of using a pre-trained, open-source model rather than training a custom one?
A) Collecting millions of new labeled images and training from scratch B) Downloading a model from Hugging Face and using it directly C) Hand-coding business rules D) Manually labeling a new dataset
**Answer:** B
**Explanation:** If someone else already trained the model and you're simply using their finished artifact, did you do any training at all? You sourced a pre-trained model rather than building one yourself.

**Q15.** A managed API service for deploying ML models means:
A) You manage every server yourself B) The cloud provider exposes the model via an API and handles the underlying infrastructure C) The model only runs locally D) There is no inference cost
**Answer:** B
**Explanation:** If you call an endpoint and get a prediction back without ever touching a server, who's managing that infrastructure — you, or the provider? That's the definition of a managed API service.

**Q16.** Which AWS service would help you track and manage curated features for reuse across multiple ML models?
A) SageMaker Data Wrangler B) SageMaker Feature Store C) SageMaker Model Monitor D) SageMaker Clarify
**Answer:** B
**Explanation:** If the goal is storing and reusing engineered features so multiple models and teams don't redo the same work, what's the AWS service literally named for storing features?

**Q17.** Continuous model re-training is part of which broader ML concept?
A) EDA B) MLOps C) Tokenization D) Prompt engineering
**Answer:** B
**Explanation:** Is re-training a one-time event, or an ongoing operational practice meant to keep a model fresh as data drifts? Ongoing, repeatable, production-focused practices like this fall under MLOps.

**Q18.** Which business metric would be most relevant when evaluating the ROI of an ML model deployment?
A) F1 score B) AUC C) Development costs vs. revenue generated D) Token count
**Answer:** C
**Explanation:** F1 and AUC tell you about model *performance* — but does performance alone tell a business whether the project was worth the money spent? ROI requires comparing cost to the actual business value generated.

**Q19.** Unlabeled data is best paired with which learning approach by default?
A) Supervised learning B) Unsupervised learning C) Regression only D) Classification only
**Answer:** B
**Explanation:** If there's no "answer key" attached to each data point, can a model learn to predict a known label? Without labels, the natural fit is finding structure on its own — unsupervised learning.

**Q20.** A company wants to forecast next quarter's revenue using past sales trends. Which ML technique is most appropriate?
A) Clustering B) Regression C) Classification D) Reinforcement learning
**Answer:** B
**Explanation:** Is revenue a category (like "fraud/not fraud"), or a continuous numeric value you're trying to predict? When the target is a number on a continuous scale, that's regression.

---

## Domain 2: Fundamentals of Generative AI (Q21–Q44)

**Q21.** What is a "token" in the context of a large language model?
A) A unit of currency for AWS billing B) A small unit of text (word, subword, or character) that the model processes C) A type of neural network layer D) A security credential
**Answer:** B
**Explanation:** When a model reads "unbelievable," does it necessarily see one whole word, or might it break that into smaller recognizable pieces like "un," "believe," "able"? Those processing units — whatever their size — are tokens.

**Q22.** What does "chunking" refer to in a generative AI / RAG context?
A) Compressing model weights B) Breaking a large document into smaller pieces for retrieval and embedding C) Reducing temperature D) Filtering toxic content
**Answer:** B
**Explanation:** If a knowledge base document is 50 pages long but a model can only retrieve and reason over a limited amount of text at once, what would you need to do to that document before embedding it? Break it into manageable pieces — chunks.

**Q23.** An embedding is best described as:
A) A compressed image file B) A numeric vector representing the semantic meaning of text, image, or other data C) A type of prompt template D) A billing unit
**Answer:** B
**Explanation:** How does a model compare whether two sentences mean similar things mathematically? It needs some numeric representation it can measure distance between — that's an embedding, a vector capturing meaning.

**Q24.** Which architecture underlies most modern LLMs, enabling parallel processing of input sequences?
A) Recurrent neural networks (RNNs) only B) Transformer architecture (self-attention) C) Decision trees D) K-means clustering
**Answer:** B
**Explanation:** If a model had to process one word at a time in strict sequence, could it scale efficiently to billions of parameters? The shift to processing relationships between all words simultaneously, via self-attention, is what transformers introduced.

**Q25.** A model capable of accepting both text and image input, and producing text output, is best described as:
A) A diffusion model B) A multi-modal model C) A unimodal model D) A reinforcement learning agent
**Answer:** B
**Explanation:** If the model handles more than one "mode" or type of data (text AND images), what word captures that versatility? Multi-modal.

**Q26.** Diffusion models are most commonly associated with which use case?
A) Text summarization B) Image generation C) Speech-to-text D) Tabular data classification
**Answer:** B
**Explanation:** If a model works by gradually removing noise from a random starting point until a coherent image emerges, what creative task does that "denoising" process power? Image (and video) generation.

**Q27.** Which of the following is a foundation-model use case explicitly suited to generative AI rather than traditional ML?
A) Predicting house prices from square footage B) Generating a unique marketing email from a prompt C) Classifying an email as spam D) Detecting fraud from transaction patterns
**Answer:** B
**Explanation:** Are the other three options about predicting a known category or number, or about creating brand-new original content from a description? Generating new content is the signature use case of generative AI.

**Q28.** What is the correct order of the foundation model lifecycle?
A) Fine-tuning → data selection → deployment → pre-training B) Data selection → model selection → pre-training → fine-tuning → evaluation → deployment → feedback C) Deployment → evaluation → pre-training D) Feedback → pre-training → data selection
**Answer:** B
**Explanation:** Can you fine-tune a model before you've even selected which base model to use? Can you deploy before evaluating? Working backward from what depends on what reveals the natural order: select data and model first, train, refine, check it works, then ship and learn from real use.

**Q29.** Which is an advantage of generative AI commonly cited in the exam guide?
A) Perfect factual accuracy always B) Adaptability across many tasks with the same underlying model C) Zero computational cost D) Fully deterministic outputs every time
**Answer:** B
**Explanation:** Does one LLM need to be retrained from scratch for every new task, or can the same model flexibly handle summarization, translation, and chat with just different prompts? That flexibility is adaptability.

**Q30.** Which is a disadvantage of generative AI?
A) High interpretability B) Hallucination C) Perfect determinism D) Inability to generate any text
**Answer:** B
**Explanation:** If a model can produce a fluent, confident answer that is simply false, what do we call that failure mode? Hallucination.

**Q31.** Nondeterminism in generative AI means:
A) The model always crashes B) The same input can produce different outputs across separate runs C) The model never produces output D) The output is always identical
**Answer:** B
**Explanation:** If you ask the exact same question twice and get two different (but both plausible) answers, is that a bug, or an inherent property of how the model samples its next word? That variability is nondeterminism.

**Q32.** Which factor would NOT typically influence the choice of a generative AI model for a business use case?
A) Performance requirements B) Compliance constraints C) The model's favorite color D) Capabilities and limitations
**Answer:** C
**Explanation:** Of these four, which one isn't even a real property of a model? That's your answer by elimination — models don't have favorite colors, but they do have real performance, compliance, and capability profiles.

**Q33.** "Average revenue per user" (ARPU) as a business metric for a generative AI chatbot would help measure:
A) Token latency B) The financial value generated per user interacting with the AI feature C) Model accuracy D) GPU utilization
**Answer:** B
**Explanation:** Is ARPU a technical performance number, or a business outcome tying revenue to user engagement? When evaluating whether a gen AI feature is worth its cost, business metrics like ARPU answer the "is this making money" question.

**Q34.** Which AWS service is a no-code playground for experimenting with foundation models?
A) Amazon SageMaker Studio B) PartyRock, an Amazon Bedrock Playground C) AWS Glue D) Amazon QuickSight
**Answer:** B
**Explanation:** If the goal is letting anyone, even without code, build and try a gen AI app casually, which AWS offering is literally branded as a "playground"?

**Q35.** Which AWS service provides access to a wide selection of foundation models from multiple providers through one unified API?
A) Amazon SageMaker JumpStart B) Amazon Bedrock C) Amazon Comprehend D) AWS Glue
**Answer:** B
**Explanation:** If you want to switch between models from different providers (Anthropic, Meta, etc.) without managing separate integrations, which managed service is built exactly for that purpose?

**Q36.** Amazon Q is best described as:
A) A database service B) A generative-AI-powered assistant for tasks like coding and business Q&A C) A vector database D) A networking service
**Answer:** B
**Explanation:** If the name itself suggests "ask a question, get help," and the product spans coding assistance and business knowledge — what category of AWS offering does that put it in?

**Q37.** "Provisioned throughput" in Amazon Bedrock pricing refers to:
A) Free usage tier B) Reserved capacity purchased in advance for consistent, high-volume inference needs C) A discount only for first-time users D) A security feature
**Answer:** B
**Explanation:** If your application needs guaranteed, consistent throughput rather than unpredictable pay-as-you-go capacity, what would you need to reserve ahead of time? Provisioned throughput.

**Q38.** Which is a genuine cost tradeoff to consider when choosing AWS generative AI services?
A) Token-based pricing vs. provisioned throughput B) The color scheme of the console C) Whether AWS has a logo D) The number of letters in the model's name
**Answer:** A
**Explanation:** Of these, which option reflects an actual financial and architectural decision you'd have to make? Pay-per-token is flexible but variable; provisioned throughput is predictable but requires upfront commitment — a real tradeoff.

**Q39.** Which best describes "responsiveness" as a benefit of AWS infrastructure for generative AI applications?
A) How colorful the UI is B) How quickly the infrastructure can scale and reply to requests C) How many regions exist D) The number of available models
**Answer:** B
**Explanation:** If a user expects a quick reply from a chatbot, what underlying infrastructure property determines whether that expectation is met? Responsiveness — speed and scalability of the system.

**Q40.** Regional coverage matters for generative AI applications primarily because of:
A) Aesthetic preferences B) Latency and data residency/compliance requirements C) It doesn't matter at all D) Marketing purposes only
**Answer:** B
**Explanation:** If users are halfway across the world from the nearest region, what happens to response time? And if a regulation requires data to stay within a country, what role does region selection play? Both latency and compliance hinge on regional coverage.

**Q41.** Which scenario best illustrates a generative AI customer service use case?
A) A model classifying transactions as fraud or not B) A chatbot drafting personalized responses to support tickets C) A regression model predicting churn D) A clustering algorithm grouping users
**Answer:** B
**Explanation:** Is drafting an original, contextual written reply a generation task, or a classification/prediction task? Generating new text per ticket is the generative AI signature.

**Q42.** Code generation as a generative AI use case means:
A) Compiling existing code faster B) Producing new source code from a natural language description C) Encrypting code D) Deleting unused code automatically
**Answer:** B
**Explanation:** If you type "write a function that sorts a list" and the model produces working code it never saw verbatim before, is that retrieval, or generation? That's generation — creating new code from a description.

**Q43.** Which of these is a true statement about foundation models compared to traditional task-specific ML models?
A) Foundation models can only do one task B) Foundation models are pre-trained broadly and can be adapted to many downstream tasks C) Foundation models never require any data D) Foundation models are always smaller than traditional models
**Answer:** B
**Explanation:** If a traditional model is built and trained for exactly one job, but a foundation model is trained broadly and then reused across many different tasks via prompting or fine-tuning, which is the more flexible design? That breadth-then-adapt pattern defines foundation models.

**Q44.** Which best matches "search" as a generative AI use case?
A) A model summarizes a document into 3 bullet points B) A model retrieves and generates a synthesized answer from many sources in response to a natural-language query C) A model classifies an image D) A model predicts a stock price
**Answer:** B
**Explanation:** If the system doesn't just return links but synthesizes an actual generated answer pulled from multiple retrieved sources, is that classic keyword search, or something generative AI now enables? That synthesis is the gen-AI-powered search use case.

---

## Domain 3: Applications of Foundation Models (Q45–Q72)

**Q45.** Which inference parameter most directly controls the randomness/creativity of a model's output?
A) Top-K only B) Temperature C) Max tokens D) Latency
**Answer:** B
**Explanation:** If lowering a single setting makes the model pick the same most-likely word every time, and raising it makes outputs more varied and surprising, what's that setting called? Temperature.

**Q46.** Setting temperature to 0 results in:
A) Maximum randomness B) Deterministic, repeatable output C) No output at all D) Faster token generation only
**Answer:** B
**Explanation:** If the model always selects the single most probable next token with no randomness introduced, will running the same prompt twice give the same answer? Yes — that's determinism at temperature 0.

**Q47.** Retrieval Augmented Generation (RAG) is best defined as:
A) Retraining a model's weights with new labeled data B) Retrieving relevant external documents at inference time and feeding them into the prompt as context C) Reducing the number of tokens in a prompt D) A type of inference parameter
**Answer:** B
**Explanation:** Does RAG change the model's weights at all, or does it hand the model fresh, relevant information right before it answers? Since the weights stay untouched and only the prompt context grows, RAG is a retrieval-then-generate pattern, not a training method.

**Q48.** Which AWS service is explicitly named for storing embeddings within a vector database for RAG applications?
A) Amazon RDS for MySQL B) Amazon OpenSearch Service C) Amazon CloudFront D) AWS Lambda
**Answer:** B
**Explanation:** Among AWS's vector-capable database options named in the exam guide, which is most commonly paired with Bedrock Knowledge Bases for semantic search? OpenSearch Service.

**Q49.** Besides OpenSearch, which other AWS database is explicitly listed as supporting vector embeddings?
A) Amazon Neptune B) Amazon CloudWatch C) AWS Config D) Amazon Inspector
**Answer:** A
**Explanation:** Which of these options is even a database at all? Only Neptune — a graph database that, along with Aurora, DocumentDB, and RDS for PostgreSQL, can also store embeddings for vector search.

**Q50.** Of the four customization approaches (pre-training, fine-tuning, in-context learning, RAG), which generally requires the LEAST effort and cost?
A) Continued pre-training B) Fine-tuning C) In-context learning / prompt engineering D) Full pre-training from scratch
**Answer:** C
**Explanation:** Which of these options needs zero new training data or weight updates — just clever wording in the prompt itself? In-context learning (prompt engineering) sits at the low-effort end of the spectrum.

**Q51.** What is the role of an "agent" in Amazon Bedrock?
A) A human customer service representative B) An orchestration layer that can break down and execute multi-step tasks, calling APIs and tools as needed C) A type of vector database D) A pricing tier
**Answer:** B
**Explanation:** If a single prompt-response isn't enough because the task requires multiple steps (look something up, call an API, then respond), what component coordinates that multi-step execution? An agent.

**Q52.** "Negative prompts" in prompt engineering are used to:
A) Make the output more positive in tone B) Explicitly tell the model what to avoid or exclude from its output C) Increase temperature D) Reduce token count
**Answer:** B
**Explanation:** If you tell an image generator "no text, no watermark," are you describing what you want, or explicitly excluding what you don't want? That exclusion instruction is a negative prompt.

**Q53.** "Model latent space" refers to:
A) The physical server location B) The internal, high-dimensional representation space where the model encodes learned concepts and relationships C) A type of API endpoint D) The model's billing dashboard
**Answer:** B
**Explanation:** When the model "understands" that "king" and "queen" are related, where is that relationship actually encoded — in a visible table, or in an internal mathematical space the model learned during training? That internal representation is the latent space.

**Q54.** Chain-of-thought prompting is best described as:
A) Asking the model to skip explanation and answer immediately B) Asking the model to reason step-by-step before producing a final answer C) A technique to reduce token usage D) A type of fine-tuning
**Answer:** B
**Explanation:** If you want better accuracy on a multi-step math problem, would it help more to ask for just the final number, or to ask the model to show its reasoning along the way? Walking through intermediate reasoning is chain-of-thought.

**Q55.** Few-shot prompting means:
A) Providing zero examples B) Providing a handful of examples within the prompt to demonstrate the desired format or behavior C) Fine-tuning on thousands of examples D) Using only negative prompts
**Answer:** B
**Explanation:** If you show the model 2–3 example input/output pairs directly in the prompt to set the pattern, without ever updating its weights, what prompting technique is that? Few-shot.

**Q56.** Which of these is a genuine RISK of prompt engineering listed in the official exam guide?
A) Prompt hijacking B) Faster inference C) Lower cost D) Improved accuracy
**Answer:** A
**Explanation:** Of these four, which one describes something going wrong rather than something going right? Hijacking — where a malicious input redirects the model away from its intended instructions — is a real risk, not a benefit.

**Q57.** "Jailbreaking" a model refers to:
A) Optimizing inference speed B) Crafting input designed to bypass the model's safety guardrails C) A type of fine-tuning method D) Reducing the context window
**Answer:** B
**Explanation:** If someone deliberately phrases a request to trick the model into ignoring its safety training, what's that technique called? Jailbreaking.

**Q58.** "Prompt poisoning" is best described as:
A) Injecting malicious or misleading content into a prompt/context to manipulate the model's output B) A technique to speed up inference C) A formal evaluation metric D) A type of model architecture
**Answer:** A
**Explanation:** If an attacker slips harmful instructions into a document that later gets retrieved into a RAG prompt, hoping to manipulate the final answer, what's that contamination called? Poisoning.

**Q59.** Continuous pre-training differs from fine-tuning primarily in that it:
A) Uses small amounts of labeled data for a specific task B) Uses large amounts of unlabeled domain data to extend the model's general knowledge C) Never updates any weights D) Is only used for classification tasks
**Answer:** B
**Explanation:** If you're feeding the model a massive amount of raw, unlabeled text from a new domain (like legal documents) to broaden its general understanding — rather than teaching it one specific labeled task — which of the two methods does that match?

**Q60.** Instruction tuning is a fine-tuning method that:
A) Removes all instructions from training data B) Trains a model specifically to better follow natural-language instructions and prompts C) Only applies to image models D) Requires no data at all
**Answer:** B
**Explanation:** If the goal is making a model more obedient and responsive to direct instructions like "summarize this in 3 bullets," what type of fine-tuning is purpose-built for that improvement?

**Q61.** Transfer learning means:
A) Moving a model between AWS regions B) Taking knowledge learned on one task/domain and applying/adapting it to a related but different task C) Deleting old model versions D) A type of data encryption
**Answer:** B
**Explanation:** If a model trained on general images is adapted to specifically recognize medical X-rays by reusing most of its learned features, is that starting from zero, or transferring prior knowledge? Transfer learning.

**Q62.** Reinforcement Learning from Human Feedback (RLHF) is primarily used to:
A) Speed up tokenization B) Align model outputs with human preferences and values through reward signals based on human ratings C) Compress model size D) Increase the context window
**Answer:** B
**Explanation:** If humans rate which of two model responses they prefer, and that preference data is used to reward the model toward better behavior, what alignment technique does that describe?

**Q63.** Which factor is part of preparing data for fine-tuning, per the exam guide?
A) Data representativeness B) Choosing a logo color C) Selecting a region for billing D) Renaming the S3 bucket
**Answer:** A
**Explanation:** Of these options, which one actually affects whether the fine-tuned model generalizes well to real-world cases? Representativeness — ensuring the training data reflects the true population it will be used on.

**Q64.** ROUGE is a metric most commonly used to evaluate:
A) Image classification accuracy B) Summarization quality C) Speech recognition latency D) Database query speed
**Answer:** B
**Explanation:** If the metric is measuring overlap between a generated summary and a reference summary, what NLP task is it designed for? Summarization.

**Q65.** BLEU is a metric most commonly used to evaluate:
A) Translation quality B) Image generation realism C) Clustering performance D) Network latency
**Answer:** A
**Explanation:** If the metric compares a machine-translated sentence against human reference translations for word-overlap quality, what task is BLEU built for?

**Q66.** BERTScore differs from ROUGE/BLEU primarily because it:
A) Only measures token count B) Uses contextual embeddings to measure semantic similarity rather than just exact word overlap C) Cannot be used for any NLP task D) Measures image resolution
**Answer:** B
**Explanation:** If two sentences mean the same thing but use entirely different words, would word-overlap metrics like BLEU/ROUGE score them well? Probably not. BERTScore instead compares meaning via embeddings, catching similarity that surface-level overlap would miss.

**Q67.** Human evaluation of a foundation model is most valuable for assessing:
A) Token billing accuracy B) Nuanced qualities like tone, helpfulness, and appropriateness that automated metrics struggle to capture C) Server uptime D) Network bandwidth
**Answer:** B
**Explanation:** Can an automated metric easily judge "does this response feel genuinely helpful and appropriately toned"? That kind of subjective, nuanced judgment is exactly where human evaluation adds value automated scores can't fully replace.

**Q68.** Which selection criterion would matter most if your application needs sub-200ms response times?
A) Model size/modality only B) Latency C) Multi-lingual support D) Licensing cost alone
**Answer:** B
**Explanation:** If your hard constraint is response speed, which selection criterion directly measures exactly that? Latency.

**Q69.** A company needs a model that performs well in both English and Japanese. Which selection criterion is most relevant?
A) Multi-lingual capability B) Input/output length C) Model complexity D) Latency
**Answer:** A
**Explanation:** If the requirement is specifically about supporting more than one language well, which named criterion in the exam guide directly addresses that need?

**Q70.** In-context learning is best described as:
A) Updating model weights permanently B) Teaching the model a new task temporarily through examples in the current prompt, without altering its underlying weights C) A type of data encryption D) A networking protocol
**Answer:** B
**Explanation:** If the examples you give the model only affect that one conversation and vanish the next session because nothing was permanently learned, is that fine-tuning, or something more temporary? In-context learning never touches the weights.

**Q71.** Which is the most direct way to increase the length of a model's response?
A) Lower the temperature B) Increase the max tokens / output length parameter C) Use fewer embeddings D) Switch to batch inferencing
**Answer:** B
**Explanation:** If a response keeps getting cut off mid-sentence, which parameter caps how much text the model is allowed to generate? Max tokens.

**Q72.** Cost tradeoffs across pre-training, fine-tuning, in-context learning, and RAG generally follow which pattern?
A) Pre-training is always cheapest B) In-context learning/RAG are typically cheaper and faster than fine-tuning, which is cheaper than full pre-training C) All four cost exactly the same D) RAG always costs more than pre-training
**Answer:** B
**Explanation:** Which option requires building a model from raw data at massive scale (most expensive), versus which simply changes a prompt at runtime (cheapest)? Effort and cost generally scale: prompting/RAG < fine-tuning < continued pre-training < full pre-training.

---

## Domain 4: Guidelines for Responsible AI (Q73–Q86)

**Q73.** Which of these is listed as a feature of responsible AI in the official exam guide?
A) Veracity B) Token pricing C) Latency D) Region selection
**Answer:** A
**Explanation:** Of these four, which one describes a quality of trustworthiness in the AI's outputs rather than a technical or cost property? Veracity — truthfulness — is one of the named responsible AI features alongside bias, fairness, inclusivity, robustness, and safety.

**Q74.** Guardrails for Amazon Bedrock are primarily used to:
A) Speed up model training B) Identify and enforce responsible AI behavior such as blocking harmful content or off-topic responses C) Reduce AWS billing D) Replace the need for IAM
**Answer:** B
**Explanation:** If the tool's job is to stop a model from discussing forbidden topics or producing harmful content, what category of AI development does that directly support? Responsible AI.

**Q75.** Sampling bias occurs when:
A) A human labeler injects personal opinions during labeling B) The training data over- or under-represents certain groups relative to the real population C) The model is too slow D) The encryption key is misconfigured
**Answer:** B
**Explanation:** If your training data was collected mostly from one demographic group, leaving others thin or absent, where did that imbalance enter — during data collection, or during labeling? Collection-stage imbalance is sampling bias.

**Q76.** Overfitting is best understood in a bias/variance context as:
A) High bias, low variance B) Low bias, high variance — model fits training noise too closely C) No bias and no variance D) A type of hallucination only
**Answer:** B
**Explanation:** If a model captures every quirk of its training set, including random noise, will it generalize well to new data, or perform inconsistently? That inconsistency on new data, despite excellent training performance, reflects high variance.

**Q77.** Which characteristic of a dataset is explicitly named as important for responsible AI?
A) File format B) Balanced datasets C) Compression ratio D) Upload speed
**Answer:** B
**Explanation:** Of these options, which one actually affects whether a model treats different groups fairly? A balanced dataset — not over-representing any one group — directly supports fairness.

**Q78.** Which AWS service is specifically designed to detect bias and provide explainability (e.g., via SHAP values) for ML models?
A) Amazon Macie B) SageMaker Clarify C) AWS Config D) Amazon Polly
**Answer:** B
**Explanation:** If the tool's specific job is flagging bias in your data/model and explaining individual predictions, which named SageMaker feature is built exactly for that?

**Q79.** Amazon Augmented AI (A2I) is primarily used for:
A) Encrypting data at rest B) Incorporating human review into ML prediction workflows, especially for low-confidence predictions C) Training foundation models D) Managing IAM permissions
**Answer:** B
**Explanation:** If a model isn't confident about a prediction and a human needs to step in and review it before action is taken, which AWS service is purpose-built for inserting that human checkpoint?

**Q80.** A legal risk explicitly associated with generative AI, per the exam guide, is:
A) Intellectual property infringement claims B) Faster development cycles C) Lower compute costs D) Improved customer satisfaction
**Answer:** A
**Explanation:** If a generated image or text closely resembles existing copyrighted material, what kind of legal exposure could that create for a business? IP infringement claims are explicitly named as a generative AI legal risk.

**Q81.** The difference between a "transparent and explainable" model and one that is not is best described as:
A) Transparent models are always faster B) Transparent/explainable models allow stakeholders to understand how and why decisions were made; opaque models do not C) There is no real difference D) Explainability only applies to image models
**Answer:** B
**Explanation:** If you can trace exactly why a loan application was denied versus just getting a black-box "no," which model property are you relying on? Explainability and transparency.

**Q82.** SageMaker Model Cards are used to:
A) Process credit card payments B) Document a model's intended use, training data, performance, and limitations for transparency C) Encrypt model artifacts D) Schedule training jobs
**Answer:** B
**Explanation:** If auditors or downstream users need a standardized summary of what a model does, what data it was trained on, and where its limits are, what artifact provides exactly that documentation?

**Q83.** A tradeoff between model safety and transparency might involve:
A) More interpretable models sometimes sacrificing some raw performance B) Transparency always improving performance with no tradeoff C) Safety having no relationship to transparency D) Larger models always being more transparent
**Answer:** A
**Explanation:** If a simpler, more interpretable model (like a decision tree) is easier to explain but sometimes less accurate than a complex black-box model, what's being traded off? Interpretability against raw predictive performance.

**Q84.** Human-centered design for explainable AI emphasizes:
A) Designing explanations around technical engineers only B) Designing explanations that are understandable and useful to the actual end users affected by AI decisions C) Removing all explanations to simplify the UI D) Avoiding any user feedback
**Answer:** B
**Explanation:** If a credit decision explanation is written in dense statistical jargon a loan applicant can't parse, has it actually served its purpose? Human-centered design tailors explanations to the people who need to understand and act on them.

**Q85.** Considering environmental impact and sustainability when selecting a model reflects which responsible AI practice?
A) Cost optimization only B) Responsible model-selection practices that weigh broader societal/environmental impact C) A security requirement D) A networking consideration
**Answer:** B
**Explanation:** If choosing a smaller, more efficient model over a massive one partly because of its energy footprint, is that purely a cost decision, or a broader responsibility consideration? The exam guide explicitly frames this as a responsible AI practice.

**Q86.** Subgroup analysis as a bias detection technique involves:
A) Analyzing model performance separately across different demographic or data subgroups B) Reducing the size of the training dataset C) Increasing the temperature parameter D) Merging all data into one group
**Answer:** A
**Explanation:** If overall accuracy looks fine but you suspect the model performs worse for one specific group, would looking at the aggregate number reveal that, or would you need to break performance down group by group? That breakdown is subgroup analysis.

---

## Domain 5: Security, Compliance, and Governance for AI Solutions (Q87–Q100)

**Q87.** Which AWS service would you use to discover and protect sensitive data like PII stored in S3?
A) Amazon Macie B) AWS PrivateLink C) Amazon Inspector D) AWS Config
**Answer:** A
**Explanation:** If the goal is specifically scanning storage for sensitive data like Social Security numbers, which AWS service is purpose-built for that discovery and protection task?

**Q88.** AWS PrivateLink is primarily used to:
A) Encrypt data at rest B) Provide private connectivity between VPCs and AWS services without traversing the public internet C) Manage IAM roles D) Generate compliance reports
**Answer:** B
**Explanation:** If traffic between your VPC and an AWS service needs to avoid the public internet entirely, what networking service is designed exactly for that private connection?

**Q89.** Data lineage refers to:
A) The physical location of a data center B) Tracking the origin, movement, and transformations of data throughout its lifecycle C) The cost of storing data D) The encryption algorithm used
**Answer:** B
**Explanation:** If you need to trace exactly where a dataset came from and every transformation it went through before reaching a model, what's that traceability concept called? Data lineage.

**Q90.** Which is a best practice for secure data engineering mentioned in the exam guide?
A) Implementing privacy-enhancing technologies B) Disabling all logging C) Using the same IAM credentials for every team D) Ignoring data quality checks
**Answer:** A
**Explanation:** Of these four options, which one actually strengthens data security and privacy rather than weakening it? Privacy-enhancing technologies are explicitly named as a best practice.

**Q91.** Prompt injection is a security concern primarily relevant to:
A) Database indexing B) Generative AI applications, where malicious input attempts to override a model's intended instructions C) Network routing D) Hardware failure
**Answer:** B
**Explanation:** If an attacker embeds hidden instructions inside user input or a retrieved document hoping the model obeys them instead of its system prompt, what's that attack called? Prompt injection.

**Q92.** Which AWS service provides a record of who called which API and when, for auditing purposes?
A) AWS CloudTrail B) Amazon Comprehend C) Amazon Polly D) AWS Glue
**Answer:** A
**Explanation:** If you need a chronological record of every API call made across your account, including who made it, which management and governance service is purpose-built for that audit trail?

**Q93.** AWS Audit Manager is best described as:
A) A tool for continuously assessing whether your AWS environment meets a chosen compliance framework B) A vector database C) A speech-to-text service D) An image recognition service
**Answer:** A
**Explanation:** If the goal is ongoing assessment against a named regulatory framework like HIPAA, rather than just a raw log of API calls, which service automates that continuous compliance mapping?

**Q94.** AWS Artifact provides:
A) On-demand compute capacity B) On-demand access to AWS's own compliance reports and certifications (e.g., SOC reports) C) A code repository D) A monitoring dashboard for EC2
**Answer:** B
**Explanation:** If an external auditor asks for AWS's official SOC 2 report, do you generate that yourself, or retrieve something AWS already prepared? AWS Artifact is where you download those pre-existing compliance documents.

**Q95.** Which regulatory compliance standard is explicitly mentioned in the exam guide as relevant to AI systems?
A) ISO B) HTML5 C) USB-C D) Bluetooth 5.0
**Answer:** A
**Explanation:** Of these options, which one is actually a recognized international standards body relevant to compliance, rather than a technical hardware/web standard? ISO (International Organization for Standardization).

**Q96.** Data residency requirements typically mandate:
A) Data must be deleted after 24 hours B) Data must remain within a specific geographic boundary or jurisdiction C) Data must always be unencrypted D) Data must be duplicated across all regions
**Answer:** B
**Explanation:** If a regulation requires citizen data to never leave the country, what type of governance requirement is that — about storage location specifically? Data residency.

**Q97.** The "Generative AI Security Scoping Matrix" mentioned in the exam guide is best understood as:
A) A pricing calculator B) A governance framework to help classify and scope security/risk considerations for different generative AI implementation patterns C) A type of vector database D) An EC2 instance type
**Answer:** B
**Explanation:** If a team needs a structured way to think through varying security responsibilities depending on whether they're using a pre-built service, fine-tuning, or building from scratch, what kind of artifact would provide that structured scoping? A governance framework — which is exactly how this matrix is described.

**Q98.** Which AWS service helps assess workloads for security best practices and provides recommendations, including cost and performance?
A) AWS Trusted Advisor B) Amazon Rekognition C) Amazon Translate D) AWS Glue DataBrew
**Answer:** A
**Explanation:** If the tool's job is scanning your account and proactively recommending fixes across cost, performance, security, and fault tolerance, which AWS service is designed for that broad advisory role?

**Q99.** Encryption "in transit" protects data:
A) Only while stored on disk B) While it is actively moving between systems or services over a network C) Only after deletion D) Only within a single server's memory
**Answer:** B
**Explanation:** If data is being sent from a client to an API endpoint across a network, at what stage is it most vulnerable to interception, and what type of encryption defends specifically against that? Encryption in transit.

**Q100.** Which best illustrates the AWS Shared Responsibility Model as applied to AI systems on AWS?
A) AWS handles 100% of security with no customer involvement B) The customer handles 100% of security with no AWS involvement C) AWS secures the underlying infrastructure (e.g., physical data centers, host OS) while the customer is responsible for securing what they configure (e.g., IAM permissions, data, application-level security) D) Security responsibility is randomly assigned each month
**Answer:** C
**Explanation:** If AWS guarantees the physical data center is locked and the hardware is maintained, does that also guarantee your IAM policies are configured correctly? No — that split, where AWS secures "of the cloud" and you secure "in the cloud," is the Shared Responsibility Model.

---

*End of 100-question set. Distribution: Domain 1 (Q1–20), Domain 2 (Q21–44), Domain 3 (Q45–72), Domain 4 (Q73–86), Domain 5 (Q87–100) — matching official exam weightings of 20/24/28/14/14%.*

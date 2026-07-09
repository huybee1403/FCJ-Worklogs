---
title: "Event 1"
date: 2026-05-23
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# EVENT REPORT: AWS COMMUNITY DAY VIETNAM TECH CONFERENCE
---
![Proof of Attendance at AWS COMMUNITY DAY VIETNAM](/images/1779719099882.jpg)
> [!IMPORTANT]
> ### 📅 Event Overview & Objectives
> **AWS Community Day Vietnam 2026** is the largest community-led tech event of the year focusing on the Amazon Web Services Cloud ecosystem. This report synthesizes and provides an in-depth analysis of **6 deep-dive technical sessions** covering today's hottest trends: The AWS Ecosystem, Generative AI, Enterprise Multi-Agent Architecture, and cloud cost/performance optimization strategies.

## 2. DETAILED SESSION BREAKDOWNS
### Session 1: Making AI Actually Work for You — Context Is Everything
* **Speaker:** Trinh Truong – Platform Engineer at GoTymeX.
* **Core Topic:** The vital importance of Context in optimizing AI effectiveness and building a "Second AI Brain."
#### Key Takeaways:
1. **The Bottleneck in AI Applications:** * Many disappointing AI outputs are caused by a lack of input context (vague prompts, missing target outcomes, unstated constraints) rather than a weak model.
   * AI cannot read user minds; it operates purely on the data and parameters provided.
2. **Defining Context:** Comprises the Target Goal, Real-world Situation, Technical/Budgetary/Formatting Constraints, and Relevant Evidence or reference data.
3. **Common Context Pitfalls:**
   * *Information Overstuffing (Internet Puller):* Copying massive raw documents or numerous screenshots into the chatbot, which generates model noise and inflates token costs.
   * *Restating What the AI Already Knows:* For instance, feeding generic Express.js boilerplate and asking the AI to write Express.js code instead of defining the exact refactoring requirements (e.g., pagination, validation).
   * *Lack of Clear Goals and Rconstraints.*
4. **The Evolution of AI Apps:** Shifting from **Prompt (Single-turn Questions)** $\rightarrow$ **Context (Context-aware Systems)** $\rightarrow$ **Memory (Personalized Retentive Systems)**.
5. **The "Second AI Brain" Blueprint:**
   * Operates as a continuous loop: **Store (Notes/Codebases)** $\rightarrow$ **Retrieve (Relevant Segments)** $\rightarrow$ **Generate (Tailored Responses)** $\rightarrow$ **Learn (Retain Feedback)**.
   * Mapping to AWS Services: Amazon S3, Vector Databases, Amazon Bedrock, and various Observability tools.
---
### Session 2: Friendly AI Assistant with Amazon Q (Quick)
* **Speaker:** Pham Ngo Hai Anh – AWS Community Builder at G-AsiaPacific Vietnam.
* **Core Topic:** Building user-friendly enterprise AI assistants using the Amazon Quick (Amazon Q) product suite.
#### Key Takeaways:
1. **Enterprise User Pain Points:** Spending excessive time gathering/analyzing data from siloed environments, handling repetitive manual tasks, and relying heavily on data specialists for deep analytics.
2. **AWS Agentic AI Solutions:** * Introduction to the **Amazon Quick Suite** – a unified experience that securely integrates enterprise data repositories to dramatically shorten the time from data to action.
   * Powerful Integration Support: Features 40+ built-in data connectors with the capacity to ingest user uploads, relational databases, and enterprise data warehouses.
3. **Responsible AI and Governance:** Ensuring enterprise-grade safety through rigorous access controls, security Guardrails, and strict regulatory compliance.
4. **Real-world Use Case:** A Project Management Assistant (PM Assistant) that automates writing Minutes of Meetings (MoM), broadcasts action items to stakeholders, and schedules follow-up syncs.
---
### Session 3: From Edge to Origin — CloudFront as Your Foundation
* **Speaker:** Nguyen Tuan Thinh – DevOps Engineer at First Cloud AI Journey.
* **Core Topic:** Optimizing costs, boosting security, and accelerating web application performance via Amazon CloudFront.
#### Key Takeaways:
1. **Traditional CDN Pay-As-You-Go Challenges:**
   * Pure consumption-based bills expose businesses to severe "bill spikes" costing hundreds of thousands of dollars during unexpected traffic surges or volumetric DDoS attacks.
2. **New AWS Pricing Structures (Launched November 2025):** * Fixed-Price CDN & Security Pricing Plans bundle together CloudFront, AWS WAF, DDoS protection, Route 53 DNS, CloudWatch Logging, and S3 storage under a predictable monthly financial forecast.
3. **Volumetric DDoS Mitigation:** Leveraging CloudFront’s massive globally distributed edge network (700+ PoPs across 50+ countries) alongside AWS Shield and AWS WAF to drop malicious traffic closest to the source.
4. **Cost & Performance Optimization:**
   * Zero Data Transfer Out (DTO) fees when shifting assets from AWS origin services down to CloudFront.
   * Reducing CPU load on origin infrastructure (EC2/ALB) by offloading TLS handshakes, compression algorithms (Gzip/Brotli), and static asset caching to the Edge.
   * Maximizing throughput via Multi-layer caching (Edge $\rightarrow$ Regional Edge Caches $\rightarrow$ Origin Shield) and implementing HTTP/3 (QUIC/UDP) for parallel stream loading.
5. **Advanced Security Mechanisms:** * Native support for Mutual TLS (mTLS), Origin Access Control (OAC) to hide origin servers (S3, API Gateway, Lambda), and Signed URLs/Cookies for digital rights management.
---
### Session 4: 36 Hours with LotusHacks — Building UTMorpho from Idea to Reality
* **Speaker/Team:** Team VIB.
* **Core Topic:** Engineering execution under pressure during Vietnam’s largest Hackathon (LotusHacks) and the journey of building UTMorpho in 36 hours.
#### Key Takeaways:
1. **From Zero to One:** Starting with absolute zero concrete ideas at Hour 0, the team derived inspiration from immediate pain points in daily workflows to architect **UTMorpho** – a utility focused on absolute content-editing experiences.
2. **Rapid Development Lifecycles Under Pressure (36 Hours):**
   * Setting up environment scaffolding & team alignment.
   * Isolating and shipping the core functional slice first.
   * Battling through fatigue during "the hard middle."
   * Feature consolidation, polishing, and final pitch preparation.
3. **Technical Hurdles and Edge Cases:**
   * AI overgeneration of unnecessary text outputs.
   * Reaching hard model token limits.
   * Severe developer burnout as the pitching deadline drew close.
4. **Critical Lessons Learned:**
   * "Real Frustration Creates Real Ideas" – the most impactful MVPs stem from practical workflow bottlenecks.
   * Quality and focus trump an overwhelming volume of disjointed concepts.
   * Transparent team synchronization and swift communication steer success under strict temporal boundaries.
---
### Session 5: Non-Determinism of "Deterministic" LLM Settings
* **Speaker:** Duc Dao – Solution Architect at Cloud Kinetics.
* **Core Topic:** The inherent non-determinism of LLMs even when configuring Temperature = 0, along with systemic mitigation strategies.
#### Key Takeaways:
1. **Theory vs. Reality:** * *Theory:* Setting `Temperature = 0` forces greedy decoding – picking the absolute highest probability token at every step to guarantee predictable, reproducible string generation.
   * *Reality:* Empirical research across 5 flagship models (GPT-3.5, GPT-4o, Llama-3, Mixtral) proves **no commercial LLM exhibits absolute determinism**. Output accuracy can swing by up to 15% across identical runs, and exact string matches (TARr@10) approach 0% on complex reasoning tasks.
2. **Root Causes:**
   * *Hardware Constraints (GPU):* Floating-point arithmetic calculations on parallel GPUs lack strict associativity (`(a + b) + c` does not always equal `a + (b + c)` under IEEE 754). Non-deterministic execution order across thousands of GPU threads introduces microscopic rounding errors in logits, altering the final argmax outcome (token flip).
   * *Commercial Architectures (Batching):* API providers group distinct user requests together (Inference Batching) to optimize hardware utilization. Thus, your prompt's calculation matrix is implicitly impacted by parallel requests processing inside the same batch.
3. **Mitigation Strategies:**
   * *Multi-run Ensembles & Majority Voting:* Sampling prompts multiple times and running consensus logic on outputs.
   * *Enforced Structural Schemas:* Mandating JSON mode or function calling parameters to narrow vocabulary generation spaces.
   * *Self-hosting Models:* Providing absolute authority over inference server hardware and configurations.
   * *Production Tip:* Set `Temperature = 0.1` instead of `0` to prevent repetitive loops, and build robust downstream processing systems designed to handle data variance.
---
### Chuyên đề 6: Enterprise-Grade Multi-Agent System — The Case of Startup Credit Scoring
* **Speaker:** Vy Lam – Senior Business Systems Analyst at VPBank.
* **Core Topic:** Architecting enterprise-ready Multi-Agent ecosystems to solve credit scoring models for early-stage startups.
#### Key Takeaways:
1. **Structural Data Mismatch:** Traditional banking credit frameworks require tangible collateral, 3-year historical audited financial statements, and long-term credit profiles. Startups, conversely, operate with only 6–18 months of transactional footprints, rely heavily on intellectual property (IP), show non-linear growth trajectories, and store highly unstructured data.
2. **Limitations of Single Agent Deployments:** Prone to context dilution due to overly broad prompt constraints (Context Limits), lacks internal peer review (Checks & Balances), and frequently hallucinating unreliable data points.
3. **Virtual Credit Committee Model (Multi-Agent):**
   * Highly specialized agents working in sync: **Financial Analyst** (cashflow, burn rate tracking), **Market Analyst** (TAM/SAM/SOM, competitor benchmarks), **Team Evaluator** (founder background assessment), **Risk Assessor** (downside modeling), and **Compliance Agent** (banking policy checking).
   * All sub-agents are governed by a central **Manager Agent** to reach a consensus credit score backed by a definitive Audit Trail.
4. **6 Pillars of Enterprise-Grade AI:** Security, Data Governance, Network Isolation (VPC Architecture), Operations Observability, Human-in-the-loop Factors, and Legal Compliance.
5. **Tangible Return on Investment (Real-world ROI):**
   * Document processing lifecycles reduced from **2–3 weeks down to 2–4 hours** (a 95% acceleration).
   * Analyst labor cut down from **40–60 hours per application to 2–4 hours**.
   * Approval ratios expanded from **15–20% up to 35–45%** by correctly quantifying startup traction.
   * Lowered strategic decision-making overhead by 95%.
6. **Implementation Timeline:** Divided into 4 distinct execution phases: **Foundation** $\rightarrow$ **Integration** $\rightarrow$ **Pilot** $\rightarrow$ **Full-Scale Production**.
---
> [!TIP]
> ### 💡 Strategic Synthesis & Tech Trends
> 
> Reviewing the collective sessions from the event points to 3 macro trends driving the current state of technology implementation:
> 
> 1. **The Shift from "Naïve AI" to "Complex, Specialized Composite Ecosystems"**:
>    * Basic prompt engineering has reached its architectural limit. Context Engineering, stateful Memory loops, and collaborative Multi-Agent frameworks are foundational to onboarding AI into highly complex, audit-heavy domains like automated corporate finance (VPBank) and system orchestration (Amazon Q).
> 2. **Production-ready Engineers Must Design for Technical Limitations**:
>    * Teams must accept non-determinism as a constant reality of commercial LLM processing at the GPU and batch layer. Rather than blind faith in `temp=0`, system engineers must build robust downstream validation mechanisms (majority voting ensembles, validation guardrails).
> 3. **Rock-solid Cloud Infrastructure Enables Competitive Application Scaling**:
>    * Whether deploying bleeding-edge AI models or core traditional web layouts, fundamental infrastructure building blocks—such as advanced caching proxies (CloudFront), perimeter firewalls (WAF), network
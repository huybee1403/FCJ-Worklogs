---
title: "Event 2"
date: 2026-05-30
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# REFLECTION: INTRODUCING HERA — VOICE AGENT WORKSHOP ON AWS
---
> [!IMPORTANT]
> ### 🎯 Workshop Objectives & Overview
> **The Hera Workshop** is a detailed hands-on guide for deploying a real-time **Bilingual Voice Agent** using **Amazon Bedrock AgentCore Runtime** and the **Amazon Nova 2 Sonic** audio model.


## 1. What are Voice AI and the Hera Project?

### Voice Agent

A Voice Agent is an artificial intelligence (AI) service that operates on a mechanism of **real-time bidirectional audio streaming**.

Operational flow:

1. The user speaks into the microphone.
2. The audio is streamed to a speech-to-speech model.
3. The model processes and generates a voice response.
4. The response audio is played back in the browser.

The entire cycle occurs with a latency of under **1 second**.

### Hera

Hera uses **Amazon Nova 2 Sonic**, a speech-to-speech model on **Amazon Bedrock**, deployed in the **ap-northeast-1 (Tokyo)** region.

Key capabilities:

- Real-time voice communication.
- Support for tool calling (*Tool Use*).
- The ability to query the **Amazon Bedrock Knowledge Base** right within the same streaming flow.

---

## 2. Rationale for the Tech Stack Selection

The Hera Workshop is built on a combination of the following technologies.

### Amazon Nova 2 Sonic

- A pure-AWS speech-to-speech model.
- Low latency from Vietnam.
- Billed per minute of usage.
- Native support for Tool Use with the Bedrock Knowledge Base.

### Amazon Bedrock AgentCore Runtime

- A managed runtime.
- No need to configure VPC, ALB, or NAT Gateway.
- Support for ARM64.
- Security through IMDSv2.
- Easy to debug and operate.

### Pipecat (v1.1.0)

Pipecat serves as the *orchestrator* for the voice pipeline.

Characteristics:

- Built-in `AWSNovaSonicLLMService` integration.
- Automatically handles the **8-minute** maximum stream limit of Nova Sonic.
- Manages the entire voice loop.

### S3 Vectors + Titan v2

A low-cost RAG solution:

- Approximately **0.10 USD/month** with small datasets.
- Significantly cheaper than OpenSearch Serverless (**200–400 USD/month**).

### Terraform + AWS CDK (Python)

A combined Infrastructure as Code approach:

| Tool | Role |
|---------|----------|
| Terraform | Manages the Bedrock Knowledge Base |
| AWS CDK (Python) | Deploys the AgentCore Runtime |

---

## 3. Overall Architecture

The voice processing workflow proceeds as follows.

### Step 1. Connection Request

The browser requests a **WebSocket URL (WSS)** signed with **AWS SigV4**, valid for approximately **300 seconds**, from the **Presigner Lambda**.

### Step 2. Connection

The browser connects to the **AgentCore Runtime** (the Pipecat container) via WebSocket and streams **16 kHz** audio.

### Step 3. Tool Use

The AgentCore Runtime forwards the audio to Nova 2 Sonic.

When Sonic detects a question that requires looking up data, it calls the tool:

```text
lookup_product
```

### Step 4. RAG Retrieval

The AgentCore Runtime calls:

```text
bedrock-agent-runtime.retrieve
```

to query the **Bedrock Knowledge Base**.

The Knowledge Base returns:

- The top 3 results
- From S3 Vectors

The AgentCore Runtime then sends the results back to Nova Sonic within the same streaming flow.

### Step 5. Response

Nova Sonic:

- Generates a voice response at 24 kHz.
- Sends the audio back to the AgentCore Runtime.
- The AgentCore Runtime streams it back to the browser.
- The browser plays the audio for the user.

> The total processing time for a single conversation turn (End-to-End Turn) is approximately **3 seconds**.

---

## 4. Deployment Region

The default region:

```text
ap-northeast-1 (Tokyo)
```

Reasons:

- The lowest latency to Vietnam.
- Full support for:
  - Amazon Nova 2 Sonic
  - AgentCore Runtime
  - Bedrock Knowledge Base
  - S3 Vectors

Other supported regions:

- `us-east-1`
- `us-west-2`
- `eu-north-1`

---

## 5. Prerequisites Before Getting Started

### AWS Account

You need to prepare:

- An AWS Account
- An IAM User
- `AdministratorAccess` permissions

> Use this only for the workshop; do not use the Root account.

### Knowledge

Learners should have basic knowledge of:

- AWS Console
- IAM
- VPC
- Docker
- Terraform

### Tools to Install

- AWS CLI v2
- Terraform >= 1.9
- uv (Python package manager)
- Docker Desktop (with Buildx Multi-Arch support)
- jq
- Chrome / Firefox / Safari (with HTTPS and microphone support)

> The workshop uses **uv**, not `pip`.

### Cost

Estimated:

- **2–5 USD**
- For approximately **2 hours** of hands-on practice.

> After completing the workshop, perform the **Cleanup** step to avoid incurring ongoing resource maintenance costs.

---

## 6. Workshop Conventions

### Source Code

The source code is organized by **Phase** for ease of following along.

### Images

Every screenshot includes:

- A red box
- A guiding arrow
- Annotations at the important steps on the AWS Console

### Language

The workshop uses:

- Chatbot: **English** (Nova Sonic works best with English)
- Documentation: **Bilingual English–Vietnamese (vi/en)**

> The CI system checks the number of Vietnamese and English pages. The build will fail if the two languages are out of sync.

---

> [!TIP]
> ### 💡 Lessons Learned & Synthesis
> 
> Through studying and practicing the Hera Workshop, I have drawn several important technological insights:
> 
> 1. **The revolution of real-time Voice AI**:
>    * Thanks to **Amazon Nova 2 Sonic** with its improved speech-to-speech architecture, bidirectional communication with AI is no longer fragmented into intermediate steps (STT -> LLM -> TTS), which helps optimize latency to under 1 second, delivering a natural conversational experience that is nearly human-like.
> 2. **Optimizing infrastructure design and cost (Serverless & minimalist RAG)**:
>    * Instead of using the costly OpenSearch Serverless (200-400 USD/month), the integrated **S3 Vectors + Titan v2** solution consumes only about 0.10 USD/month while still fully meeting RAG requirements.
>    * Using **Amazon Bedrock AgentCore Runtime** simplifies managing the lifecycle of the Pipecat container without requiring complex configuration of VPC, ALB, or NAT Gateway components, saving operational costs while ensuring security.
> 3. **The importance of synchronization in Infrastructure as Code (IaC)**:
>    * Combining **Terraform** (for the Bedrock Knowledge Base) and **AWS CDK Python** (for the AgentCore Runtime) in parallel creates a seamless deployment flow that is easy to manage and easy to clean up (cleanup) after the project ends.

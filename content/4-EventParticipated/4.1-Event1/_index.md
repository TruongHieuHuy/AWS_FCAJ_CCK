---
title: "Event 1"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Event Report: AWS Community Day 2026 (May 2026)

![AWS Community Day](/images/4-EventParticipated/4.1-Event1/Event1.jpg)

## Date & Venue

- **Venue:** New World Hotel, District 1, Ho Chi Minh City
- **Date:** Saturday, May 23, 2026
- **Role:** Attendee

---

## Event Objectives

- Update on the latest cloud computing and Generative AI (GenAI) technology trends in Vietnam.
- Learn about solutions for optimizing edge infrastructure performance and reducing latency using Amazon CloudFront.
- Study the operation mechanism of Multi-Agent Systems and their applications in complex financial scenarios.
- Explore testing methodologies and techniques to mitigate the non-deterministic nature of Large Language Models (LLMs).
- Connect, learn, and network with AWS Solutions Architects and industry experts.

---

## Featured Speakers

- **Mr. Dennis Traeger** - Head of Solutions Architecture, AWS Vietnam
- **Mr. Donnie Prakoso** - Principal Developer Advocate, AWS
- **Mr. Nguyen Phung** - AWS User Group Leader & Solutions Architect

---

## Key Highlights & Detailed Sessions

### 1. Building a Second Brain & Context Engineering
This session focused on transitioning from simple prompt writing to building a comprehensive knowledge management architecture (Second Brain).
- AI only delivers true value when provided with deep business context.
- Designing automated context management systems reduces token consumption and increases LLM response accuracy.
- Deep integration into daily business workflows generates direct economic value.

### 2. Addressing LLM Non-Determinism in Testing
Since LLMs operate on probabilistic mechanisms, output consistency remains a challenge even with identical prompts.
- Even at `temperature = 0`, LLMs exhibit variance in outputs due to hardware-level parallel processing optimization on GPUs.
- Recommendations include implementing automated bulk testing combined with structured outputs to enforce specific formats.
- Implementing evaluation layers and Guardrails to sanitize and normalize data before it reaches the end user.

### 3. Multi-Agent Architecture in Credit Assessment (Virtual Credit Committee)
A solution utilizing specialized AI agents to automate complex manual approval processes in the financial sector.
- Instead of using a single LLM to handle the entire task, the system distributes work among independent agents: Financial Analyst Agent, Market Risk Agent, and Compliance Agent.
- These agents collaborate and critique each other's outputs (Agent-in-the-loop) to reach an optimal consensus.
- Incorporating human oversight (Human-in-the-loop) for sensitive, final decisions.

### 4. RTT Optimization and Edge Security with Amazon CloudFront
An architectural deep dive into global content delivery optimization to improve user experience and tighten security.
- Using Amazon CloudFront to minimize RTT (Round Trip Time) via global Edge Locations.
- Optimizing outbound data transfer costs (Data Transfer Out - DTO).
- Leveraging CloudFront Functions and Lambda@Edge to process application logic at the edge, reducing origin server load.

---

## Key Takeaways

### 1. Cloud Engineer Perspective
- **Edge Infrastructure Optimization:** CloudFront is not just for static caching; it serves as the first line of defense (DDoS protection, WAF) and significantly improves application performance.
- **Ensuring AI Stability:** Understanding hardware limits and LLM non-determinism enables engineers to build more defensive systems with robust retry and validation mechanisms.

### 2. BA/SA Perspective
- **Solving Business Pain Points:** The "Virtual Credit Committee" demonstrates how GenAI can streamline compliance-heavy workflows, removing operational bottlenecks and driving business velocity.
- **Cost Optimization & ROI:** Optimizing Context Engineering saves organizations thousands of dollars in LLM API call costs while maintaining rapid customer service response times.

---

## Application to FCAJ Internship & Future Direction

- **Practical Application:** I applied edge optimization concepts from Amazon CloudFront to Module 8 (Website) of the Budget Tracker project to deliver static reports quickly and securely.
- **Design Strategy:** I implemented structured prompts with clear contexts and output format constraints for the intelligent query features of our application.

---

## Event Experience

Attending AWS Community Day 2026 opened my eyes to the scale of real-world cloud applications. I realized that the gap between theoretical labs and enterprise-level software is bridged by meticulous security design, strict cost management, and relentless automation. This experience has fueled my commitment to completing my internship project to the highest standard.

---

## Event Photos

![AWS Community Day 2026](/images/4-EventParticipated/4.1-Event1/Event_1.jpg)

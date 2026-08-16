# Evance Chapuma — AI Automation Portfolio

[![Upwork](https://img.shields.io/badge/Hire%20on-Upwork-6FDA44?style=for-the-badge&logo=upwork&logoColor=white)](https://www.upwork.com/freelancers/evancechapuma)
[![n8n](https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io)
[![Make](https://img.shields.io/badge/Make-6D00CC?style=for-the-badge&logo=make&logoColor=white)](https://www.make.com)
[![Zapier](https://img.shields.io/badge/Zapier-FF4A00?style=for-the-badge&logo=zapier&logoColor=white)](https://zapier.com)
[![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)](https://openai.com)
[![Claude](https://img.shields.io/badge/Claude-111827?style=for-the-badge&logo=anthropic&logoColor=white)](https://www.anthropic.com)
[![Airtable](https://img.shields.io/badge/Airtable-18BFFF?style=for-the-badge&logo=airtable&logoColor=white)](https://airtable.com)
[![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com)

---

> **I build AI-powered automation systems that save businesses 10–40 hours per week** — from intelligent voice agents that book appointments, to WhatsApp bots that qualify leads, to multi-agent workflows that run entire business processes on autopilot.

---

## About Me

I'm **Evance Chapuma**, a freelance AI automation specialist with hands-on experience designing and deploying production-grade automation systems for clients across real estate, e-commerce, customer support, and event management.

My core stack spans **n8n**, **Make (Integromat)**, **Zapier**, **Vapi** (voice AI), **HubSpot**, **WhatsApp/Twilio**, and **Django** — with AI agents powered by **OpenAI GPT-4o** and **Claude**.

I don't just connect APIs. I design systems that handle edge cases, fail gracefully, and scale with your business.

📬 **Available for hire:** [Upwork Profile](https://www.upwork.com/freelancers/evancechapuma)

---

## Projects

| # | Project | Description | Stack | Folder |
|---|---------|-------------|-------|--------|
| 11 | [Rooms OKC — Rental Marketplace Platform](#11--rooms-okc--rental-marketplace-platform) | Production Django marketplace serving three audiences — public listings site, agency CMS, and self-service owner portal — with lead ownership and SLA escalation, a Cloudflare Email Worker that threads tenant replies back onto their lead, a listing review queue, layered spam defence, and cookieless first-party analytics. 849 tests, CI, four cron services | Django · PostgreSQL · Redis · Cloudflare (R2 · CDN · Workers · Turnstile) · Railway · Docker | [→](./projects/11-rooms-okc/) |
| 10 | [Candidate Pipeline Automation](#10-candidate-pipeline-automation) | End-to-end Zapier recruitment pipeline — Claude AI parses CV submissions from Typeform, scores skill overlap against open roles, routes to Shortlisted or Talent Pool in Airtable, creates a ClickUp review task, sends an acknowledgement email, and fires a Slack recruiter reminder after 3 days if no action taken | Zapier · Claude Sonnet · Typeform · Airtable · ClickUp · Gmail · Slack | [→](./projects/10-candidate-pipeline/) |
| 09 | [Real Estate — Lead-to-Close Automation](#09-real-estate--lead-to-close-automation) | Two-workflow pipeline: W1 AI-qualifies inbound leads and routes them to ClickUp, books discovery calls, and alerts the agent; W2 fires when a deal is Won and provisions the full client project across Drive, ClickUp, Gmail, and Slack in under 60 seconds | n8n · Claude Opus · Claude Sonnet · ClickUp · Google Drive · Google Calendar · Gmail · Slack | [→](./projects/09-real-estate-lead-to-close/) |
| 08 | [Weekly KPI Summary — Wellness Practice](#08-weekly-kpi-summary--wellness-practice) | Automated weekly business report — parallel Airtable fetching, JS KPI calculation, AI insights, branded HTML email | n8n · Airtable · Claude Sonnet · Gmail | [→](./projects/08-hackensack-weekly-kpi/) |
| 07 | [AI Law Firm Receptionist](#07-ai-law-firm-receptionist) | 8-workflow autonomous receptionist — triage, intake, scheduling, conflict checks, billing, documents | n8n · Claude · Clio · Google Calendar · Zoom · Gmail · Slack | [→](./projects/07-law-firm-receptionist/) |
| 06 | [WhatsApp Event Registration System](#06-whatsapp-event-registration-system) | End-to-end event registration via WhatsApp: PDF ingestion, payment verification, seat assignment | n8n · Airtable · Twilio · OpenAI Vision | [→](./projects/06-whatsapp-event-registration/) |
| 05 | [Multi-Agent Personal Assistant](#05-multi-agent-personal-assistant) | Orchestrated AI assistant managing email, calendar, CRM, and messaging | n8n · HubSpot · Gmail · Telegram | [→](./projects/05-multi-agent-personal-assistant/) |
| 04 | [Vapi Customer Support Agent](#04-vapi-customer-support-agent) | Voice AI agent that handles Tier-1 support calls with FAQ resolution | Vapi · n8n · OpenAI | [→](./projects/04-vapi-customer-support/) |
| 03 | [Vapi Real Estate Booking Agent](#03-vapi-real-estate-booking-agent) | Voice AI agent that handles property inquiries and books viewings | Vapi · n8n · Google Calendar | [→](./projects/03-vapi-real-estate-booking/) |
| 02 | [WhatsApp Lead Agent](#02-whatsapp-lead-agent) | Conversational AI agent that qualifies inbound leads via WhatsApp | n8n · Twilio · OpenAI | [→](./projects/02-whatsapp-lead-agent/) |
| 01 | [Google Review Responder](#01-google-review-responder) | Multi-agent system that auto-responds to Google Reviews with sentiment-aware messaging | n8n · OpenAI · Google Maps API | [→](./projects/01-google-review-responder/) |

---

## Project Highlights

### 11 — Rooms OKC — Rental Marketplace Platform

A production Django platform for a room-rental agency in Oklahoma City, serving three distinct audiences from one codebase: a public listings site for tenants, a bespoke CMS for agency staff, and a self-service portal for invited property owners.

The build is organised around the problems that start *after* a tenant clicks send. **Lead ownership is explicit** — read scope and write scope are separate querysets, so a manager can oversee every owner's leads while only being able to *act* on their own; an hourly cron escalates a lead to the agency only when the owner's response window lapses, which is the sole path that transfers that right. **A dependency-free Cloudflare Email Worker** sits in the domain's mail routing and hands inbound messages to the app, so a tenant's email reply threads back onto its lead instead of landing in a shared mailbox — and the app tells the Worker, per message, whether the mailbox should even receive a copy, which is what eliminated the duplicate-email problem. **Owner listings pass a review queue** before the public sees them, with re-review triggered only by material changes, and the owner-facing explanation of that rule generated from the same frozen field set the workflow branches on. **Contact-form spam** is met with a honeypot, weighted heuristic scoring, and Turnstile — flagged leads are quarantined rather than deleted, and the auto-reply is suppressed so the form can't be used as a relay. **Traffic is measured in-house** with a date-salted visitor hash: no cookie, no stored IP, no consent banner, and every recorded path validated against the URLconf before it's written.

Rounded out with a full media pipeline (EXIF-stripped photo processing, background FFmpeg video transcoding), version-stamped cache invalidation behind a Cloudflare CDN, a 30-day grace period on account deletion that keeps lead history when a landlord leaves, and a JSON-LD/SEO layer that deliberately withholds contact details from structured data to keep them unharvestable.

**Engineering:** ~11,300 lines of application Python across six Django apps · **849 tests** on real Postgres · CI running Ruff lint/format plus the full suite on every push · four scheduled cron services · nightly backups with a tested restore path.

[View project →](./projects/11-rooms-okc/)

---

### 10 — Candidate Pipeline Automation

A three-Zap Zapier system that automates the full CV intake-to-review cycle for a recruitment team.

**Zap 1 — Main Pipeline (18 steps):** A Typeform CV submission triggers the pipeline. Before creating any record, the Zap checks Airtable by email for a duplicate — updating on resubmission instead of creating a duplicate. Claude Sonnet receives the candidate's form fields and parses them into a structured JSON object (skills, seniority, role type, availability, profile summary) via a direct Anthropic API call. A Code step wraps the JSON.parse in a try/catch — parse failures set Status to `Needs Manual Review` rather than silently creating broken records. The candidate record is upserted to Airtable, then the pipeline looks up all open roles matching the candidate's role type. A second Code step computes a skill overlap score (0–100%) using substring matching across both lists. Paths by Zapier branches: a score ≥ 40% creates a ClickUp CV review task in the role's designated list and sets Airtable Status to `Shortlisted`; below the threshold sets Status to `Pooled`. Both paths converge — a neutral acknowledgement email fires for every candidate. The Zap then pauses 3 calendar days using Delay by Zapier, re-fetches the Airtable record to read the live Status (not the cached value), and sends a Slack DM to the recruiter if the record is still `Shortlisted` and `Reminder Sent = false`. A final Airtable update marks `Reminder Sent = true`.

**Zap 2 — Parse Error Handler:** Polls the Airtable `Needs Manual Review` view every 15 minutes. When a new record appears, it sends a Slack ops alert with the candidate name, email, and a direct Airtable link, then sets `Ops Alerted = true` to prevent duplicate alerts.

**Zap 3 — Weekly Pooled Digest:** Runs every Monday at 9am. Fetches all `Pooled` candidates and all roles opened in the past 7 days, runs the same skill overlap algorithm, and posts a ranked Slack digest to the recruitment channel — surfacing candidates who were pooled before a matching role existed.

**Impact:** Every CV submission is captured, parsed, scored, routed, and acknowledged within seconds — with no human triage required. Recruiters receive a ClickUp task for every relevant candidate and a Slack nudge if they haven't reviewed it within 3 days.

[View project →](./projects/10-candidate-pipeline/)

---

### 09 — Real Estate — Lead-to-Close Automation

A two-workflow n8n system covering the full real estate pipeline from first inquiry to closed deal.

**W1 — Lead Intake & Qualification (11 nodes):** An inbound webhook receives raw lead data from any capture form. A single Claude Opus 4.5 agent normalises the data, scores the lead 0–100, and generates all downstream content in one call. Qualified leads (score ≥ 70) get a high-priority ClickUp task, an AI-written comment, a branded HTML welcome email, a 30-minute Google Calendar discovery call booked for the next business day, and a Slack agent alert. Nurture leads get a normal-priority ClickUp task due in 14 days and a value-first follow-up email.

**W2 — Transaction Launch (27 nodes):** Fires the moment a deal is marked Won in ClickUp. Claude Sonnet generates a complete structured project plan — Drive folder name, 5 subfolder names, a 3-section ClickUp board with tasks and due dates, a branded client welcome email, an internal project brief, and a Slack message. The workflow executes that plan in parallel: Google Drive folders and subfolders, ClickUp board with lists and seeded tasks, conditional client email (guarded for missing addresses), internal brief with a live Drive link, and Slack team alert. Full idempotency on re-runs — no duplicate folders or lists regardless of how many times the workflow fires.

**Impact:** A lead goes from form submission to CRM-routed + calendar-booked in seconds. A won deal goes from status change to fully provisioned client project in under 60 seconds — no manual work at either end of the pipeline.

[View project →](./projects/09-real-estate-lead-to-close/)

---

### 08 — Weekly KPI Summary — Wellness Practice

A single n8n workflow that delivers an automated weekly business intelligence report to a solo acupuncture practitioner every Monday morning. Three Airtable tables (Business Tracker, Ads Tracker, Social Posts) are fetched in parallel via a fan-out/merge pattern. A JavaScript Code node handles all date-range filtering and KPI aggregation — revenue, clients, hours worked, revenue per hour, ad spend by channel, and social posts by platform — with week-over-week comparisons. KPI data is passed to Claude Sonnet via OpenRouter, which writes 3–5 specific, data-driven business insights. A second Code node renders a fully branded HTML email. Smart alerting fires a separate email when revenue drops sharply, data gaps are detected, or performance falls below benchmarks. A weekly snapshot is also written back to Airtable for historical tracking.

**Impact:** The practitioner opens her inbox every Monday to a complete picture of her practice — no spreadsheets, no manual number-pulling, no analyst.

[View project →](./projects/08-hackensack-weekly-kpi/)

---

### 07 — AI Law Firm Receptionist

An 8-workflow autonomous receptionist stack for law firms. An AI triage agent classifies every inbound enquiry by intent and urgency, then dispatches to specialist sub-workflows: new client intake creates a Clio contact and matter; appointment scheduling sends clickable booking emails and auto-creates Zoom meetings; a parallel conflict-of-interest checker searches Clio for name and email matches; document generation drafts engagement letters and intake questionnaires; billing pulls outstanding Clio invoices and time entries into a branded HTML summary. All client-facing emails use a consistent branded HTML template. Attorneys receive Slack alerts for emergencies, new clients, and outstanding balances, plus an 8am morning digest of overnight messages.

**Impact:** A solo attorney or small firm can handle 3× the enquiry volume with zero reception staff — and no client message goes unanswered, even at 2am.

[View project →](./projects/07-law-firm-receptionist/)

---

### 06 — WhatsApp Event Registration System

A complete event management pipeline over WhatsApp. Ingests event details from a PDF, runs a conversational registration flow, verifies payment screenshots using **OpenAI Vision**, assigns bus seats from an Airtable inventory, and sends automated reminders before the event.

**Impact:** Replaces a manual registration desk with a fully automated system handling hundreds of attendees.

[View project →](./projects/06-whatsapp-event-registration/)

---

### 05 — Multi-Agent Personal Assistant

A sophisticated n8n orchestration system with specialized sub-agents for email triage (Gmail), calendar management (Google Calendar), CRM updates (HubSpot), SMS alerts (Twilio), and Telegram command handling. A central router agent interprets natural language requests and delegates to the right sub-agent.

**Impact:** A fully automated executive assistant that runs 24/7.

[View project →](./projects/05-multi-agent-personal-assistant/)

---

### 04 — Vapi Customer Support Agent

**Alex** — a voice AI customer support agent built on Vapi for CreekSoftware. Handles inbound support calls, resolves Tier-1 issues using a dynamic FAQ knowledge base, and escalates complex cases to human agents with a full call summary.

**Impact:** Deflects 60–70% of support calls without human intervention.

[View project →](./projects/04-vapi-customer-support/)

---

### 03 — Vapi Real Estate Booking Agent

**Stevenson** — a voice AI agent built on Vapi for Maplecrest Realty. Handles inbound property inquiries over the phone: answers questions about listings, captures prospect details via structured data extraction, and books property viewings directly into the agent's calendar via an n8n webhook.

**Impact:** A always-on receptionist that converts cold calls into booked viewings.

[View project →](./projects/03-vapi-real-estate-booking/)

---

### 02 — WhatsApp Lead Agent

An n8n workflow that connects to a Twilio WhatsApp number and runs a conversational AI lead qualification flow. The agent asks structured discovery questions, scores the lead, and either books a call or routes to a CRM pipeline — all within a WhatsApp thread.

**Impact:** Qualifies inbound leads instantly without a human sales rep.

[View project →](./projects/02-whatsapp-lead-agent/)

---

### 01 — Google Review Responder

A production n8n multi-agent system that monitors Google My Business for new reviews and automatically crafts professional responses. It routes reviews through a **Text Classifier agent** to detect sentiment, then dispatches to either a **Positive Review agent** or **Negative Review agent**. A **Revision agent** performs a final quality check before posting.

**Impact:** Zero manual review management. Every review gets a response within 5 minutes, 24/7.

[View project →](./projects/01-google-review-responder/)

---

## Tech Stack Overview

![Tech Stack](./assets/tech_stack_mindmap_v2.svg)

---

## Repository Structure

```
automation-portfolio/
├── projects/
│   ├── 01-google-review-responder/
│   ├── 02-whatsapp-lead-agent/
│   ├── 03-vapi-real-estate-booking/
│   ├── 04-vapi-customer-support/
│   ├── 05-multi-agent-personal-assistant/
│   ├── 06-whatsapp-event-registration/
│   ├── 07-law-firm-receptionist/
│   ├── 08-hackensack-weekly-kpi/
│   ├── 09-real-estate-lead-to-close/
│   ├── 10-candidate-pipeline/
│   └── 11-rooms-okc/
├── templates/
│   └── workflow-readme-template.md
├── .github/
│   ├── CONTRIBUTING.md
│   └── ISSUE_TEMPLATE/bug_report.md
└── LICENSE
```

---

## License

MIT — see [LICENSE](./LICENSE) for details.

---

*Built with care by [Evance Chapuma](https://www.upwork.com/freelancers/evancechapuma)*

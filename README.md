<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                    SAKTHIVEL MADHU · GITHUB PROFILE            -->
<!-- ═══════════════════════════════════════════════════════════════ -->

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:2d1065,100:0d1117&height=200&section=header&text=Sakthivel%20Madhu&fontSize=52&fontColor=e8e6f3&fontAlignY=42&desc=Backend%20Engineer%20·%20Building%20Production%20LLM%20Agents&descAlignY=62&descSize=17&descColor=a78bfa&animation=fadeIn" width="100%"/>

<div align="center">

<img src="./assets/profile.jpg" width="128" height="128" style="border-radius:50%;object-fit:cover;border:3px solid #7c3aed;" alt="Sakthivel Madhu"/>

<br/><br/>

<a href="https://sakthivelmadhu.github.io/"><img src="https://img.shields.io/badge/🌐_Portfolio-7C3AED?style=flat-square&labelColor=0d1117"/></a>&nbsp;
<a href="https://www.linkedin.com/in/sakthivel-madhu-864647238/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white"/></a>&nbsp;
<a href="mailto:sakthi130597@gmail.com"><img src="https://img.shields.io/badge/Gmail-EA4335?style=flat-square&logo=gmail&logoColor=white"/></a>&nbsp;
<a href="https://leetcode.com/u/sakthi130597"><img src="https://img.shields.io/badge/LeetCode-FFA116?style=flat-square&logo=leetcode&logoColor=black"/></a>&nbsp;
<a href="https://drive.google.com/file/d/1rLtlLlLSBEiQulypJezq-kmwUfeK5qNW/view?usp=sharing"><img src="https://img.shields.io/badge/Resume-22c55e?style=flat-square"/></a>

<br/><br/>

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=17&duration=3200&pause=1400&color=A78BFA&center=true&vCenter=true&width=620&height=28&lines=Java+%2F+Spring+Boot+backend+engineer+%7C+3%2B+years;Shipping+production+multi-agent+LLM+systems+since+2025;92%25+manual-entry+eliminated+%7C+real+users%2C+real+scale" alt="Typing SVG"/>

<br/>

<sub>📍 Bangalore, India &nbsp;·&nbsp; 🟢 Open to work &nbsp;·&nbsp; 🏆 Employee of the Quarter</sub>
&nbsp;&nbsp;
<img src="https://komarev.com/ghpvc/?username=SakthivelMadhu&color=7c3aed&style=flat-square&label=profile+views"/>

</div>

<br/>

I'm a backend engineer at **Twinleaves Retail Ecommerce**, where I own procurement, finance, and HR platforms end-to-end — and, most recently, built the company's first production **LLM agent**. I like systems that remove a human from a task they shouldn't have to do by hand, and I like being able to explain *why* the system made the decision it made, not just that it did.

<br/>

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                      FEATURED PROJECT                          -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🤖&nbsp; Featured — Purchase AI Agent

<table>
<tr><td>

**Invoice-to-GRN Automation**, built with Java, Spring Boot, Google's Agent Development Kit, and Gemini 2.5.

An agent that turns a photographed vendor invoice into a completed Goods Receipt Note — extracting, matching, and validating data that used to require manual entry. A user uploads a photo or PDF of an invoice and asks the assistant to create a GRN; the agent reads the invoice with Gemini's multimodal vision, resolves the vendor's identity, matches every line item against the product catalog, flags anything uncertain for human review, and — once confirmed — creates the GRN directly against the company's purchase and inventory systems.

</td></tr>
</table>

**What it does**

- 📸 **Invoice extraction from a photo/PDF** — no manual typing of vendor, items, quantities, or prices
- 🏢 **Automatic vendor resolution** — validates GST/PAN, looks up existing vendors, or creates new ones
- 🎯 **Deterministic product matching** — scores catalog candidates across five priority tiers (barcode, vendor item code, HSN code, fuzzy name match, brand/variant), so match confidence is reproducible and auditable, not just an LLM guess
- 👀 **Human-in-the-loop review** — streams live checkpoints (vendor info, matched items, order summary) to the UI so the user can correct anything before it's committed
- 🛑 **Validation before commit** — blocks GRN creation on missing/unresolved data (unmatched vendor, missing pricing, unresolved product line) while surfacing non-blocking warnings, e.g. invoice-total mismatch
- 🔁 **Full lifecycle handling** — including raising a Purchase Indent first if preferred, and processing returns for rejected items

**How it's built**

| | |
|---|---|
| **Orchestration** | A coordinator agent routes requests to a dedicated Purchase AI Agent, which delegates sub-tasks (catalog search, new product creation) to specialized sub-agents via tool-calling — each agent stays focused, and token usage is tracked per agent |
| **OCR** | Gemini's multimodal vision reads the invoice directly — no separate document-extraction service |
| **Catalog search** | Agents don't search the catalog themselves — they compose structured query/filter objects executed against an Elasticsearch-backed catalog service, keeping retrieval fast and results explainable |
| **Matching logic** | Runs as plain, testable Java code, not model inference — so confidence scores stay consistent and can be safely gated on |
| **Real-time UX** | Server-Sent Events stream progress and intermediate results to the frontend as the agent works |
| **Integration** | Talks to independent Vendor, Purchase Order, Inventory, and Catalog microservices over REST rather than owning that data itself |

> **A problem worth mentioning:** early testing surfaced a real data-quality issue — fuzzy name-matching alone occasionally matched unrelated products at high confidence (e.g. a soft drink matching flavored water). Tuning the similarity threshold numerically couldn't reliably separate genuine near-duplicates from wrong matches, so instead I added a semantic sanity-check step where the agent itself verifies a match makes sense before trusting it, backed by regression tests documenting the original failure cases.

**Stack:** `Java` `Spring Boot` `Google Agent Development Kit` `Gemini 2.5 Pro/Flash` `Elasticsearch` `REST APIs` `Server-Sent Events` `Google Cloud Storage` `BigQuery` `JUnit`

**My role:** designed and implemented the agent end-to-end — extraction pipeline, deterministic product-matching engine, agent orchestration/routing, and integration with downstream purchase/vendor/inventory services — plus the unit test suite covering the new logic.

<br/>

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                    OTHER PLATFORMS                              -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🏗️&nbsp; Other Platforms I've Built

<sub>Production systems handling real money, real vendors, real employees — every day, at Twinleaves.</sub>

<br/>

<table>
<tr>
<td width="50%" valign="top">

**🧾 Purchase Order Management & ERP**
Full purchase lifecycle — PR → PO → GRN, billing, payments, returns, inter-company workflows. Built **Express Purchase** (combined PO + GRN + put-away) and Doc-AI invoice extraction.
<br/><br/>
`92%` manual entry eliminated · `80%` faster onboarding
<br/>
`Java 17` `Spring Boot` `Doc-AI` `PostgreSQL` `Pub/Sub`

</td>
<td width="50%" valign="top">

**💰 Finance & Banking System** <sub>(Pallet Books)</sub>
A Zoho Books/Tally-style platform built from scratch — ledgers, purchase accounting, real-time bank reconciliation, and Elasticsearch-powered ledger search.
<br/><br/>
`~50ms` search response · `95%` statement extraction accuracy
<br/>
`Spring Cloud` `Elasticsearch` `Redis` `BigQuery`

</td>
</tr>
<tr>
<td width="50%" valign="top">

**👥 HRMS — Facial Recognition & AI Payroll**
Attendance via facial recognition and GPS geo-fencing, feeding an automated payroll engine that computes LOP, overtime, and compliance without manual HR work.
<br/><br/>
`~10m` geo-fence precision · `100%` payroll automated
<br/>
`Spring Security` `OpenCV` `MySQL` `Pub/Sub`

</td>
<td width="50%" valign="top">

**🏭 Vendor Management & Compliance**
Centralized vendor onboarding with real-time GST/PAN/bank verification across 5+ government APIs, plus a configurable Terms-of-Trade rules engine.
<br/><br/>
`5+` government APIs automated · `100%` verification automated
<br/>
`API Gateway` `OAuth 2.0` `MongoDB` `Microservices`

</td>
</tr>
</table>

<br/>

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                      WORK HISTORY                               -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 💼&nbsp; Work History

<br/>

**Software Development Engineer** — Twinleaves Retail Ecommerce &nbsp;·&nbsp; *May 2024 – Present* &nbsp;·&nbsp; 📍 Bangalore
Full technical ownership of 4 production platforms (Purchase & ERP, Finance, HRMS, Vendor Management) plus the company's Purchase AI Agent. Architected microservices with high-throughput REST APIs, fault-tolerant async workflows on GCP Pub/Sub, CI/CD (GitHub Actions, Jenkins), and Elasticsearch-backed search. Mentored junior engineers via code review and pairing.

**Full Stack Web Developer** — Masai School &nbsp;·&nbsp; *Jul 2022 – Jul 2023* &nbsp;·&nbsp; 📍 Remote
2,160+ hours of intensive full-stack and backend training. Shipped 3+ production-style apps, including a Naukri clone and a real-time bidding Auction System, on Java, Spring Boot, Hibernate, and MySQL.

**Associate Software Engineer** — EFI Pvt. Ltd. &nbsp;·&nbsp; *Oct 2020 – Mar 2021* &nbsp;·&nbsp; 📍 Bangalore
Delivered 3+ feature modules for the Fiery product (C++, SQL) across two stable production releases, working closely with QA and business stakeholders.

<br/>

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                       TECH STACK                                -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🧰&nbsp; Tech Stack

<div align="center">

[![Skills](https://skillicons.dev/icons?i=java,spring,hibernate,gcp,docker,kubernetes,postgres,mysql,mongodb,redis,elasticsearch,python,nodejs,js,react,git,github,linux&theme=dark&perline=9)](https://skillicons.dev)

</div>

<br/>

| | |
|---|---|
| **AI / LLM Agents** | Google Agent Development Kit (ADK) · Gemini 2.5 (Pro/Flash) · Multi-Agent Orchestration · Tool-Calling · Multimodal Document Extraction · Prompt Engineering |
| **Backend** | Java 17 · Spring Boot · Spring Security · Spring Cloud · REST APIs · Microservices · Hibernate/JPA · Event-Driven Architecture |
| **Cloud & DevOps** | GCP · Docker · Kubernetes · GitHub Actions · Jenkins · Linux |
| **Data & Messaging** | PostgreSQL · MySQL · MongoDB · BigQuery · Elasticsearch · Redis · GCP Pub/Sub |
| **Security** | JWT · OAuth 2.0 · API Gateway · RBAC |
| **Domain** | ERP / Procurement · FinTech / Accounting · HRMS / Payroll · Vendor Compliance · E-Invoicing |

<br/>

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                    GITHUB ANALYTICS                             -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 📊&nbsp; GitHub Analytics

<div align="center">

<img height="165" src="https://github-readme-stats.vercel.app/api?username=SakthivelMadhu&show_icons=true&hide_border=true&count_private=true&include_all_commits=true&bg_color=0d1117&title_color=c084fc&icon_color=a78bfa&text_color=8b9caf&ring_color=7c3aed" />&nbsp;
<img height="165" src="https://github-readme-streak-stats.herokuapp.com/?user=SakthivelMadhu&hide_border=true&background=0d1117&ring=7c3aed&fire=c084fc&currStreakLabel=a78bfa&sideLabels=a78bfa&dates=6b7280&stroke=1e1b4b&currStreakNum=c084fc&sideNums=a78bfa" />

<br/>

<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=SakthivelMadhu&layout=donut&hide_border=true&bg_color=0d1117&title_color=c084fc&text_color=8b9caf&langs_count=8" />&nbsp;
<img height="165" src="https://leetcode-stats-card.vercel.app/card/?username=sakthi130597&theme=dark&border=7c3aed&bg=0d1117&text=c084fc&circle=7c3aed"/>

<br/><br/>

[![Trophy](https://github-profile-trophy.vercel.app/?username=SakthivelMadhu&theme=discord&no-frame=true&no-bg=true&column=7&margin-w=6&margin-h=6)](https://github.com/ryo-ma/github-profile-trophy)

</div>

<br/>

### 📈 Contribution Activity

<div align="center">

[![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=SakthivelMadhu&theme=react-dark&hide_border=true&bg_color=0d1117&color=c084fc&line=7c3aed&point=a78bfa&area=true&area_color=5b21b6)](https://github.com/ashutosh00710/github-readme-activity-graph)

</div>

### 🌐 3D Contribution Calendar

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./profile-3d-contrib/profile-night-rainbow.svg" />
  <source media="(prefers-color-scheme: light)" srcset="./profile-3d-contrib/profile-night-rainbow.svg" />
  <img alt="3D Contribution Calendar" src="./profile-3d-contrib/profile-night-rainbow.svg" width="100%" />
</picture>

</div>

### 🐍 Contribution Snake

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/SakthivelMadhu/SakthivelMadhu/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/SakthivelMadhu/SakthivelMadhu/output/github-contribution-grid-snake.svg" />
  <img alt="Snake animation" src="https://raw.githubusercontent.com/SakthivelMadhu/SakthivelMadhu/output/github-contribution-grid-snake-dark.svg" />
</picture>

</div>

<br/>

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                CERTIFICATIONS & RECOGNITION                     -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🏆&nbsp; Certifications & Recognition

<table>
<tr>
<td align="center" width="33%">

**🏆 Employee of the Quarter**
<sub>Twinleaves Retail Ecommerce</sub>
<br/><sub><i>High-impact engineering across ERP, HRMS, and Finance</i></sub>
<br/><code>2024</code>
<br/><a href="https://drive.google.com/file/d/1uu_cF3-hacTCve8xITkrSTivhXP8U5jS/view?usp=drive_link">View certificate ↗</a>

</td>
<td align="center" width="33%">

**🤖 Prompt Engineering for Devs**
<sub>DeepLearning.AI × OpenAI</sub>
<br/><sub><i>LLM API integration patterns for production Java systems</i></sub>
<br/><code>2024</code>
<br/><a href="https://drive.google.com/file/d/1WxbYa7Iwbv7RLjo5zRuZmZDiBGacOShI/view?usp=sharing">View certificate ↗</a>

</td>
<td align="center" width="33%">

**🐍 Python Programming**
<sub>Apponix Training Center</sub>
<br/><sub><i>Core Python, OOP, scripting & automation</i></sub>
<br/><code>2023</code>
<br/><a href="https://drive.google.com/file/d/1WwUrLLHI4uib6dqFcEVzrL0e1spKFdZi/view?usp=sharing">View certificate ↗</a>

</td>
</tr>
</table>

<br/>

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                  OPEN SOURCE & EARLIER PROJECTS                 -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🗂️&nbsp; Open Source & Earlier Projects

<div align="center">

<a href="https://github.com/masai-builds/TeamiplyBackend">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=masai-builds&repo=TeamiplyBackend&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=c084fc&icon_color=a78bfa&text_color=8b9caf" width="47%"/>
</a>&nbsp;&nbsp;
<a href="https://github.com/SakthivelMadhu/Automated_Auction_System">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=SakthivelMadhu&repo=Automated_Auction_System&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=c084fc&icon_color=a78bfa&text_color=8b9caf" width="47%"/>
</a>

<a href="https://github.com/SakthivelMadhu/Clone-Naukri">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=SakthivelMadhu&repo=Clone-Naukri&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=c084fc&icon_color=a78bfa&text_color=8b9caf" width="47%"/>
</a>&nbsp;&nbsp;
<a href="https://github.com/SakthivelMadhu/Restaurant_management_system">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=SakthivelMadhu&repo=Restaurant_management_system&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=c084fc&icon_color=a78bfa&text_color=8b9caf" width="47%"/>
</a>

<a href="https://github.com/SakthivelMadhu/Job_Matching_System">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=SakthivelMadhu&repo=Job_Matching_System&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=c084fc&icon_color=a78bfa&text_color=8b9caf" width="47%"/>
</a>&nbsp;&nbsp;
<a href="https://github.com/SakthivelMadhu/Library-Management-System">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=SakthivelMadhu&repo=Library-Management-System&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=c084fc&icon_color=a78bfa&text_color=8b9caf" width="47%"/>
</a>

</div>

<br/>

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                     BEYOND THE CODE                              -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🏍️&nbsp; Beyond the Code

<div align="center">

<sub>🏍️ Royal Enfield rider &nbsp;·&nbsp; 🏊 Swimmer &nbsp;·&nbsp; 🧠 Daily LeetCode &nbsp;·&nbsp; 🍜 Bangalore food explorer &nbsp;·&nbsp; 🍳 Cooking</sub>

</div>

<br/>

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                        CONTACT                                  -->
<!-- ═══════════════════════════════════════════════════════════════ -->

<div align="center">

## 🤝&nbsp; Let's Build Something

Open to **Backend / Platform / AI-Agent Engineering** roles — FinTech, HRTech, ERP/Enterprise SaaS, and AI-powered platforms.

<br/>

<a href="mailto:sakthi130597@gmail.com"><img src="https://img.shields.io/badge/✉️_sakthi130597@gmail.com-7C3AED?style=for-the-badge&logoColor=white" height="45"/></a>&nbsp;
<a href="https://www.linkedin.com/in/sakthivel-madhu-864647238/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" height="45"/></a>&nbsp;
<a href="https://sakthivelmadhu.github.io/"><img src="https://img.shields.io/badge/Portfolio-0d1117?style=for-the-badge&logoColor=white" height="45"/></a>&nbsp;
<a href="https://drive.google.com/file/d/1rLtlLlLSBEiQulypJezq-kmwUfeK5qNW/view?usp=sharing"><img src="https://img.shields.io/badge/Resume-22c55e?style=for-the-badge" height="45"/></a>

<br/><br/>

<sub>📍 Bangalore, India &nbsp;·&nbsp; 🌐 Available remotely &nbsp;·&nbsp; ⚡ Responds within 24h</sub>

</div>

<br/>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:2d1065,100:0d1117&height=100&section=footer" width="100%"/>

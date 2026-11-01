# 🔍 TraceLens AI — Cyberpunk OSINT & Digital Forensics Terminal

<div align="center">

<img src="./public/Octo-Icon.svg" alt="TraceLens AI Logo" width="120" />

### *Adaptive Forensic Investigation & Cyber Threat Intelligence Powered by Generative UI*

[![Next.js](https://img.shields.io/badge/Next.js-15.5-black?style=for-the-badge&logo=next.js&logoColor=white)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![Tambo AI](https://img.shields.io/badge/Tambo_AI-GenUI_SDK-7928CA?style=for-the-badge)](https://tambo.ai)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

<br/>

<p align="center">
  <a href="#-demo-preview">Video Demo</a> •
  <a href="#-overview">Overview</a> •
  <a href="#-key-features">Key Features</a> •
  <a href="#-architecture--generative-ui">Architecture & GenUI</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-getting-started">Getting Started</a> •
  <a href="#-api--tool-system">Tool System</a> •
  <a href="#-authors--acknowledgments">Authors</a>
</p>

</div>

---

## 📹 Demo Preview

<div align="center">

<!-- ============================================================ -->
<!-- STEP TO ADD YOUR VIDEO: Replace the URL or embed link below -->
<!-- ============================================================ -->

### 🌟 [Watch the TraceLens AI Walkthrough & Live Demo Video](https://www.youtube.com/watch?v=YOUR_DEMO_VIDEO_HERE)

[![TraceLens AI Demo Video Thumbnail](https://img.youtube.com/vi/YOUR_DEMO_VIDEO_HERE/maxresdefault.jpg)](https://www.youtube.com/watch?v=YOUR_DEMO_VIDEO_HERE)

> 💡 *Click the thumbnail above or [click here](https://www.youtube.com/watch?v=YOUR_DEMO_VIDEO_HERE) to watch the video demonstration.*
> 
> *(Replace `YOUR_DEMO_VIDEO_HERE` with your YouTube video ID, Loom, or Vimeo link).*

<br/>

</div>

---

## ⚡ Overview

**TraceLens AI** is an advanced digital forensics workstation and open-source intelligence (OSINT) terminal designed with a high-octane cyberpunk aesthetic. Built for modern cyber investigators and intelligence analysts, it models an interactive investigation room where the interface evolves dynamically in response to case discoveries.

Powered by **Tambo AI's Generative UI (GenUI)**, TraceLens solves the "dashboard overload" problem. Instead of cluttering investigators with static tables, charts, and graphs, TraceLens serves an intelligent conversational agent that dynamically mounts interactive components—such as dynamic **React Flow Evidence Graphs**, **Incident Timelines**, and **Breach Audits**—exactly when and where the investigation demands it.

---

## ✨ Key Features

### 🕵️‍♂️ Autonomous OSINT Scanner
- **Target Footprinting**: Conducts rapid intelligence scans across usernames, emails, aliases, and IP addresses.
- **Social Profile Reconnaissance**: Cross-references real-time search queries (powered by Serper.dev / Google Custom Search) across platforms like GitHub, X/Twitter, LinkedIn, Instagram, and Reddit.
- **Threat & Risk Scoring**: Automated risk-weighting engine evaluating suspect exposure, breached accounts, and network footprints.

### 🧠 Generative UI with Tambo AI
- **Dynamic Component Mounting**: The AI Assistant inspects intent and streams interactive visual components directly into the chat thread or active caseboard.
- **On-Demand Evidence Graph**: Natural language requests like *"Show me the suspect's connection to the compromised IP"* trigger an interactive, draggable **React Flow** network graph.
- **Chronological Timeline View**: Unravels multi-hop attack timelines with event categorization, timestamps, and severity badges.

### 🛡️ Forensic Chain of Custody & Security
- **Immutable Evidence Records**: SHA-256 cryptographic verification ensuring evidence integrity throughout investigation lifecycles.
- **Compromise & Breach Detection**: Inspects whether suspect identifiers correlate with compromised databases or credential dumps.
- **One-Click Dossier Export**: Generate and download comprehensive, court-ready PDF and JSON forensic reports (using jsPDF & html2canvas).

### 💻 Immersive Cyberpunk Terminal UI
- High-contrast tactical dark mode with neon accents (Cyan, Emerald, Amber, Crimson).
- Fluid micro-interactions and decrypt/scramble animations powered by **Framer Motion**.
- Real-time reactive data updates and streamlined investigation history management.

---

## 🏗 Architecture & Generative UI

```mermaid
flowchart TD
    User([Investigator / Analyst])

    subgraph Client ["Frontend: Next.js 15 (App Router)"]
        Terminal[Cyberpunk Terminal UI]
        Chat[Tambo Assistant Thread]
        GenUIHost[Generative UI Viewport]
        
        subgraph MountedComponents ["Dynamic GenUI Components"]
            EvGraph[EvidenceGraph (React Flow)]
            Timeline[TimelineView Component]
            BreachList[BreachDetails Component]
            RiskGauge[RiskScore Meter]
        end
    end

    subgraph TamboCore ["Tambo AI Engine"]
        TamboProvider[TamboProvider & Registry]
        ToolRouter[Tambo Tool Dispatcher]
        LLMStream[Generative UI Streaming Engine]
    end

    subgraph BackendServices ["Backend / Forensic Engines"]
        ScanTool[OSINT Scanner (Serper API)]
        BreachTool[Breach & Credential Inspector]
        GraphTool[Evidence Node-Link Generator]
        CaseDB[(Local DB / Case Memory)]
    end

    User -->|Prompt: 'Show evidence graph'| Chat
    Chat --> TamboProvider
    TamboProvider --> LLMStream
    LLMStream --> ToolRouter

    ToolRouter -->|Invoke| ScanTool
    ToolRouter -->|Invoke| BreachTool
    ToolRouter -->|Invoke| GraphTool

    GraphTool --> CaseDB
    ScanTool --> CaseDB

    LLMStream -->|Stream Component Specs| GenUIHost
    GenUIHost --> EvGraph
    GenUIHost --> Timeline
    GenUIHost --> BreachList
    GenUIHost --> RiskGauge
```

### How Generative UI Works in TraceLens
1. **Clean Baseline**: The investigation workspace starts clutter-free, focusing on primary suspect stats.
2. **Intent Parsing**: The investigator types naturally: *"Analyze the correlation between the darknet handle and the reported corporate email."*
3. **Tool Invocation**: Tambo calls registered tools (`scanTarget`, `getEvidenceGraph`, `getCaseDetails`) defined in `lib/tambo.ts` with strict Zod validation schemas.
4. **Adaptive Rendering**: Tambo streams the corresponding UI components into the view, pre-hydrated with live investigation nodes, threat vectors, and connection links.

---

## 🛠 Tech Stack

| Domain | Technology | Purpose |
|---|---|---|
| **Core Framework** | **Next.js 15 (App Router)** | High-performance React framework with server/client boundaries |
| **Language** | **TypeScript 5** | Strict end-to-end type safety |
| **Generative UI** | **@tambo-ai/react & SDK** | Dynamic component registration, tools, and GenUI streaming |
| **Styling & Theme** | **Tailwind CSS v4** | Cyberpunk design system, responsive utility styling |
| **Animations** | **Framer Motion 12** | Decryption text effects, slick panel transitions, terminal scanlines |
| **Network Visualization** | **React Flow 11** | Interactive, draggable node-link evidence graphs |
| **Data Visualization** | **Recharts 3** | Threat distribution charts and severity metrics |
| **OSINT Search** | **Serper.dev API** | Real-time social footprint scraping and Google search extraction |
| **Export Engines** | **jsPDF & html2canvas** | Automated client-side PDF forensic dossier creation |
| **Icons & Typography** | **Lucide React** | Tactical iconography |

---

## 📂 Project Structure

```text
tracelens-ai/
├── app/
│   ├── about/                 # Platform mission & technology overview
│   ├── api/                   # Next.js Serverless Route Handlers
│   │   ├── cases/             # Case history CRUD & retrieval
│   │   ├── chat/              # Chat endpoint handlers
│   │   ├── investigate/       # Deep OSINT intelligence scan worker
│   │   └── report/            # Report compilation API
│   ├── case/                  # Active investigation caseboard
│   ├── dashboard/             # Main threat intelligence command hub
│   ├── history/               # Archive of prior forensic cases
│   ├── report/                # Forensic dossier view & PDF export page
│   ├── globals.css            # Cyberpunk aesthetic variables & scanline effects
│   ├── layout.tsx             # Root layout with TamboProvider context
│   └── page.tsx               # Terminal landing page with decrypt animation
├── components/
│   ├── forensics/             # Specialized Forensic GenUI Components
│   │   ├── EvidenceGraph.tsx  # React Flow node-link relationship diagram
│   │   └── TimelineView.tsx   # Chronological incident progression tracker
│   └── tambo/                 # Tambo GenUI integrations & chat widgets
│       └── tamboRegistry.ts   # Component catalog exposed to AI
├── lib/
│   ├── data/                  # Seed datasets & investigation mock feeds
│   ├── db/                    # Case storage & persistent state
│   ├── forensics/             # Forensic analysis & tool implementations
│   │   └── forensicTools.ts   # Zod-typed tools (scanTarget, getEvidenceGraph)
│   ├── osint/                 # Serper API integration & footprint scrapers
│   └── tambo.ts               # Central Tambo tools & components configuration
├── public/                    # SVG badges, brand assets, and icons
├── example.env.local          # Template environment configuration
├── package.json               # Project dependencies & scripts
├── tailwind.config.ts         # Tailwind theme customizations
└── tsconfig.json              # TypeScript compilation setup
```

---

## 🚀 Getting Started

### Prerequisites

Ensure you have installed:
- **Node.js**: v18.17.0 or higher (Node 20+ recommended)
- **npm**, **pnpm**, or **yarn**
- API Keys:
  - [Tambo AI API Key](https://tambo.ai) *(for Generative UI and assistant intelligence)*
  - [Serper.dev API Key](https://serper.dev) *(for live OSINT social scraping)*

---

### Step 1: Clone the Repository

```bash
git clone https://github.com/AP952005/tracelens-ai.git
cd tracelens-ai
```

### Step 2: Install Dependencies

```bash
npm install
```

### Step 3: Configure Environment Variables

Create a `.env.local` file in the root directory:

```bash
cp example.env.local .env.local
```

Add your keys to `.env.local`:

```env
# Tambo AI Configuration
NEXT_PUBLIC_TAMBO_API_KEY=your_tambo_api_key_here
NEXT_PUBLIC_TAMBO_URL=https://api.tambo.ai

# OSINT Search API
SERPER_API_KEY=your_serper_api_key_here
```

### Step 4: Run the Development Server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 🕹️ Investigation Walkthrough

1. **Initialize Terminal**: From the landing page, hit **INITIALIZE TERMINAL** to launch the dashboard.
2. **Launch a Target Scan**: Enter any identifier (e.g., a username like `darkwolf_007`, an email, or a domain) to trigger an automated OSINT reconnaissance scan.
3. **Analyze Findings**: Review discovered social media footprints, estimated threat levels, and breach exposure.
4. **Command the Tambo Assistant**:
   - *"Show me the evidence graph for this target."*
   - *"Highlight connections between the suspect and compromised database breaches."*
   - *"Generate the chronological incident timeline."*
5. **Export Case Dossier**: Click **Export Report** to package evidence into a verified forensic PDF with cryptographic hash timestamps.

---

## ⚙️ Tool & Component System

TraceLens registers custom tools and UI components using Tambo's schema-first design:

| Tool / Component | Type | Description |
|---|---|---|
| `scanTarget` | **Tool** | Queries OSINT feeds and search index for social profiles, emails, and threats |
| `getCaseDetails` | **Tool** | Retrieves full contextual metadata of an active case by ID |
| `getEvidenceGraph` | **Tool** | Generates node-link relationship graphs between entities |
| `EvidenceGraph` | **Component** | Interactive React Flow canvas displaying suspect-to-asset linkages |
| `TimelineView` | **Component** | Visual chronometer displaying timestamped security incidents |

---

## 👤 Author & Acknowledgments

**Abishek Palani**
- **GitHub**: [@AP952005](https://github.com/AP952005)
- **LinkedIn**: [in/ap9505](https://www.linkedin.com/in/ap9505)
- **Organization**: AP Solutions

Built with ❤️ for the **Tambo AI Generative UI Hackathon**.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

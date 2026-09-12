Here is the completely redesigned README in raw Markdown format, entirely in English. You can click the **"Copy code"** button in the top-right corner of the block below to paste it directly into your `README.md` file:

```markdown
<div align="center">
  <h1>🏗️ Ghost Arc</h1>
  <h3>AI-Powered Collaborative System Architect</h3>
  <p>An agentic planning application built for software teams to collaboratively design, visualize, and generate technical specifications for complex systems in real-time.</p>

  <div>
    <img src="https://img.shields.io/badge/-Next.js-black?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js" />
    <img src="https://img.shields.io/badge/-Typescript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
    <img src="https://img.shields.io/badge/-Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" alt="Tailwind CSS" />
    <img src="https://img.shields.io/badge/-shadcn/ui-000000?style=for-the-badge&logo=shadcnui&logoColor=white" alt="shadcn/ui" /><br/>
    <img src="https://img.shields.io/badge/-Prisma-2D3748?style=for-the-badge&logo=prisma&logoColor=white" alt="Prisma" />
    <img src="https://img.shields.io/badge/-PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
    <img src="https://img.shields.io/badge/-Clerk-6C47FF?style=for-the-badge&logo=clerk&logoColor=white" alt="Clerk" /><br/>
    <img src="https://img.shields.io/badge/Trigger.dev-22c55e?style=for-the-badge&logo=triggerdotdev&logoColor=white" alt="Trigger.dev" />
    <img src="https://img.shields.io/badge/-Liveblocks-050505?style=for-the-badge&logo=liveblocks&logoColor=white" alt="Liveblocks" />
    <img src="https://img.shields.io/badge/-Google_Gemini-8E75B2?style=for-the-badge&logo=google&logoColor=white" alt="Gemini" />
  </div>
</div>

---

## 📋 Table of Contents
1. [Introduction](#-introduction)
2. [Features](#-features)
3. [Tech Stack](#-tech-stack)
4. [Quick Start](#-quick-start)
5. [Available Scripts](#-available-scripts)
6. [Project Structure](#-project-structure)

## ✨ Introduction
Ghost Arc is an interactive systems architecture builder powered by AI. A user submits a natural-language prompt, and a Google Gemini-powered AI agent autonomously places nodes and edges onto a shared React Flow canvas in real-time. Human teammates can watch the AI build the diagram live and jump in to collaboratively refine it. 

Once the team is satisfied, a secondary AI background task converts the visual graph into a comprehensive, multi-page Markdown technical specification that can be directly downloaded from the app.

## 🔋 Features
- **AI Architecture Agent:** Submit a plain-English prompt, and Gemini draws nodes/edges onto the live canvas in real-time via Trigger.dev background tasks.
- **Multiplayer Canvas:** Full real-time collaboration powered by Liveblocks (synchronized state, live cursor positions, and presence avatars).
- **Custom Canvas Nodes:** Inline label editing, resizing with NodeResizer, and custom color swatches via a floating NodeToolbar.
- **AI Spec Generation:** One-click conversion of the visual graph into a detailed Markdown technical specification.
- **Auto-Save & Storage:** The canvas state auto-saves (debounced) every 3 seconds. Metadata is stored securely in PostgreSQL using Prisma.
- **Authentication:** Secure user management and route protection powered by Clerk.

## ⚙️ Tech Stack
- **Framework:** [Next.js](https://nextjs.org/) & [React](https://react.dev/)
- **Language:** [TypeScript](https://www.typescriptlang.org/)
- **Styling:** [Tailwind CSS](https://tailwindcss.com/) & [shadcn/ui](https://ui.shadcn.com/)
- **Database & ORM:** [PostgreSQL](https://www.postgresql.org/) & [Prisma](https://www.prisma.io/)
- **Authentication:** [Clerk](https://clerk.com/)
- **Collaboration:** [Liveblocks](https://liveblocks.io/)
- **Background Jobs:** [Trigger.dev](https://trigger.dev/)
- **AI Models:** [Google Gemini API](https://aistudio.google.com/)

## 🤸 Quick Start

Follow these steps to set up the project locally on your machine.

### Prerequisites
- Node.js (v18 or higher)
- npm or yarn
- Git

### 1. Clone the Repository
```bash
git clone [https://github.com/your-username/ghost-ai.git](https://github.com/your-username/ghost-ai.git)
cd ghost-ai

```

### 2. Install Dependencies

```bash
npm install

```

### 3. Set Up Environment Variables

Create a `.env` file in the root of your project and configure the following keys:

```env
# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up

# Liveblocks Collaboration
LIVEBLOCKS_SECRET_KEY=your_liveblocks_secret_key

# Trigger.dev Background Tasks
TRIGGER_SECRET_KEY=your_trigger_secret_key
NEXT_PUBLIC_TRIGGER_PUBLIC_API_KEY=your_trigger_public_key

# PostgreSQL Database (Neon.tech / Supabase)
DATABASE_URL="postgresql://user:password@host:port/db?sslmode=require"

# Google Gemini AI
GOOGLE_GENERATIVE_AI_API_KEY=your_gemini_api_key
GEMINI_MODEL=gemini-2.0-flash
GEMINI_SPEC_MODEL=gemini-2.0-flash

# Application URL
APP_URL=http://localhost:3000

```

### 4. Setup the Database

Sync your Prisma schema with your PostgreSQL database:

```bash
npx prisma db push
npx prisma generate

```

### 5. Run the Application

Start the Next.js development server:

```bash
npm run dev

```

### 6. Run Trigger.dev (Background Tasks)

In a **second terminal instance**, start the Trigger.dev worker so the AI generation tasks can execute locally:

```bash
npx trigger.dev@latest dev

```

Open [http://localhost:3000](http://localhost:3000) in your browser to view the app!

## 📜 Available Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start Next.js development server |
| `npm run build` | Build the application for production |
| `npm run start` | Start the production server |
| `npm run lint` | Run ESLint for code quality |
| `npx prisma db push` | Push schema changes to the database |
| `npx prisma studio` | Open the Prisma Studio GUI to view data |

## 📂 Project Structure

```text
.
├── app/                  # Next.js App Router (pages, API routes)
├── components/           # React components (editor, ui, sidebar)
├── data/                 # Local storage for canvas JSON & generated specs
├── hooks/                # Custom React hooks (auto-save, shortcuts)
├── lib/                  # Utilities (Prisma client, Liveblocks, AI configs)
├── prisma/               # Database schema
├── trigger/              # Trigger.dev background tasks for AI
└── types/                # TypeScript interfaces & types

```

---

**Developed and Maintained by Nipun Kushwaha**

```

<Elicitations message="Let me know if you need any further customizations:">
  <Elicitation label="Add my GitHub username" query="How do I add my actual GitHub username where it says 'your-username' in the clone link?"/>
  <Elicitation label="It looks good" query="Thank you, I've copied this file. I'll try running the project now."/>
</Elicitations>

```
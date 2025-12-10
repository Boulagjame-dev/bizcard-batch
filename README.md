# BizCard Batch

**Transform physical business cards into actionable digital contacts with AI.**

![BizCard Batch Banner](https://via.placeholder.com/1200x400?text=BizCard+Batch+AI)

## 🚀 The Working Idea

**BizCard Batch** is an intelligent web application designed to solve the chaos of business card collection. Instead of manually typing in details from dozens of cards collected at conferences or meetings, users can simply upload images—batches of cards at once—and let Gemini AI (Google's multimodal model) extract, structure, and save the data.

### Core Intelligence
At the heart of BizCard Batch is a specialized AI pipeline:
1.  **Image Ingestion**: Accepts individual or stitched images of business cards.
2.  **Multimodal Extraction**: Uses **Google Gemini 1.5 Pro** to "see" the card and extract fields (Name, Job Title, Company, Phone, Email, Address, Website) with high accuracy, even from creative or cluttered designs.
3.  **Smart Verification**: Flags low-confidence extractions for user review.
4.  **CRM Sync**: Exports clean data to CSV, HubSpot, or Salesforce (planned).

## 🛠 Tech Stack

Built with a modern, type-safe, and serverless-ready stack:

-   **Frontend**: [Next.js 15](https://nextjs.org/) (App Router, Server Components)
-   **Styling**: [Tailwind CSS](https://tailwindcss.com/) + [shadcn/ui](https://ui.shadcn.com/) (Premium UI)
-   **Database**: [Supabase](https://supabase.com/) (PostgreSQL + Auth + Realtime)
-   **AI Engine**: [Google Gemini API](https://ai.google.dev/) (OCR & Entity Extraction)
-   **Storage**: Supabase Storage (for card images)
-   **Language**: TypeScript

## 📂 Project Structure

```bash
bizcard-batch-core/
├── app/                # Next.js App Router
│   ├── api/            # Serverless API routes (webhook, AI processing)
│   ├── auth/           # Authentication pages (Supabase)
│   ├── dashboard/      # Main user interface
│   └── page.tsx        # Landing page
├── components/         # React components
│   ├── ui/             # Reusable UI primitives (buttons, cards)
│   └── bizcard/        # Domain-specific components (Scanner, Editor)
├── lib/
│   ├── supabase/       # Supabase client instantiation
│   └── gemini/         # Gemini AI processing logic
├── public/             # Static assets
└── types/              # TypeScript definitions
```

## ✨ Key Features (Planned/In-Progress)

-   [x] **Secure Authentication**: Magic Link & Google Sign-In via Supabase.
-   [ ] **Batch Processing**: Upload multiple card images simultaneously.
-   [ ] **AI Extraction**: Automatic field population using Gemini.
-   [ ] **Confidence Scoring**: Visual indicators for AI certainty.
-   [ ] **Manual Override**: Easy-to-use editor for correcting AI mistakes.
-   [ ] **Export Tools**: Download as `.vcf` or `.csv`.

## 🚀 Getting Started

### Prerequisites
-   Node.js 18+
-   npm or yarn
-   A **Supabase** project (free tier works great).
-   A **Google Cloud** project with Gemini API enabled.

### Installation

1.  **Clone the repository**:
    ```bash
    git clone https://github.com/Boulagjame-dev/bizcard-batch.git
    cd bizcard-batch
    ```

2.  **Install dependencies**:
    ```bash
    npm install
    # or
    yarn install
    ```

3.  **Environment Setup**:
    Copy the example environment file:
    ```bash
    cp .env.example .env.local
    ```
    Fill in your keys in `.env.local`:
    ```env
    NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
    NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
    GEMINI_API_KEY=your_gemini_api_key
    ```

4.  **Run Locally**:
    ```bash
    npm run dev
    ```
    Visit `http://localhost:3000`.

## 🤝 Contributing

We welcome contributions! Please check out `docs/CONTRIBUTING.md` (coming soon) for guidelines.

## 📄 License

MIT License. See `LICENSE` for details.

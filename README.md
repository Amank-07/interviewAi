## InterviewAI

An AI‑powered interview practice web app that generates tailored interview questions based on **job title**, **tech stack**, and **years of experience**, using Google’s **Gemini** models. Built with **Next.js 14**, **Tailwind CSS**, **shadcn/ui**, **Drizzle ORM**, **PostgreSQL**, and **Clerk** authentication.

### Features

- **AI‑generated interview questions**: Create question sets customized to role, skills, and experience level.
- **Configurable question count**: Control how many questions are generated per session.
- **Secure authentication**: User sign‑in/sign‑up powered by Clerk.
- **PostgreSQL + Drizzle ORM**: Persist interview sessions and related data with a type‑safe schema.
- **Modern UI/UX**: Responsive layout built with Tailwind CSS, shadcn/ui components, and theming support.
- **Next.js App Router**: File‑based routing with middleware‑driven protection for dashboard and other private pages.

### Tech Stack

- **Framework**: Next.js 14 (App Router)
- **Language**: JavaScript / React 18
- **Styling**: Tailwind CSS, tailwind-merge, tailwindcss-animate
- **UI Library**: shadcn/ui (Radix primitives, custom components)
- **Auth**: Clerk (`@clerk/nextjs`)
- **Database**: PostgreSQL (e.g. Neon) with Drizzle ORM + drizzle-kit
- **AI**: Google Gemini via `@google/generative-ai`
- **Tooling**: ESLint, Next.js lint, Drizzle Studio

---

## Getting Started

### Prerequisites

- **Node.js** ≥ 18
- **npm** (or yarn/pnpm/bun, but examples below use npm)
- A PostgreSQL database (local or managed, e.g. Neon)
- API keys/accounts for **Clerk** and **Google Gemini**

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/InterviewAI.git
cd InterviewAI
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env.local` file in the project root (this file should **never** be committed to git):

```env
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key

NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up

NEXT_PUBLIC_DRIZZLE_DB_URL=postgresql://user:password@host:port/database?sslmode=require

NEXT_PUBLIC_GEMINI_API_KEY=your_gemini_api_key

NEXT_PUBLIC_INTERVIEW_QUESTION_COUNT=5
```

**Notes:**

- Keep `.env.local` out of source control (ensure `.gitignore` includes `.env*`).
- Use the connection string provided by your PostgreSQL provider (e.g. Neon).
- Obtain Gemini API keys from the [Google AI for Developers portal](https://ai.google.dev/).
- Obtain Clerk keys from your [Clerk dashboard](https://dashboard.clerk.com/).

### 4. Database setup (Drizzle + PostgreSQL)

This project uses **Drizzle ORM** with **drizzle-kit** for schema management.

- **Push schema to the database**:

```bash
npm run db:push
```

- **Open Drizzle Studio** (optional, for inspecting data and schema):

```bash
npm run db:studio
```

Make sure your `NEXT_PUBLIC_DRIZZLE_DB_URL` is correctly set before running these commands.

### 5. Run the development server

```bash
npm run dev
```

Then open `http://localhost:3000` in your browser.

---

## Project Structure (High Level)

- `app/` – Next.js App Router pages, layouts, and API routes.
- `components/` – Reusable UI components (including shadcn/ui wrappers).
- `lib/` – Shared utilities, config, and helpers.
- `utils/` – Integration helpers (e.g. Gemini model wrapper).
- `public/` – Static assets.


---

## Available Scripts

- `npm run dev` – Start the Next.js development server.
- `npm run build` – Create an optimized production build.
- `npm run start` – Run the production build.
- `npm run lint` – Run linting with Next.js/ESLint.
- `npm run db:push` – Push Drizzle schema to the configured database.
- `npm run db:studio` – Open Drizzle Studio to inspect and manage the DB.

---

## Deployment

This project is designed to be deployed on platforms like **Vercel** or any environment that supports Next.js 14 and Node.js 18+.

Typical steps:

1. Push your code to GitHub.
2. Connect the repository to Vercel (or your preferred host).
3. Configure the same **environment variables** in the hosting provider’s dashboard.
4. Trigger a deployment; Vercel will run `npm install`, `npm run build`, and then host the app.

---

## Contributing

Contributions, ideas, and feedback are welcome. If you’d like to improve the app:

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/my-feature`.
3. Commit your changes: `git commit -m "Add some feature"`.
4. Push the branch: `git push origin feature/my-feature`.
5. Open a Pull Request describing your changes.

---

## License

Specify your preferred license for this project (for example, MIT) or keep it private for personal use. Until a license is added, assume the code is **all rights reserved** by the repository owner.

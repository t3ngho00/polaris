# Polaris

Polaris is a browser-based development environment for building and experimenting with software projects. It combines a multi-file editor, an AI coding assistant, project storage, and an in-browser preview workflow in one workspace.

## Features

- CodeMirror editor with syntax highlighting, folding, minimap, bracket matching, and multi-cursor editing
- File and folder management with autosave and project navigation
- AI suggestions, quick edits, conversations, and an agent with file-management tools
- Live project data and mutations backed by Convex
- Background work and message processing through Inngest
- WebContainer-powered previews and an integrated terminal
- GitHub import and export
- Authentication, error tracking, and usage monitoring

## Technology

- Next.js 16 with the App Router
- React 19 and TypeScript
- Tailwind CSS 4, shadcn/ui, and Radix UI
- CodeMirror 6
- Convex and Inngest
- Vercel AI SDK with Anthropic or Google AI providers
- WebContainer API and xterm.js
- Clerk authentication and Sentry monitoring

## Requirements

- Node.js 20.9 or newer
- npm
- Accounts and API keys for the services enabled in your environment: Clerk, Convex, Inngest, and an AI provider
- Firecrawl and Sentry credentials are optional

## Setup

Install the dependencies:

```bash
npm install
```

Create `.env.local` and add the credentials required by the application:

```env
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=

NEXT_PUBLIC_CONVEX_URL=
CONVEX_DEPLOYMENT=
POLARIS_CONVEX_INTERNAL_KEY=

ANTHROPIC_API_KEY=
GOOGLE_GENERATIVE_AI_API_KEY=

FIRECRAWL_API_KEY=
SENTRY_DSN=
```

Run the development services in separate terminals:

```bash
npx convex dev
npx inngest-cli@latest dev
npm run dev
```

The application is available at [http://localhost:3000](http://localhost:3000).

## Commands

```bash
npm run dev       # Start the Next.js development server
npm run build     # Create a production build
npm run start     # Start the production server
npm run lint      # Run ESLint
```

## Project Layout

```text
src/
  app/             Next.js routes and API handlers
  components/      Shared UI and AI interface components
  features/        Auth, conversations, editor, preview, and projects
  inngest/         Background functions and client setup
  lib/             Shared utilities and service clients
convex/            Schema, queries, mutations, and internal functions
```

## Configuration Notes

The application expects Convex-generated files in `convex/_generated`. Run the Convex development command after configuring `NEXT_PUBLIC_CONVEX_URL` and `CONVEX_DEPLOYMENT` so the local generated client stays in sync with the schema.

AI functionality requires at least one supported provider key. When both are present, the application can select between Anthropic and Google models through its configured model settings.

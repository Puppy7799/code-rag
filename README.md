# RAG Multimodal Chatbot

This project delivers a multimodal chatbot with Retrieval-Augmented Generation (RAG) and optional tool calling. It supports text questions, image inputs, and grounded answers using a local knowledge base. The stack uses Next.js, Vercel AI SDK, and OpenAI.

## Features

- Text and image queries in a single chat interface
- RAG with a local MiniSearch index for fast retrieval
- Optional tool calling for knowledge lookup and study plan generation
- Clean, deploy-ready UI

## Quick Start

1) Install dependencies:

```bash
npm install
```

2) Add environment variables:

```bash
cp .env.example .env.local
```

Set `OPENAI_API_KEY` in `.env.local`.

3) Start the dev server:

```bash
npm run dev
```

Open `http://localhost:3000`.

## Environment Variables

- `OPENAI_API_KEY` (required): OpenAI API key
- `OPENAI_MODEL` (optional): defaults to `gpt-4o-mini`

## RAG Knowledge Base

Edit `src/lib/knowledge-base.ts` to add or replace knowledge entries. The retrieval layer uses MiniSearch with fuzzy matching and boosts for titles and tags.

## API Notes

The chat API lives at `src/app/api/chat/route.ts`. It:

- Builds RAG context from the latest user message
- Injects context into a system prompt
- Sends text + image messages to Groq via the AI SDK
- Uses optional tools for lookup and study plan generation

## Deployment

Deploy on Vercel and add `OPENAI_API_KEY` in project environment variables. The app is ready for Vercel hosting out of the box.

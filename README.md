# Foreman — AI Workplace Productivity Assistant

## Project Overview
Foreman is a single integrated AI-powered dashboard that helps professionals automate everyday workplace tasks. Rather than five separate tools, it is one platform with a sidebar-navigated dashboard containing five connected AI features, all backed by the Claude API.

## Features
1. **Smart Email Generator** — Turn a few bullet points into a polished email. Choose a tone (Formal, Friendly, Persuasive, Apologetic) and recipient context; output is editable before copying.
2. **Meeting Notes Summarizer** — Paste raw or messy meeting notes and get a structured summary: overview, decisions made, action items (with owners/deadlines where mentioned), and open questions.
3. **AI Task Planner** — List out tasks, pick "today" or "this week," and get a prioritized, time-blocked schedule with a short rationale for each priority level.
4. **AI Research Assistant** — Paste a topic, question, or article text and receive a summary, key insights, and practical recommendations, optionally focused on a specific angle.
5. **Workplace Chatbot** — A general-purpose conversational assistant for quick questions, brainstorming, and drafting help, with full conversation memory within the session.

## Tools Used
- **Claude (Anthropic API, model `claude-sonnet-4-6`)** — powers all five AI features via the `/v1/messages` endpoint.
- **HTML/CSS/JavaScript (vanilla)** — single-page application, no build step required.
- **Prompt engineering** — each feature uses a dedicated system prompt scoped to its task (e.g. the summarizer is instructed to always return Overview / Decisions / Action Items / Open Questions in plain text, the planner is instructed to prioritize and time-block realistically), plus a structured user prompt built from form inputs.

## Design
- Single dashboard shell with persistent sidebar navigation and a responsive layout that collapses to a slide-out menu on mobile.
- Every AI output is shown in an **editable** panel so the user can correct or personalize it before use — outputs are drafts, not final copy.
- A **Responsible AI disclaimer** is shown on every tool screen, reminding users to review AI output for accuracy and tone, and not to enter sensitive personal, financial, or client data.
- Clear loading and error states on every AI call.

## Responsible AI Practices
- Persistent disclaimer on every screen generating AI content.
- All outputs are editable, never auto-sent or auto-applied — keeps a human in the loop.
- System prompts are scoped narrowly to each task to reduce off-topic or unpredictable output.
- No sensitive data is stored; all state (chat history, drafts) lives only in the browser session and is lost on refresh.

## Setup Instructions
1. Open `index.html` in any modern browser — no build step or dependencies required.
2. The app calls the Anthropic API directly from the client (`https://api.anthropic.com/v1/messages`) using model `claude-sonnet-4-6`. If hosting this yourself outside of an environment that already provides API access, you will need to either:
   - proxy requests through your own backend that attaches a valid Anthropic API key, or
   - swap the `callClaude` function to call your preferred AI provider.
3. No environment variables are required for the version included here since the API call is pre-authenticated in its current hosting context.

## Team Members
- (Add your name(s) here)

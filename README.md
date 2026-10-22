# AI-Tech-Consultant-capstone-project
**Prepared by Prasanna Kumar Pachigolla**

This project connects three agents: a Python Knowledge Brain that indexes the Brilliant Directories Solution Center; a TypeScript Inbox Agent that drafts replies and records human edits; and a Python Meeting-to-Scope team that produces a draft scope, estimate and proposal. Tasks 2 and 3 call Task 1 over HTTP. Human approval is required for customer-facing outputs.

## Run
Install Docker, copy `.env.example` to `.env`, set `ANTHROPIC_API_KEY` if available, then run:
```bash
docker compose up --build
```
Open `http://localhost:8001/docs`, `http://localhost:8002/health`, and `http://localhost:8003/docs`.

Index the official help centre:
```bash
curl -X POST http://localhost:8001/knowledge/ingest -H 'Content-Type: application/json' -d '{"sitemap_url":"https://support.brilliantdirectories.com/support/sitemap.xml","max_pages":100}'
```
Daily refresh endpoint: `POST http://localhost:8001/knowledge/refresh`.
Inbox draft: `POST http://localhost:8002/inbox/draft`.
Meeting scope: `POST http://localhost:8003/scope/generate`.

See `DESIGN.md`, `EVALS.md`, `AI_LOG.md`, `data/`, and `evals/` for design decisions, sample inputs and test plans. Evaluation results are pending until the cases are run. Do not commit `.env` or API keys.

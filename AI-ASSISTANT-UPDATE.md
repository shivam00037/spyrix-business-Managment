# SPYRIX AI Assistant and monochrome refinement

- The global header search and module-level search inputs now use explicit black/white styles in the Black & White workspace theme.
- The Customers route now uses the shared workspace shell and reference-style KPI/customer-card/recent-customer layout instead of rendering a second red/pink sidebar.
- Added an AI Assistant sidebar tab and route at `/app/ai-assistant`.
- The assistant UI includes text chat, microphone transcription (browser Speech Recognition), spoken responses (browser Speech Synthesis), a read-aloud action, stop-speaking control and starter prompts.
- Added protected `POST /api/v1/ai/chat` backend route using the OpenAI Responses API. Configure `OPENAI_API_KEY`, `OPENAI_MODEL`, and `OPENAI_WEB_SEARCH_ENABLED` in `server/.env`.
- AI features require an authenticated account and configured provider credentials.

The AI service requires an OpenAI API key and API billing. The key is server-only and must not be placed in any `VITE_*` frontend variable.

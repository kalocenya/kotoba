# Kotoba prototype

## Public-test version

`index.html` is now a standalone, non-AI build. It can be hosted as a static site: upload this file to GitHub Pages, Netlify, Vercel, or any ordinary web host. No API key, server, or AI billing is needed for the public test.

The browser keeps saved cards and level settings on that browser/device. They are not shared between testers yet.

## Run locally

The app is a static page plus an optional Perl server for AI exercise generation.

```bash
export OPENAI_API_KEY="your_api_key"
export OPENAI_MODEL="gpt-4.1-mini"
perl server.pl
```

For a simpler one-time terminal setup, run `sh start-kotoba.sh`. It securely prompts for the key without echoing it to the screen.

Open `http://localhost:8080`. The API key stays on the server and is never sent to the browser.

The optional server and AI endpoint are not used by the public-test build. Keep them only if AI generation is re-enabled later.

## AI endpoint

`POST /api/exercises/generate`

Example request:

```json
{"type":"reading","level":"A1","topic":"polite office meeting"}
```

The endpoint requests strict JSON from the OpenAI Responses API and returns a validated exercise. It uses the structured-output guidance from the official OpenAI documentation: https://developers.openai.com/api/docs/guides/structured-outputs

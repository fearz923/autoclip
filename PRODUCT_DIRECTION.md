# Product Direction — Creator-First AutoClip

## Goal

Turn this fork into an English-first AI short-form video clipping product while preserving the proven processing engine.

Primary workflow:

**Upload a video or paste a supported URL → analyze → rank moments → generate clips → preview/export.**

## Baseline rules

1. Keep `main` usable. Product work happens on feature branches and is reviewed before merge.
2. Preserve the existing FastAPI, FFmpeg, Celery/Redis, desktop/CLI, and AI-provider pipeline unless a change is required.
3. Do not add billing, subscriptions, credits, or multi-user SaaS complexity until the real-video pipeline is verified end-to-end.
4. English is the default product language for this fork.
5. Prioritize YouTube and local uploads. Bilibili-specific UI should be de-emphasized/hidden from the primary workflow rather than deleting backend support immediately.
6. Preserve the MIT license and required copyright notice.

## Existing capabilities worth keeping

- Local file and YouTube ingestion
- AI outline/timeline/scoring pipeline
- OpenAI-compatible, Gemini, Qwen/DashScope, SiliconFlow, Ollama and LM Studio support
- FFmpeg rendering
- CLI and MCP integration
- 9:16 publish export, subtitle burn-in and title-card support
- Docker and desktop delivery paths

## Phase 1 — Verify before redesign

- Run backend/frontend automated checks.
- Verify a real local-video pipeline end-to-end.
- Verify at least one cloud LLM provider or a local Ollama path.
- Verify 9:16 export visually.
- Record failures before changing architecture.

## Phase 2 — Creator-first UI

- English-first home screen.
- Reduce the first-run workflow to two obvious choices: Upload Video / Paste Video URL.
- Make clip generation and export the dominant path.
- De-emphasize Bilibili account management and China-specific surfaces.
- Finish migration away from legacy Ant Design layout components where practical.

## Phase 3 — Short-form quality

- Better hook/moment scoring.
- Vertical framing presets for Shorts/Reels/TikTok-style output.
- Caption presets and safe-area handling.
- Optional titles/hooks generated from clip content.
- Batch export.

## Deployment note

The full processing stack is not a good fit for Vercel serverless functions because it requires FFmpeg, long-running jobs, persistent media storage and workers. Vercel can still host a future web frontend; processing should run on a container/VPS-style backend.

## Current fork baseline

Fork: `fearz923/autoclip`

Baseline commit when this direction file was added: `aaf863bbd7bba99c64bc53284d41c0ed19034387`.

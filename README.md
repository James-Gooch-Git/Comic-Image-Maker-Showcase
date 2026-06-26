# Automated Comic Image Maker

An AI-assisted comic book production pipeline that takes a finalised script and produces a page-by-page image-generation promptbook — a structured set of prompts ready to feed into AI image generation tools.

Built around an original comic title (*Issue #1*), the system combines director-of-photography guidance, continuity management, and dynamic movement direction to produce consistent, production-ready prompts across a full issue.

---

## The Problem

Generating a consistent comic book with AI image tools is hard. Characters look different panel to panel, lighting shifts unexpectedly, and action sequences lose coherence. This pipeline solves that by treating prompt generation as a first-class engineering problem.

---

## Features

- **Script-to-promptbook pipeline** — reads a finalised comic script and generates a prompt per panel
- **Continuity management** — tracks character appearance, costume, and environment consistency across pages
- **Director-of-photography layer** — applies cinematic framing, lighting, and camera angle guidance per panel
- **Dynamic movement guidance** — generates action/motion descriptors for fight and chase sequences
- **Dual output format** — produces both Markdown (human-readable) and JSON (machine-readable) promptbooks
- **Cost reporting** — tracks and reports API token usage across a full issue
- **Bible-driven** — character descriptions and visual canon feed into every prompt automatically

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Python |
| Data models | Pydantic v2 |
| Async pipeline | asyncio |
| Orchestration | Claude API |
| Output | Markdown + JSON promptbook |

---

## Pipeline Overview

```
┌──────────────────────┐
│   Comic Script (.md) │
└──────────┬───────────┘
           │
┌──────────▼───────────┐
│  Script Parser        │
│  (scenes, panels,     │
│   dialogue, action)   │
└──────────┬───────────┘
           │
┌──────────▼───────────────────────────────────┐
│  Prompt Generation Pipeline                   │
│  ┌──────────────┐  ┌────────────────────┐    │
│  │  Character   │  │  Director of        │    │
│  │  Bible       │  │  Photography Layer  │    │
│  └──────┬───────┘  └─────────┬──────────┘    │
│         └──────────┬──────────┘               │
│               ┌────▼─────┐                    │
│               │  Claude  │                    │
│               │   API    │                    │
│               └────┬─────┘                    │
│                    │                          │
│          ┌─────────▼──────────┐               │
│          │ Continuity Manager │               │
│          └─────────┬──────────┘               │
└────────────────────┼──────────────────────────┘
                     │
        ┌────────────▼────────────┐
        │      Promptbook         │
        │  (Markdown + JSON)      │
        └─────────────────────────┘
```

---

## Example Output (single panel)

```json
{
  "page": 3,
  "panel": 2,
  "prompt": "Wide establishing shot. A twelve-year-old boy with messy dark hair 
             and oversized grey hoodie stands at the edge of a collapsed overpass,
             golden hour backlight, volumetric fog below. Crash test dummy beside 
             him, arm raised. Cinematic composition, muted palette with warm rim light.",
  "negative_prompt": "text, watermark, blurry, extra limbs",
  "camera": "wide shot, low angle",
  "lighting": "golden hour, backlit",
  "mood": "isolated, surreal"
}
```

---

## Screenshots

*Contact me for a demo or to discuss the architecture.*

---

## Source Code

This is a portfolio showcase. The full source code is private as this project has commercial potential.

**Interested in the codebase or a walkthrough?** Reach out via [GitHub](https://github.com/James-Gooch-Git) or [email](mailto:gewainwright@gmail.com).

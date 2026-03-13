# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

ZeroEval documentation site built with [Mintlify](https://mintlify.com). ZeroEval is an AI evaluation platform with three core products: Tracing (monitoring & observability), Judges (AI evaluation calibrated to human preferences), and Prompts (automatic prompt optimization).

## Development Commands

```bash
# Install Mintlify CLI globally
npm i -g mintlify

# Run local dev server (must run from repo root where docs.json is)
mintlify dev

# Re-install dependencies if dev server fails
mintlify install
```

## Architecture

- **docs.json** - Central config: navigation structure, theme (`willow`), branding, navbar, footer. This is the single source of truth for page hierarchy.
- **Content pages** are `.mdx` files using Mintlify's MDX components (`<Card>`, `<CardGroup>`, `<Accordion>`, `<CodeGroup>`, etc.)
- **snippets/** - Reusable MDX fragments included in other pages
- **api-reference/** - API docs with OpenAPI spec (`openapi.json`) and endpoint pages
- **images/** and **videos/** - Static assets referenced from MDX pages
- **logo/** - SVG logos (light/dark variants)

## Content Sections (in docs.json navigation)

| Directory | Purpose |
|-----------|---------|
| `tracing/` | Monitoring & tracing guides, SDK docs (Python + TypeScript), advanced topics (sessions, tagging, OTel) |
| `autotune/` | Prompt optimization ("Prompts" in nav), setup, model configs |
| `judges/` | AI evaluation judges, setup, multimodal eval, feedback submission |
| `evaluations/` | Evaluations section (currently placeholder) |

## Key Conventions

- Page metadata uses YAML frontmatter (`title`, `description`, `sidebarTitle`)
- Navigation is defined entirely in `docs.json` under `navigation.tabs[].groups` - adding a new page requires updating this file
- The `autotune/` directory maps to "Prompts" in the navigation (not "Autotune")
- Deployments auto-propagate from the default branch via Mintlify's GitHub App

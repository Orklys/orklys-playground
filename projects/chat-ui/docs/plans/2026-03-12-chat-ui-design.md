# Chat UI Design Document

**Date:** 2026-03-12
**Status:** Approved

## Context

Orklys needs a chat UI that serves as the primary interface between the company and its users — ranging from complete beginners exploring energy communities to advanced users consuming dense legal citations. The chat is powered by an orchestrator agent that routes to specialized agents (legal, project architect, etc.) behind the scenes, but presents a single unified interface.

This is a design playground — we're building 5 distinct variations in vanilla HTML/CSS/JS to explore different UX directions before porting the winner to the production React/Next.js app.

## Core Requirements

### Functional
- Single adaptive UI — one chat interface for all user types
- Mobile-first — generous touch targets, full-screen on mobile
- Container-agnostic — works as popup widget, dashboard panel, or standalone
- Vanilla HTML/CSS/JS — no frameworks, self-contained per variation

### Message Types
1. **User text bubble** — right-aligned, forest green bg, white text
2. **Assistant text bubble** — left-aligned, light/cream bg, dark text
3. **Citation-enriched message** — inline superscript [1] with hover tooltip + collapsible "Sources" section
4. **Interactive components** (inline in chat flow): slider, multiple choice, file upload
5. **Data confirmation card** — "Noted: Location: Aarhus, 150 homes. [Edit]"
6. **System/status message** — centered, subtle

### Citation System
- Inline superscript numbers [1][2] in assistant messages
- Hover/tap → tooltip: quote excerpt, document title, section ref, "View document" link
- Collapsible "Sources (N)" section below the message
- Click "View document" → PDF viewer dialog (modal on desktop, bottom sheet on mobile)

### Progressive Profile (Side Panel)
- Side panel ("Community Profile") on wider screens, pull-up drawer on mobile
- Fields appear progressively as captured — empty fields hidden
- Grouped by category: Location, Energy, Community, Status
- Each field has inline-edit
- Completion indicator (e.g., "5/12 fields")
- Inline confirmation cards in chat when data is captured
- Mobile: floating indicator to open drawer

### Visual Foundation (Orklys Design System)
- Primary: Forest green #0a5c36
- Background: Cream #f5f2eb
- Text: Near-black #02120a
- Typography: Nunito (headings), Open Sans (body)
- Transitions: 200-300ms smooth
- Shadows: subtle, card-lift on hover

## The 5 Variations

### Variation 1 — "Clean Minimal"
Maximum whitespace, thin lines, understated backgrounds. Barely-there bubble tints. Slim side panel. Inspiration: Linear, Notion. Professional, quiet confidence.

### Variation 2 — "Warm Conversational"
Rounded bubbles, soft shadows, avatar circles, gentle animations. Card-style side panel with icons. Warmer cream tones, generous padding. Inspiration: WhatsApp meets Scandinavian design. Friendly, approachable, trustworthy.

### Variation 3 — "Dashboard-Native"
Compact, dense layout. Structured side panel with clear labels, form-like feel. Smaller bubbles, tighter spacing. Inspiration: Intercom, Zendesk. Efficient, professional, data-aware.

### Variation 4 — "Full-Bleed Immersive"
No visible container — messages float on subtle background. Stronger user/assistant separation. Side panel as overlay. Inspiration: Claude.ai, ChatGPT. Modern, focused, distraction-free.

### Variation 5 — "Card-Based Modular"
Every message/component is a distinct card. Citations, components, confirmations all have card treatment. Side panel as mini-card stack. Inspiration: Slack blocks, Notion databases. Structured, scannable, modular.

## Mock Conversation (Same Across All Variations)

1. System message: "Welcome to Orklys"
2. Assistant greeting with guidance
3. User response about their community
4. Assistant with data confirmation card (location, homes)
5. Interactive slider (number of community members)
6. Completed slider state
7. Multiple choice component (energy type)
8. Assistant message with citations [1][2]
9. Collapsible Sources section (2 references)
10. Side panel with 5 populated fields + edit capability

---
name: ai-landing-pipeline
description: "Use when the user wants to create, redesign, launch, or manage a landing page end-to-end with AI: brief, copy, design direction, implementation, browser QA, accessibility, SEO, analytics, deployment, and post-launch edits. Trigger on лендинг, landing, промо-страница, MVP page, product page, portfolio/site showcase, AI Projects landing, web3brand-style page, or requests to go from idea to production page."
version: "1.0.0"
author: web3blind / Hermes Agent
license: MIT
---
# ai-landing-pipeline

End-to-end manager for fast but production-safe landing pages. The goal is not “generate a pretty page”, but ship a maintainable, accessible, measurable page from idea to production.

## When to use

Use this skill for:
- new landing pages, promo pages, product pages, portfolio/showcase pages;
- redesigning an existing landing while preserving stack and content constraints;
- turning a rough idea, Google Doc, voice note, or existing draft into a launched page;
- pages similar to prior the user workflows: web3brand-style landing, AI Projects portfolio, project launch pages.

If the task is mainly visual direction, also load `webd`. If it is mainly conversion diagnosis, also load `page-cro`. If it is mainly copy, also load `copywriting`. If it involves analytics, also load `analytics-tracking`.

## Core principle

Always run the pipeline in this order:

1. **Landing doc** — goal, audience, offer, CTA, block structure, draft copy, proof, SEO, analytics, accessibility requirements.
2. **Design direction** — choose one visual language before coding; avoid mixing unrelated aesthetics.
3. **Prototype / implementation** — build in the target stack or vanilla-first if stack is unspecified.
4. **QA pass** — browser, mobile, links, forms/buttons, accessibility, SEO/meta, performance sanity.
5. **Production handoff** — deployment notes, editable content points, analytics events, follow-up checklist.

Do not start from random component generation unless the user explicitly asks for a quick throwaway mockup.

## Workflow

### 1. Intake

Gather or infer:
- project/product name;
- target audience;
- primary action/CTA;
- domain/deployment target if known;
- stack/repo if existing;
- must-have sections;
- language(s);
- assets: logo, screenshots, images, icons;
- analytics/SEO requirements;
- accessibility requirements, especially screen-reader and keyboard use.

If enough context is present, proceed without asking. Ask only when missing information changes implementation materially.

### 2. Landing doc

Create a concise landing doc before design/code:
- page goal;
- promise / value proposition;
- primary CTA and fallback CTA;
- audience and objections;
- section map;
- draft copy for each section;
- proof/trust elements;
- SEO title and description;
- OpenGraph/social preview requirements;
- analytics events;
- accessibility notes.

Use `references/landing-doc-template.md` when a structured artifact is useful.

### 3. Design direction

Use `webd` patterns and run its anti-generic design gate:
- select one primary aesthetic;
- define typography, color roles, spacing rhythm, CTA treatment;
- choose whether the page should be premium, brutalist, clean SaaS, Web3-native, portfolio/editorial, etc.;
- avoid the default AI landing skeleton (`hero → three cards → CTA → footer`) unless it is genuinely the right structure;
- vary section rhythm and use real proof/product material instead of invented metrics, logos, testimonials, or fake dashboard data;
- keep motion intentional and reduced-motion safe.

For small pages, a short direction note is enough. For multi-page or long-term brand work, create a lightweight design-system note.

### 4. Implementation

Default to the existing repo/stack when present. If no stack is specified, use local HTML/CSS/JS first; do not introduce React/Next/Tailwind/build tools by assumption.

Before implementing a frontend pattern, apply a modern-web check:
- look up or inspect current guidance for the exact pattern when it involves modern CSS, forms, accessibility, native dialogs/popovers, passkeys, View Transitions, scroll animations, container queries, or performance-sensitive behavior;
- prefer native browser capabilities over old library-heavy workarounds when support is acceptable;
- do not run or install external frontend-guidance packages by default; if later approved, use a reviewed/pinned local copy and disable telemetry when the package supports it.

Implementation rules:
- preserve semantic headings and landmarks;
- keep content editable and sectioned clearly;
- avoid remote scripts, analytics, trackers, CDNs, and embeds unless requested;
- keep images optimized and alt text meaningful;
- include keyboard-accessible controls and visible focus;
- respect `prefers-reduced-motion` for animations.

### 5. QA before calling done

Run real checks where tools are available:
- browser open/snapshot or screenshot;
- mobile/responsive sanity if possible;
- all links and CTAs;
- forms/buttons/wallet/connect placeholders;
- title, meta description, OpenGraph/Twitter tags;
- heading order and landmark sanity;
- contrast/focus/keyboard basics;
- console errors;
- performance sanity: no obvious huge images, heavy animation, or blocking assets.

For launch-critical pages, create a small QA report with PASS/REVISE/BLOCK items.

### 6. Production handoff

Return:
- what was built/changed;
- where the files/repo/deploy are;
- what was verified with real outputs;
- what still needs external action, if any: domain, analytics key, DNS, copy approval, assets.

Do not claim deployment or analytics are working unless verified.

## Fast modes

### Draft mode
Use when the user wants speed over completeness:
- produce landing doc + first visual/HTML draft;
- skip deployment;
- still keep accessibility basics.

### Build mode
Use when the user wants a working page:
- implement in repo or local files;
- run browser QA;
- provide MEDIA/screenshot if useful.

### Launch mode
Use when the user wants production:
- include SEO, analytics, deploy/domain checklist;
- verify live URL after deploy if credentials/path are available.

## Quality bar

A good AI-built landing is:
- clear in the first screen;
- specific about the offer;
- visually coherent, not generic AI-gloss;
- accessible enough to navigate by keyboard/screen reader;
- easy to edit after launch;
- backed by real browser checks, not only model confidence.

## Trigger examples

- “Собери лендинг для нового проекта от идеи до продакшена.”
- “Нужен быстрый landing pipeline как для web3brand/AI Projects.”
- “Переделай промо-страницу и проверь, чтобы она была доступной и SEO-ready.”

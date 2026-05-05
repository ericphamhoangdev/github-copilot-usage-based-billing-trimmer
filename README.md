# GitHub Copilot Usage-Based Billing Trimmer / Cost Optimizer

## 👉 [Open the tool](https://ericphamhoangdev.github.io/github-copilot-usage-based-billing-trimmer/) — no install, runs entirely in your browser

A self-contained, browser-only tool that analyses your GitHub Copilot Chat debug logs and shows you **how much your sessions will cost under the new token-based billing model** (effective 2026-06-01) — with a focus on identifying **redundant MCP tool schemas** that silently inflate every request.

> ⚠ This tool is not endorsed by or affiliated with GitHub or Microsoft. All calculations are the author's own interpretation of publicly available pricing data.

---

## Why this exists

GitHub Copilot is [moving from per-request multiplier billing to usage-based token billing](https://github.blog/news-insights/company-news/github-copilot-is-moving-to-usage-based-billing/). Under the new model, every token counts — including the tool schemas that Copilot injects into every request for all enabled MCP servers, even when those tools are never called.

This tool helps you:
1. **Estimate your old vs new cost** for a real chat session.
2. **Spot tool bloat** — MCP servers whose schemas are shipped on every request but never actually invoked.
3. **Decide which MCP servers to disable** per project via `.vscode/settings.json`.

---

## Features

- 📊 **Cost comparison cards** — old multiplier-based price vs new token-based price side-by-side
- 🚨 **Tool bloat detection** — per-prompt breakdown of shipped vs used tool schemas, wasted token estimates, and a grouped tree view by MCP server source
- 📋 **Full prompt explorer** — collapsible tree of every prompt → request → message with token counts, cache rates, and cost per request
- 🔒 **100% local** — all processing happens in your browser; your chat logs never leave your machine
- 📦 **Zero dependencies** — single self-contained HTML file, no npm, no CDN, no build step

---

## Usage

### 1. Export your debug log from VS Code

1. Open the **Copilot Chat** panel in VS Code.
2. Click the **⋯** (more actions) menu in the top-right corner.
3. Select **"Export Debug Logs"** — _not_ "Export Chat" (that version omits token metadata).
4. Save the resulting `copilot_all_prompts_*.json` file anywhere on your machine.

### 2. Open the tool

**[https://ericphamhoangdev.github.io/github-copilot-usage-based-billing-trimmer/](https://ericphamhoangdev.github.io/github-copilot-usage-based-billing-trimmer/)**

No install, no server — runs entirely in your browser.

### 3. Drop your file

Drag-and-drop the exported JSON onto the drop zone, or click to browse.

### 4. Read the results

- **Summary cards** show your old vs new estimated cost and the delta.
- **Prompt list** expands each conversation turn to show per-request token breakdowns.
- Any prompt with a 🚨 **Tool bloat** banner has MCP schemas being wasted. The banner tells you exactly which servers to disable.

---

## Pricing data

Rates are embedded from the [GitHub Copilot billing documentation](https://docs.github.com/en/copilot/reference/copilot-billing/models-and-pricing) (effective 2026-06-01, 1 credit = $0.01 USD).

| Provider  | Models included | Notes |
|-----------|----------------|-------|
| OpenAI    | gpt-4.1 ⓘ, gpt-5-mini ⓘ, gpt-4o, gpt-5.2/5.3/5.4/5.5 series | ⓘ = included model (counts against plan allowance) |
| Anthropic | claude-haiku-4.5, claude-sonnet-4/4.5/4.6, claude-opus-4.5/4.6/4.7 | |
| Google    | gemini-2.5-pro, gemini-3-flash, gemini-3.1-pro | |
| xAI       | grok-code-fast-1 | |
| GitHub    | raptor-mini, goldeneye | |

---

## Supported plans

| Plan | Price | Included premium requests |
|------|-------|--------------------------|
| Pro  | $10 / mo | 300 |
| Pro+ | $39 / mo | 1,500 |

---

## ⭐ Star the repo

If you find this tool useful, please [star the repo on GitHub](https://github.com/ericphamhoangdev/github-copilot-usage-based-billing-trimmer) — it encourages the author to continue researching and improving the tool.

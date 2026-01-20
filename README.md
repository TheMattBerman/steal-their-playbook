# Steal Their Playbook

**Turn any competitor URL into a professional intelligence deck in 60 seconds.**

Drop in a competitor's website URL. Get back a beautifully designed presentation exposing their entire strategy - positioning, messaging, ads, content, SEO, and exactly how to beat them.

![n8n Workflow](https://img.shields.io/badge/n8n-Workflow-FF6D5A?style=for-the-badge&logo=n8n) ![Powered by Gamma](https://img.shields.io/badge/Powered%20by-Gamma-7C3AED?style=for-the-badge) ![AI Powered](https://img.shields.io/badge/AI-Claude%20%2B%20Gemini-00A67E?style=for-the-badge)

---

## What You Get

Enter a competitor URL. Receive a 10-slide deck covering:

| Slide | Intelligence Gathered |
|-------|----------------------|
| **Executive Summary** | Threat level assessment, 5 key insights, competitive urgency |
| **How They Dominate** | Value proposition, target audience, key differentiators |
| **Messaging Playbook** | Brand voice, primary hooks, proof elements |
| **Content Machine** | Instagram/LinkedIn metrics, posting frequency, top content |
| **Ad Strategy (EXPOSED)** | Active ad count, headlines, hooks, actual creative examples |
| **SEO Intelligence** | Traffic estimates, keyword count, opportunities to steal |
| **Weak Spots** | Content gaps, messaging gaps, audience segments they're ignoring |
| **Your Attack Plan** | Quick wins for this week, positioning plays, ad concepts to test |

All automated. All in under 60 seconds.

---

## How It Works

```
URL → Scrape 8 Data Sources → AI Analysis → Professional Deck
```

**Data Collection (Parallel):**
- **Firecrawl** - Homepage, About, Pricing, Blog pages
- **ScrapeCreators** - LinkedIn company, Instagram profile, Meta Ad Library
- **DataForSEO** - Organic traffic, keywords, domain metrics

**AI Processing:**
- **Gemini Flash** - Extracts structured data from raw API responses
- **Claude Sonnet** - Synthesizes everything into actionable competitive intelligence

**Output:**
- **Gamma Remix API** - Fills your branded template with competitor data

---

## Quick Start

### 1. Import the Workflow

Download `workflow.json` and import it into n8n:
- Go to **Workflows** → **Import from File**
- Select `workflow.json`

### 2. Set Up Your API Credentials

You'll need accounts with these services:

| Service | What It Does | Sign Up |
|---------|--------------|---------|
| **Firecrawl** | Website scraping | [firecrawl.dev](https://firecrawl.dev) |
| **ScrapeCreators** | Social media + ad data | [scrapecreators.com](https://scrapecreators.com) |
| **DataForSEO** | SEO metrics | [dataforseo.com](https://dataforseo.com) |
| **OpenRouter** | AI models (Claude + Gemini) | [openrouter.ai](https://openrouter.ai) |
| **Gamma** | Deck generation (Pro required) | [gamma.app](https://gamma.app) |

In n8n, go to **Settings** → **Credentials** and create Header Auth credentials:

| Credential Name | Header Name | Header Value |
|-----------------|-------------|--------------|
| `Firecrawl API` | `Authorization` | `Bearer YOUR_KEY` |
| `Scrapecreators` | `x-api-key` | `YOUR_KEY` |
| `DataForSEO API` | `Authorization` | `Basic YOUR_BASE64_CREDENTIALS` |
| `OpenRouter` | `Authorization` | `Bearer YOUR_KEY` |
| `Gamma API` | `X-API-KEY` | `YOUR_KEY` |

### 3. Create Your Gamma Template

This workflow uses Gamma's **Remix API** - it fills YOUR template with competitor data. You need to create a template deck first:

1. Go to [gamma.app](https://gamma.app) and create a new presentation
2. Design a 10-slide competitive playbook with your branding
3. Include placeholder content matching the slide structure above
4. Copy the deck ID from the URL (format: `g_XXXXXXXXXXXX`)
5. In the workflow, find **"Gamma - Remix Template"** node and replace `YOUR_GAMMA_TEMPLATE_ID` with your deck ID

**Want a pre-built template to start from?**

[![Use Gamma Template](https://img.shields.io/badge/Get%20Starter%20Template-Gamma-7C3AED?style=for-the-badge)](https://gamma.app/docs/LEAKED-INTEL-V3-rgos3tz3jlt77ez)

### 4. Run It

**Option A: Web Form (Easiest)**
- Activate the workflow
- Click the Form Trigger node to get the form URL
- Enter any competitor URL
- Get your deck!

**Option B: Webhook API**
```bash
curl -X POST "YOUR_WEBHOOK_URL" \
  -H "Content-Type: application/json" \
  -d '{"url": "https://competitor.com"}'
```

> **Note:** Social handles are auto-detected from the competitor's homepage. You only need to provide the URL.

---

## Architecture

```
[Form/Webhook] → [Firecrawl Homepage] → [Extract Social Handles]
                                              ↓
                                    [Company Search + LinkedIn Search]
                                              ↓
                        ┌─────────────────────┴─────────────────────┐
                        │              PARALLEL SCRAPING            │
                        ├─→ Firecrawl: About, Pricing, Blog         │
                        ├─→ ScrapeCreators: LinkedIn, Instagram, Ads│
                        └─→ DataForSEO: Domain metrics              │
                                              ↓
                        ┌─────────────────────┴─────────────────────┐
                        │            AI DATA EXTRACTION             │
                        │    Gemini Flash structures raw responses  │
                        └───────────────────────────────────────────┘
                                              ↓
                              [Merge All 8 Data Streams]
                                              ↓
                        ┌─────────────────────────────────────────┐
                        │         COMPETITIVE ANALYSIS            │
                        │   Claude Sonnet generates the playbook  │
                        └─────────────────────────────────────────┘
                                              ↓
                        ┌─────────────────────────────────────────┐
                        │           DECK GENERATION               │
                        │   Gamma Remix API fills your template   │
                        └─────────────────────────────────────────┘
                                              ↓
                                    [Shareable Deck URL]
```

**22 nodes** | **8 parallel data sources** | **2 AI models** | **1 beautiful deck**

---

## Cost Per Run

| Service | Pricing Model | ~Cost/Run |
|---------|---------------|-----------|
| Firecrawl | $0.001/page | ~$0.004 |
| ScrapeCreators | Free tier available | Free |
| DataForSEO | ~$0.002/request | ~$0.002 |
| OpenRouter (Gemini) | ~$0.10/1M tokens | ~$0.01 |
| OpenRouter (Claude) | ~$3/1M tokens | ~$0.05 |
| Gamma | Pro plan required | 1 credit |

**Total: ~$0.07 + 1 Gamma credit per competitor analyzed**

---

## Customization

**Change the analysis focus:**
Edit the Claude prompt in the **"Claude - Competitive Analysis"** node.

**Modify deck content:**
Edit the **"Format Gamma Prompt"** code node to change slide content.

**Add more data sources:**
Add HTTP Request nodes and connect them to the Merge node (8 inputs).

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Missing social data | Some companies don't link social profiles - data will be limited |
| Gamma generation failed | Verify template ID, check Pro subscription, validate API key |
| Empty ad data | Competitor may not be running Meta ads |
| Timeout errors | Try a smaller competitor website, increase timeout settings |

---

## Credits

**Created by [@themattberman](https://x.com/themattberman)**

**Learn more:** [bigplayers.co](https://bigplayers.co)

**Need AI automation for your business?** [emerald.digital](https://emerald.digital)

---

## Powered By

[![n8n](https://img.shields.io/badge/n8n-Workflow%20Automation-FF6D5A?style=flat-square&logo=n8n)](https://n8n.io) - Open-source workflow automation

[![Gamma](https://img.shields.io/badge/Gamma-AI%20Presentations-7C3AED?style=flat-square)](https://gamma.app) - Beautiful AI-powered presentations

[![Anthropic](https://img.shields.io/badge/Claude-Anthropic-D4A574?style=flat-square)](https://anthropic.com) - Advanced AI analysis

[![Firecrawl](https://img.shields.io/badge/Firecrawl-Web%20Scraping-FF6B35?style=flat-square)](https://firecrawl.dev) - Intelligent web scraping

---

## License

MIT License - Use it, modify it, build on it.

---

**Questions?** Open an issue or DM [@themattberman](https://x.com/themattberman) on X.

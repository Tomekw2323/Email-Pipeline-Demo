# 📧 AI Email Pipeline — Live Demo

> Automated email classification, prioritization, and reply drafting powered by Claude AI.

**[🔴 Live Demo](https://twojname.github.io/email-pipeline-demo)** &nbsp;|&nbsp; Built by [Tomasz Witkowski](mailto:tomekw2323@gmail.com)

---

## What it does

The pipeline connects to your Gmail inbox and for every unread email it:

1. **Classifies** — support, sales, invoice, spam, urgent, or other
2. **Prioritizes** — high / medium / low based on content
3. **Drafts a reply** — context-aware, in the same language as the email
4. **Acts automatically** — sends replies with high confidence, forwards invoices, drops spam

Average time saved: **~3 hours per week** for a typical small business inbox.

---

## Demo

The `index.html` file is a fully interactive demo page. It calls the Claude API directly from the browser so anyone can test the pipeline without installing anything.

To run the demo on GitHub Pages:
1. Fork this repo
2. Go to **Settings → Pages → Deploy from branch → main / root**
3. Done — your demo is live at `https://yourusername.github.io/email-pipeline-demo`

---

## Full Python pipeline

The production version (coming soon in `/pipeline`) runs as a background script:

```bash
# One-time run
python main.py --once

# Watch mode (checks every 5 minutes)
python main.py --watch
```

### Stack

| Component | Technology |
|---|---|
| Email fetching | Gmail API + google-auth-oauthlib |
| AI classification | Claude API (claude-opus-4-5) |
| Language | Python 3.11+ |
| Config | python-dotenv |

### Setup (Python pipeline)

```bash
git clone https://github.com/yourusername/email-pipeline-demo
cd email-pipeline-demo
pip install -r requirements.txt
cp .env.example .env
# Add your ANTHROPIC_API_KEY to .env
# Add your Gmail credentials.json (see below)
python main.py --once
```

**Gmail credentials:** Go to [Google Cloud Console](https://console.cloud.google.com) → Create project → Enable Gmail API → Create OAuth 2.0 credentials → Download as `credentials.json`.

---

## Categories detected

| Category | Action |
|---|---|
| `support` | Draft reply, auto-send if confidence > 85% |
| `sales` | Draft reply, flag for review |
| `invoice` | Forward to accounting@company.com |
| `urgent` | High priority flag, immediate forward |
| `spam` | Mark as read, no action |

---

## Contact

Want this set up for your business?

**Tomasz Witkowski** — Automation & AI specialist  
📧 tomekw2323@gmail.com  
📱 +48 784 237 870  
🔗 [LinkedIn](https://linkedin.com/in/twojprofil)

---

*Built with Python + Claude API. Demo page runs entirely in the browser — no backend needed.*

# Scam Detection Copilot

> An AI-powered fraud analysis tool combining behavioral science frameworks with LLM reasoning to detect and explain social engineering attacks.

**[Live Demo →](https://your-github-username.github.io/scam-detection-copilot)**

---

## What This Is

Modern scams don't exploit technical vulnerabilities — they exploit **human psychology**. A pig butchering operation doesn't need to hack your bank; it needs 6 weeks to make you fall in love.

This project builds a detection agent that thinks the way a fraud analyst thinks: not just pattern-matching keywords, but reasoning about **manipulation tactics, psychological leverage points, and scam lifecycle phases**.

Built to demonstrate the intersection of:
- Fraud domain expertise (operational experience at EverCompliant, 2016–2019)
- Applied AI/ML (M.Sc. Machine Learning, Reichman University, 2025)
- Behavioral science frameworks

---

## Features

### 🤖 Detection Agent
Paste any conversation transcript or case description. The agent outputs:
- **Risk score** (0–100) with severity classification
- **Scam type** identification
- **Psychological tactics** in use (e.g. Love Bombing, Authority, Scarcity)
- **Red flags** with severity and explanation
- **Current phase** in the scam lifecycle
- **Intervention recommendation** — written with victim empathy, not blame

### 📖 Scam Playbook
Structured behavioral analysis of three major scam typologies, broken down phase by phase:
- Romance Scam / Pig Butchering (杀猪盘)
- Investment Fraud / Advance Fee variants
- Authority Impersonation (Bank / Government / Tech Support)

Each phase includes: attacker psychology, victim psychology, and detectable signals.

### 🧠 Knowledge Base
The theoretical frameworks underlying the agent's reasoning:
- Cialdini's 7 Principles of Influence
- BITE Model of Coercive Control
- Cognitive Hijacking mechanisms
- Network / link analysis methodology
- Intervention design principles

---

## Detection Framework

The agent's reasoning is structured around two behavioral science models:

### Cialdini's 7 Influence Principles — Applied to Fraud

| Principle | How Scammers Use It |
|-----------|-------------------|
| Reciprocity | Small gifts, favors, emotional investment first |
| Commitment | Get a small "yes" → escalate to bigger asks |
| Social Proof | Fake testimonials, bot-filled WhatsApp groups |
| Authority | Impersonate banks, government, famous investors |
| Liking | Romance building, finding common ground |
| Scarcity | "Only 3 spots left," countdown timers |
| Unity | "We're in this together," in-group identity |

### Scam Lifecycle Phases

Scams follow predictable escalation patterns. Knowing the phase tells you how much financial exposure has occurred and what intervention is still possible:

```
RECRUITMENT → TRUST BUILDING → GROOMING → ESCALATION → EXTRACTION → EXIT
```

Early-phase detection (before financial transfer) is the highest-value intervention point.

---

## Technical Architecture

```
User Input (conversation text)
        ↓
Anthropic Claude claude-sonnet-4-20250514
(Specialized fraud analysis prompt)
        ↓
Structured JSON output:
{
  scam_type, risk_score, risk_level,
  psychological_tactics[], red_flags[],
  phase, intervention, confidence
}
        ↓
Frontend visualization
```

**Stack:** HTML / CSS / Vanilla JavaScript + Anthropic API

No backend. No framework. Single file deployment — intentionally simple to keep the focus on the analytical layer, not the engineering layer.

---

## Sample Cases

Four representative cases are included to demonstrate the agent's reasoning across different fraud typologies:

| Case | Scam Type | Key Signals |
|------|-----------|-------------|
| Romance / Crypto | Pig Butchering | Never video calls, offshore platform, guaranteed returns |
| AI Trading Bot | Investment Fraud | FOMO engineering, fake social proof, advance fee |
| Bank Security Call | Impersonation | Spoofed caller ID, isolation demand, safe account transfer |
| Urgent Email | Phishing | Domain spoofing, urgency framing, credential harvesting |

---

## Why This Approach

### The Problem With Rule-Based Detection

Traditional fraud systems flag keywords and transaction patterns. Scammers adapt: they avoid trigger words, use new platforms, evolve their scripts. A rule that catches today's pig butchering script won't catch next month's variant.

### Behavioral Invariance

What doesn't change is the underlying psychological manipulation structure. A romance scammer in 2019 and one in 2025 both use love bombing, isolation, and urgency — because these exploit hardwired human responses that don't get patched.

Detecting **tactics** rather than **scripts** creates more durable detection logic.

### LLM as Reasoning Engine

Claude is used here not as a classifier but as a **reasoning agent** — given a framework, it can apply it to novel cases, explain its reasoning, and generate victim-appropriate intervention language. This mirrors how a senior fraud analyst actually works.

---

## Limitations & Honest Assessment

- **Not production-ready:** This is a demonstration, not a deployed system. A production fraud agent would require fine-tuning on labeled case data, latency optimization, and adversarial robustness testing.
- **No ground truth validation:** Red flag detection accuracy is not benchmarked against a labeled dataset. That would be the next step.
- **LLM hallucination risk:** The agent can misclassify edge cases or benign situations as high-risk. Human review would be required in any real deployment.

---

## About

**Dan Fang** — Fraud & Risk Intelligence · M.Sc. Machine Learning

3+ years detecting merchant fraud, money laundering networks, and financial crime at EverCompliant (Tel Aviv). M.Sc. in Machine Learning & Data Science from Reichman University (distinction). Trilingual: English, Chinese, Hebrew.

Previously: link analysis across global merchant data, behavioral anomaly detection, AML risk assessment, OSINT/WEBINT investigations.

📧 danfly8888@gmail.com | 📍 Ramat Gan, Israel

---

*Built as a portfolio demonstration for Fraud AI / Risk Intelligence roles.*

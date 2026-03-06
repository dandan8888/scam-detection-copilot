# Fraud Detection AI agent

> AI-powered fraud detection agent combining behavioral science with LLM reasoning.

**[Live Demo →](https://dandan8888.github.io/Fraud_Risk_Intelligence_Portfolio/Fraud-detection/fraud-detection-dashboard.html)**

---

## The Problem

Modern scams don't exploit technical vulnerabilities — they exploit human psychology. A pig butchering operation doesn't need to hack your bank; it needs 6 weeks to make you fall in love with a fictional person. A bank impersonation call doesn't need your password; it needs 3 minutes to make you panic.

Rule-based systems fail here because scammers adapt their scripts constantly. What doesn't change is the underlying psychological manipulation structure — the same tactics appear across every variant because they exploit hardwired human responses that don't get patched.

---

## What This Does

Paste any conversation transcript or case description. The agent outputs:

- **Risk score** (0–100) with severity classification (LOW / MEDIUM / HIGH / CRITICAL)
- **Scam type** identification
- **Psychological tactics** detected (e.g. Love Bombing, Authority, Scarcity, Isolation)
- **Red flags** with per-signal severity and explanation
- **Lifecycle phase** — where in the scam progression is this case?
- **Intervention language** — what to say to the victim, written with empathy not blame

Four sample cases are pre-loaded to demonstrate reasoning across different typologies.

---

## Detection Framework

The agent's reasoning is grounded in two behavioral science models:

### Cialdini's Principles of Influence — Applied to Fraud
*(Cialdini, Influence, 1984; Pre-Suasion, 2016)*

| Principle | How Scammers Use It |
|-----------|-------------------|
| Reciprocity | Small gifts, favors, emotional investment first |
| Commitment | Get a small "yes" → escalate to bigger asks |
| Social Proof | Fake testimonials, bot-filled WhatsApp groups |
| Authority | Impersonate banks, government, famous investors |
| Liking | Romance building, mirroring, finding common ground |
| Scarcity | "Only 3 spots left," countdown timers, regulatory deadlines |
| Unity | "We're in this together," in-group financial destiny |

### BITE Model of Coercive Control
*(Steven Hassan, Combating Cult Mind Control, 1988)*

Originally developed for cult analysis — directly applicable to scam detection. Key signal: victim is systematically cut off from outside validation (friends, real bank, search engine). Information monopoly is the clearest structural red flag.

> Note: BITE model is widely used in practitioner contexts; academic consensus on its validity is limited.

### Scam Lifecycle Phases

```
RECRUITMENT → TRUST BUILDING → GROOMING → ESCALATION → EXTRACTION → EXIT
```

Knowing the phase determines the intervention strategy and the remaining financial exposure.

---

## Scam Playbook

The interface includes a structured behavioral breakdown of three major typologies:

**Romance Scam / Pig Butchering (杀猪盘)**
Six-phase analysis from first contact through disappearance. Includes psychological mechanisms at each stage and detectable signals per phase.

**Investment Fraud**
Authority establishment, FOMO engineering, social proof fabrication, advance fee extraction.

**Authority Impersonation**
Fear induction, isolation and control, asset transfer methods that bypass bank fraud controls.

---

## Technical Architecture

```
User Input (conversation text)
        ↓
Claude claude-sonnet-4-20250514
(Fraud-specialized system prompt with behavioral science framework)
        ↓
Structured JSON:
{
  scam_type, risk_score, risk_level,
  psychological_tactics[], red_flags[],
  phase, intervention, confidence
}
        ↓
Frontend visualization
```

**Stack:** HTML / CSS / Vanilla JavaScript + Anthropic API  
Single-file deployment — no backend, no build step.

---

## Limitations

- **Not production-ready.** A deployed system would require adversarial robustness testing, latency optimization, and fine-tuning on labeled case data.
- **No ground truth validation.** Detection accuracy is not benchmarked against a labeled dataset — that would be the next step.
- **LLM hallucination risk.** Edge cases and ambiguous inputs may be misclassified. Human review required in any real deployment.

---

## About

**Dan Fang** | danfly8888@gmail.com | Ramat Gan, Israel  
AI-Driven Fraud & Risk Intelligence Specialist

[← Back to Portfolio](../README.md)

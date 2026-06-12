# Isnad-Inspired Provenance Verification: A Framework for LLM Prompt Injection Defence

**Author:** Huma Shaukat  
**Date:** June 2026  
**Affiliation:** Certificate IV in Cybersecurity, Holmesglen TAFE, Melbourne, Australia  
**Repository:** github.com/HumaShaukat/isnad-ai-provenance

---

## Abstract

This paper proposes a novel defensive framework for Large Language Model (LLM) security, drawing on the Islamic hadith authentication methodology known as *isnad* — the chain of narrators. Prompt injection attacks, ranked #1 in the OWASP LLM Top 10, succeed primarily because LLMs cannot reliably distinguish legitimate system instructions from malicious user-injected instructions. This paper argues that the 1,400-year-old isnad verification methodology independently solves the core problem of instruction provenance — and that mapping its principles onto LLM input pipelines offers a structured, auditable defence against prompt injection and multi-turn crescendo attacks.

---

## 1. The Problem: Prompt Injection

Large Language Models operate on instructions delivered through a layered input pipeline:System Prompt (developer/operator instructions)
↓
User Prompt (end user input)
↓
Model Processing
↓
OutputPrompt injection occurs when malicious instructions embedded in user input override or corrupt legitimate system instructions. The model cannot reliably distinguish the source of authority between the two layers.

Current attack techniques include:

- **Direct prompt injection** — explicit override commands in user input
- **Indirect prompt injection** — malicious instructions embedded in external content the model reads
- **Multi-turn crescendo attacks** — individually harmless messages that accumulate into a dangerous instruction set across a conversation
- **Tokenade attacks** — zero-width characters, emoji encoding, and Unicode manipulation that disguise malicious intent from surface-level classifiers

These attacks share a common root cause: **the absence of instruction provenance verification**. The model processes *what* was said without verifying *who said it, through what chain, and with what authority*.

---

## 2. Islamic Isnad Methodology

In Islamic hadith sciences, isnad (إسناد) refers to the chain of narrators through which a saying or action of the Prophet Muhammad ﷺ is transmitted. Before a hadith is accepted as authentic, every link in the chain must be verified.

### Core Isnad Verification Criteria:

| Criterion | Description |
|-----------|-------------|
| **Ittisal al-sanad** | Chain continuity — no missing links |
| **Adalah** | Moral trustworthiness of each narrator |
| **Dabt** | Memory reliability and accuracy of each narrator |
| **Shudhudh** | Absence of anomaly — does this contradict stronger chains? |
| **Illah** | Absence of hidden defects — subtle corruptions |

A hadith is rejected if any single narrator in the chain is unknown, untrustworthy, or if the chain contains a gap. The content alone — no matter how plausible — cannot override a broken chain.

This is the key insight: **provenance determines authority, not content

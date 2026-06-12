# Isnad-Inspired Provenance Verification: A Framework for LLM Prompt Injection Defence

**Author:** Huma Shaukat
**Date:** June 2026
**Affiliation:** Certificate IV in Cybersecurity, Holmesglen TAFE, Melbourne, Australia
**GitHub:** github.com/HumaShaukat/isnad-ai-provenance

---

## Abstract

This paper proposes a novel defensive framework for Large Language Model (LLM) security, drawing on the Islamic hadith authentication methodology known as isnad — the chain of narrators. Prompt injection attacks, ranked #1 in the OWASP LLM Top 10, succeed primarily because LLMs cannot reliably distinguish legitimate system instructions from malicious user-injected instructions. This paper argues that the 1,400-year-old isnad verification methodology independently solves the core problem of instruction provenance — and that mapping its principles onto LLM input pipelines offers a structured, auditable defence against prompt injection and multi-turn crescendo attacks.

---

## 1. The Problem: Prompt Injection

Large Language Models operate on instructions delivered through a layered input pipeline:

- System Prompt — developer and operator instructions
- User Prompt — end user input
- Model Processing
- Output

Prompt injection occurs when malicious instructions embedded in user input override or corrupt legitimate system instructions. The model cannot reliably distinguish the source of authority between layers.

Current attack techniques include:

- **Direct prompt injection** — explicit override commands in user input
- **Indirect prompt injection** — malicious instructions embedded in external content the model reads
- **Multi-turn crescendo attacks** — individually harmless messages that accumulate into a dangerous instruction set across a conversation
- **Tokenade attacks** — zero-width characters, emoji encoding, and Unicode manipulation that disguise malicious intent from surface-level classifiers

These attacks share a common root cause: the absence of instruction provenance verification. The model processes what was said without verifying who said it, through what chain, and with what authority.

---

## 2. Islamic Isnad Methodology

In Islamic hadith sciences, isnad (إسناد) refers to the chain of narrators through which a saying or action of the Prophet Muhammad ﷺ is transmitted. Before a hadith is accepted as authentic, every link in the chain must be verified.

### Core Isnad Verification Criteria

| Criterion | Arabic Term | Description |
|-----------|-------------|-------------|
| Chain continuity | Ittisal al-sanad | No missing links |
| Trustworthiness | Adalah | Moral reliability of each narrator |
| Accuracy | Dabt | Memory precision of each narrator |
| Absence of anomaly | Shudhudh | Does not contradict stronger chains |
| Absence of hidden defect | Illah | No subtle corruptions present |

A hadith is rejected if any single narrator is unknown, untrustworthy, or if the chain contains a gap. The content alone — no matter how plausible — cannot override a broken chain.

**Core insight: provenance determines authority, not content.**

---

## 3. The Mapping: Isnad Applied to LLM Input Pipelines

| Isnad Concept | LLM Security Equivalent |
|---------------|------------------------|
| Chain of narrators | Instruction origin chain: provider, operator, user |
| Ittisal al-sanad | No unverified instruction source in pipeline |
| Adalah | Cryptographic verification of instruction source |
| Dabt | Instruction integrity — has this been tampered with? |
| Shudhudh | Does this contradict the higher-authority system prompt? |
| Illah | Tokenade detection — hidden encoding, zero-width characters |
| Matn (content) | The actual prompt text |
| Sanad (chain) | Provenance metadata attached to the prompt |

**Key principle: a plausible-sounding instruction with broken provenance must be rejected, regardless of content.**

---

## 4. Proposed Framework: Isnad-Inspired Prompt Provenance Verification (IPPV)

### 4.1 Three-Layer Authority Hierarchy

- **Tier 1 — Model Provider** (Anthropic/OpenAI): Core alignment rules. Highest authority. Cannot be overridden.
- **Tier 2 — Operator**: System prompt from verified API caller. Medium authority.
- **Tier 3 — User**: Runtime input. Lowest authority. Cannot override Tier 1 or Tier 2.

Any instruction claiming Tier 1 authority arriving through a Tier 3 channel is automatically rejected — equivalent to a fabricated hadith.

### 4.2 Conversational Threat Accumulation

Current classifiers check individual prompts in isolation. This framework proposes chain-level verification across an entire conversation.

Multi-turn crescendo attacks work because each message appears safe individually. IPPV proposes a running provenance score across the full conversation chain — flagging when cumulative instruction patterns attempt to migrate authority upward from Tier 3 to Tier 1.

### 4.3 Semantic Zone Classification

User inputs are classified into three zones before safety evaluation:

- **Green** — safe combinations, no authority conflict
- **Blue** — ambiguous, context-dependent, requires chain verification
- **Red** — dangerous regardless of framing, rejected at provenance layer

Zone classification operates on semantic meaning, not surface text — preventing tokenade and multilingual bypass attacks.

---

## 5. Why This Framework Addresses Current Gaps

| Current Gap | IPPV Response |
|-------------|---------------|
| Models trust content over source | Isnad principle: source determines authority |
| Single-prompt classifiers miss crescendo attacks | Conversational chain scoring |
| Surface text classifiers miss tokenades | Semantic zone classification |
| No audit trail for instruction origin | Provenance metadata as auditable record |

---

## 6. Governance and Compliance Implications

A live, auditable instruction provenance chain is not only a security tool — it is a compliance instrument. Regulatory frameworks including NIST AI RMF and ISO 42001 require transparency and accountability in AI decision-making. IPPV provides a mechanism for:

- Auditing what instructions the model received and from what authority level
- Demonstrating that safety controls were not bypassed
- Producing evidence trails for incident response

This positions IPPV as both a technical defence and a governance framework.

---

## 7. Conclusion

The Islamic isnad methodology, developed over 1,400 years ago to solve the problem of fabricated narrations, maps precisely onto the core vulnerability exploited by modern prompt injection attacks. Both problems share the same root: the inability to verify the chain of authority behind a claimed instruction.

This paper proposes that LLM safety researchers formalise instruction provenance verification using isnad-derived principles — not as metaphor, but as a rigorous structural framework. The convergence of Islamic epistemology and AI safety research represents a rare cross-domain insight with practical defensive application.

---

## 8. Author Note

This framework was developed independently by Huma Shaukat in June 2026 during her Certificate IV in Cybersecurity studies, arising from original thinking about cross-domain pattern recognition between Islamic hadith authentication and AI prompt injection vulnerabilities.

---

## References

- OWASP LLM Top 10: https://owasp.org/www-project-top-10-for-large-language-model-applications/
- NIST AI Risk Management Framework: https://www.nist.gov/system/files/documents/2023/01/26/AI RMF 1.0.pdf
- Ibn Hajar al-Asqalani, Nukhbat al-Fikr (classical isnad methodology)
- Anthropic Constitutional AI: https://www.anthropic.com/research/constitutional-ai-harmlessness-from-ai-feedback
- MITRE ATLAS: https://atlas.mitre.org

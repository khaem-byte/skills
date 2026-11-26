---
name: grill-with-docs
description: Grill the user about a plan or design, one question card at a time, recording terms in GLOSSARY.md and decisions in ADRs as they settle. Use when the user asks for grill-with-docs, or for a grilling that leaves docs in the repo.
---

Call the Skill tool twice, for "grilling" and "domain-modeling".

Run the grilling interview with the domain-modeling discipline woven in:

- **Write as decisions land.** Each time an answer settles a term or an ADR-worthy decision, update `GLOSSARY.md` or write the ADR before asking the next question.
- **Cross-examine the language too.** A term that conflicts with `GLOSSARY.md`, or one word doing two jobs, is a contradiction: quote both uses and make the user pick.
- **Link from the decision record.** In `grill-<topic>.md`, point at each ADR and glossary term written this session; restate only the decisions that got no ADR.

Where "domain-modeling" is unavailable, keep the same paper trail yourself: domain terms, one definition each and free of implementation detail, in `GLOSSARY.md` at the repo root; an ADR in `docs/adr/NNNN-<slug>.md` for each decision that is hard to reverse, surprising without context, and the result of a real trade-off. Create each file when its first entry exists.

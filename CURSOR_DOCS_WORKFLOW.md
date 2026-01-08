# Cursor Docs Workflow

This document defines the strict rules for generating and updating public documentation in this repository.

---

## Golden Rule

**Public docs must be written ONLY using `_private/source.md` as the source of truth.**

---

## Rules

### 1. Single Source of Truth

- All public documentation content MUST be derived from `_private/source.md`
- Never invent, guess, or assume product details
- If information is not in `_private/source.md`, it cannot go in public docs

### 2. Missing Information

- If required info is missing from `_private/source.md`: add `<!-- TODO: [description] -->` placeholders
- Never guess or fill gaps with assumptions
- Flag missing info clearly so it can be addressed

### 3. Forbidden Content

The following must NEVER appear in public docs:

- Real API endpoints or URLs
- Secrets, API keys, or tokens
- Internal database schemas
- Stripe configuration details or webhook secrets
- Internal system architecture beyond what's in source.md
- Any information not explicitly in `_private/source.md`

### 4. Rewrite Order

When updating public docs, follow this order:

1. `README.md`
2. `docs/quickstart.md`
3. `docs/merchant-of-record.md`
4. `docs/how-it-works.md`
5. `docs/why-not-stripe.md`
6. `docs/faq.md`
7. `docs/roadmap.md`

---

## Reusable Prompt Snippet

Copy and paste this prompt when asking Cursor to rewrite any public doc:

```
You are rewriting public documentation for Billai.

STRICT RULES:
1. Use ONLY `_private/source.md` as the source of truth
2. If info is missing: add <!-- TODO: [description] --> placeholders, NEVER guess
3. NEVER include: real endpoints, secrets, internal schemas, Stripe config details
4. Do NOT invent product details or capabilities
5. Maintain existing structure/formatting where appropriate
6. Add "not legal advice" disclaimers where discussing MoR/tax/compliance

The file to rewrite: [INSERT FILENAME]

Read `_private/source.md` first, then rewrite the target file using only that information.
```

---

## Verification Checklist

Before committing any doc changes:

- [ ] All content traces back to `_private/source.md`
- [ ] No real endpoints, secrets, or internal details
- [ ] TODOs added for any missing information
- [ ] Legal disclaimers present where needed
- [ ] `_private/` folder is NOT being committed


# BillAI

**Monetize your ChatGPT app in 5 minutes. No company, no Stripe setup needed.**

BillAI is a SaaS monetization platform for ChatGPT and MCP app developers. It provides access control and entitlements through a simple SDK, with hosted checkout powered by Stripe Connect.

---

## The Problem

Building a monetized ChatGPT or MCP app today means setting up a company, configuring Stripe, managing payment flows, and building access control logic—before you can charge your first user.

Most developers want to focus on their product, not payment infrastructure.

---

## What BillAI Does

- **Hosted Checkout** — Stripe Connect Express integration; no need for your own company or Stripe account
- **Access Control SDK** — Simple API for feature gating
- **Entitlements Engine** — User → plan → features → access status
- **Developer Dashboard** — Manage plans, view users, configure API keys
- **Auto-logging** — Every access check is logged for analytics
- **One-time Purchases** — v1 supports one-time payment flows
- **Feature Flags** — Boolean features (true/false access)
- **Usage-Based Features** — Numeric features with limits (e.g., API calls per month)

---

## Who This Is For

- **ChatGPT app developers** — building applications on top of ChatGPT
- **MCP (Model Context Protocol) app developers** — building MCP servers
- Developers who don't have existing Stripe accounts or companies
- Developers who want to start monetizing quickly without complex payment infrastructure setup

---

## Who This Is NOT For

> **TODO:** Non-fit criteria are not explicitly defined in current product documentation.

---

## High-Level Monetization Flow

### Developer Setup

1. Sign up on BillAI dashboard
2. Complete Stripe Express onboarding (identity verification for payouts)
3. Create your app and get credentials
4. Define pricing plans with features
5. Integrate the SDK into your ChatGPT/MCP app

### End-User Payment Flow

1. User requests a paid feature in your app
2. Your app checks if the user has access
3. If no access exists, your app creates a checkout session
4. User completes payment via Stripe Checkout
5. Payment confirmation updates entitlement status
6. User gains access to the paid feature

---

## Merchant of Record Model

> **High-level overview. Not legal advice.**

**The developer is the Merchant of Record:**

- Receives customer funds directly
- Is responsible for refunds and chargebacks
- Is the party responsible to the end customer for the purchased product or service

**BillAI's role:**

- Provides technical infrastructure for payment processing
- Collects a platform application fee
- Does not receive customer funds as the seller
- Does not assume seller obligations
- Is not the merchant of record

**Payment architecture:**

- Payments use Stripe Connect Express with direct charges
- Funds flow directly to the developer's connected account
- Customer card statements reflect the developer's Stripe connected account

---

## Limitations / Non-Goals

**Explicitly out of scope for v1:**

- ❌ Deliverable tracking or storage — BillAI is billing infrastructure, not content delivery
- ❌ Subscription lifecycle management — v1 is one-time purchases only
- ❌ Multi-product bundles — One product per checkout
- ❌ Refund processing via API — Handle manually or via Stripe dashboard
- ❌ Checkout UI customization — Fixed UI; no theming API
- ❌ Webhook registration API — Webhooks configured per-app in dashboard
- ❌ Session deletion/expiration control
- ❌ Usage-based metering on purchases (separate from feature usage limits)

**SDK design boundaries:**

- Does NOT store payment state locally
- Does NOT implement automatic polling loops
- Does NOT redirect users to checkout (returns URL for client to present)
- Does NOT auto-create checkout sessions

---

## Documentation

- [Quickstart](docs/quickstart.md)
- [How It Works](docs/how-it-works.md)
- [Merchant of Record](docs/merchant-of-record.md)
- [Why Not Stripe Directly?](docs/why-not-stripe.md)
- [FAQ](docs/faq.md)
- [Roadmap](docs/roadmap.md)

---

## Business Model

- **Platform fee:** 7% on transactions
- **No monthly fees** — only pay when transactions occur
- **Fee timing:** Deducted automatically at payment time
- **Stripe fees:** Borne by the developer (connected account), not BillAI

---

## Contact

**Email:** contact@billai.com

**Legal entity:** Intellex SAS (France)

# Quickstart

This guide walks you through the conceptual steps to monetize a ChatGPT or MCP app using BillAI. BillAI provides access control and entitlements through an SDK, with hosted checkout powered by Stripe Connect. You do not need your own Stripe account or company to get started.

---

## Prerequisites

Before you begin, you need:

- A ChatGPT app or MCP server you want to monetize
- A way to identify your users (a stable `user_id` you control)
- The ability to complete Stripe Express onboarding (identity verification for payouts)

---

## Conceptual Steps

### 1. Create a Monetizable Product

Sign up on the BillAI dashboard and create an app. This gives you an API key (`sk_live_xxx` or `sk_test_xxx`) and an App ID (`app_xxx`).

Within your app, create a plan that defines what you are selling. A plan contains features—these can be boolean (true/false access) or numeric (usage limits).

> **Note:** In the API, `product_id` refers to a plan. These terms are used interchangeably.

### 2. Define Pricing

Configure pricing for your plan in the dashboard. BillAI v1 supports **one-time purchases** only.

TODO: Exact dashboard steps for configuring pricing are not documented in source material.

### 3. Connect Payouts

Complete Stripe Express onboarding through the dashboard. This verifies your identity and sets up your connected Stripe account to receive funds.

As the developer, you are the **Merchant of Record**. Customer funds flow directly to your connected Stripe account. You are responsible for the product or service, including handling refunds and chargebacks.

### 4. Connect Monetization to Your App

Integrate the `@billai/sdk` into your application.

When a user attempts to access a paid feature:

1. Check if the user has access by calling the purchase status endpoint
2. If the user does not have access, request a checkout session
3. Present the returned checkout URL to the user (the SDK returns a URL; it does not redirect automatically)
4. The user completes payment on the hosted Stripe Checkout page

### 5. Handle Access Control

Use the SDK to check access before delivering paid functionality:

```
Conceptual step: access.check(userId, feature)
```

- `has_access` indicates whether the user has paid for the product
- `granted` indicates whether the user's plan allows a specific feature
- Access state is authoritative **at request time only**—re-check access for every gated operation

---

## What Happens After a User Pays

1. The user completes payment on Stripe Checkout
2. Stripe sends a webhook to BillAI
3. BillAI updates the user's entitlement status
4. Subsequent access checks return `has_access: true`
5. Your app delivers the paid feature

Funds are deposited directly into your connected Stripe account, minus the platform fee (7%) and Stripe's processing fees.

---

## What This Quickstart Does NOT Cover

- **Subscription lifecycle management** — v1 supports one-time purchases only
- **Multi-product bundles** — one `productId` per checkout
- **Refund processing via API** — handle refunds manually or via the Stripe dashboard
- **Checkout UI customization** — the hosted checkout has a fixed UI
- **Webhook registration via API** — webhooks are configured per-app in the dashboard
- **Usage-based metering on purchases** — this is separate from feature usage limits

---

## Next Steps

- [How It Works](./how-it-works.md) — Understand the full architecture
- [Merchant of Record](./merchant-of-record.md) — Your responsibilities as the seller
- [FAQ](./faq.md) — Common questions answered

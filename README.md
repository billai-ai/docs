# BillAI

**Monetize your AI app in minutes. No Stripe account. No company. No billing code.**

---

## The Problem

You built a cool AI app. Maybe it's a ChatGPT wrapper, a code assistant, or something weird and wonderful. Now you want to charge for it.

Here's what you're facing:

- Set up a Stripe account (requires business verification)
- Figure out usage-based billing for AI tokens
- Handle failed payments, refunds, chargebacks
- Deal with sales tax, VAT, invoicing
- Build a subscription management UI
- Worry about PCI compliance

You just wanted to ship a product. Now you're running a payments company.

## The Solution

BillAI handles all of that. You focus on your AI app; we handle everything money-related.

```
Your AI App  →  BillAI  →  Money in your bank account
```

That's it. We're the [merchant of record](./merchant-of-record.md), which means we legally sell your product and pay you out. You never touch payments directly.

## Who This Is For

✅ Solo developers shipping AI products  
✅ Indie hackers who want to validate before incorporating  
✅ Side projects that might become real businesses  
✅ Developers outside the US/EU who struggle with Stripe  
✅ Anyone tired of billing code eating into build time  

## Who This Is NOT For

❌ Enterprise companies with existing billing infrastructure  
❌ Apps requiring complex B2B contracts or custom invoicing  
❌ Highly regulated industries (healthcare, finance)  
❌ Products that need white-label payment processing  
❌ If you enjoy setting up Stripe webhooks  

## Quick Start (3 Steps)

**Step 1: Define your product**

Tell us what you're selling—a subscription, per-use credits, or one-time purchase.

```
createProduct({
  name: "Pro Plan",
  type: "subscription",
  price: "$19/month"
})
```

**Step 2: Add a payment link**

Drop our hosted checkout link into your app. No frontend code needed.

```
<a href="https://pay.billai.dev/your-product">Upgrade to Pro</a>
```

**Step 3: Check access**

When a user tries to access paid features, check if they've paid.

```
const access = await checkAccess(userId)
if (access.paid) {
  // Show the good stuff
}
```

That's the whole integration. [Full quickstart guide →](./quickstart.md)

## How It Works

We act as your billing department:

1. **We sell your product** — Customers pay us, not you directly
2. **We handle the mess** — Taxes, refunds, chargebacks, compliance
3. **We pay you** — Regular payouts to your bank account

No Stripe account needed. No business entity required. No billing code to maintain.

[Detailed explanation →](./how-it-works.md)

## Documentation

| Document | Description |
|----------|-------------|
| [Quickstart](./quickstart.md) | Get up and running conceptually |
| [How It Works](./how-it-works.md) | Understand the architecture |
| [Why Not Stripe?](./why-not-stripe.md) | Honest comparison |
| [Merchant of Record](./merchant-of-record.md) | Legal structure explained |
| [FAQ](./faq.md) | Common questions and edge cases |
| [Roadmap](./roadmap.md) | What we're building next |

## Pricing Philosophy

We take a percentage of what you earn. If you make nothing, you pay nothing.

No monthly fees. No setup costs. No minimum commitments.

The exact percentage depends on your volume—reach out when you're ready.

## Not Sure Yet?

That's fine. Here's how most people evaluate us:

1. Read the [FAQ](./faq.md) to see if we've answered your concerns
2. Check [Why Not Stripe?](./why-not-stripe.md) to understand the tradeoffs
3. Look at the [Roadmap](./roadmap.md) to see where we're headed

## Contact

Questions? Concerns? Want to roast our approach?

- Email: contact@billai.io


---

*BillAI is built by developers who got tired of writing billing code instead of shipping features.*


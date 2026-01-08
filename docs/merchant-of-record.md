# Merchant of Record

What it means, why it matters, and how it affects you.

> **Disclaimer:** This is a high-level explanation, not legal advice. Consult a professional for your specific situation.

---

## The Simple Explanation

When someone buys your product through BillAI, they're legally buying from **us**, not from you.

- The charge on their credit card says "BillAI"
- The receipt comes from BillAI
- If there's a refund dispute, it's with BillAI
- Tax obligations are BillAI's responsibility

You're the **vendor**. We're the **merchant**.

We then pay you your share, minus our fee.

## Why This Matters

### For You (The Developer)

**Benefits:**
- No business entity required to sell
- No payment processor account needed
- No tax registration in multiple jurisdictions
- No PCI compliance burden
- No chargeback liability

**Tradeoffs:**
- Your brand isn't on the receipt
- You don't own the direct payment relationship
- Payouts happen on our schedule, not instantly

### For Your Customers

**What they see:**
- A professional checkout experience
- "BillAI" on their bank statement
- Standard consumer protections
- Easy refund process (through us)

**What they don't see:**
- Any difference in the product experience
- Complicated tax calculations
- Your billing infrastructure (or lack thereof)

## How Other Companies Do This

This model isn't new. You've used it:

| Platform | Who's the Merchant | Who's the Vendor |
|----------|-------------------|------------------|
| App Store | Apple | App developers |
| Steam | Valve | Game developers |
| Gumroad | Gumroad | Creators |
| Paddle | Paddle | Software companies |
| BillAI | BillAI | You |

When you buy an iPhone app, Apple is the merchant. The developer gets a payout. Same concept.

## What This Means Legally

> Again: not legal advice. General information only.

### Sales Tax / VAT

- BillAI is responsible for collecting and remitting
- This includes US sales tax, EU VAT, and other jurisdictions
- You don't need tax registrations in places where we sell

### Business Entity

- You don't need an LLC, corporation, or any formal entity
- You can receive payouts as an individual
- When/if you form a company, nothing changes on our end

### Invoices and Receipts

- BillAI issues these to your customers
- We're the legal seller, so they come from us
- Customers can request invoices through our system

### Refunds and Chargebacks

- We handle refund requests
- We respond to payment disputes
- We absorb chargeback fees
- You're notified but not directly involved

### Income Taxes

- You still owe income tax on your earnings
- We provide documentation for your records
- How you report this depends on your tax situation
- Consult an accountant for specifics

## Payout Structure

Here's the money flow:

```
Customer pays $100
       │
       ▼
BillAI receives $100
       │
       ├── Deduct: Payment processing costs
       ├── Deduct: Tax obligations (remitted to authorities)
       ├── Deduct: BillAI fee
       │
       ▼
You receive: Net payout
```

You get a single, clean payout. No separate tax remittance, no processing fees to track.

## What We Handle vs. What We Don't

### We Handle:
- Payment processing and security
- Tax calculation and remittance
- Refunds and chargebacks
- Receipt and invoice generation
- Currency conversion
- Payment method support

### We Don't Handle:
- Your product or service delivery
- Customer support for your product
- Your income tax obligations
- Legal compliance for your product itself
- Any non-billing business operations

## Common Questions

### "Do I need a business license?"

Generally no, just to sell through us. However:
- Local regulations vary
- Some jurisdictions have specific requirements
- If you're making significant income, you may want/need a formal entity anyway

Check with a local professional.

### "What about my existing LLC/company?"

Works fine. You can receive payouts to a business bank account. Nothing changes on our end.

### "Can customers get a receipt with my business name?"

Currently, receipts come from BillAI. This is part of the merchant-of-record model. If you need white-label receipts, this model may not be right for you.

### "What if a customer disputes a charge?"

We handle it. We'll reach out if we need product-related information, but the dispute process is on us.

### "Am I liable if something goes wrong with a payment?"

For payment-related issues, no. We're the merchant, so payment liability is ours. 

For product-related issues (your app doesn't work, violates terms, etc.), that's on you.

## When MoR Doesn't Work

Merchant of Record isn't right for every situation:

- **B2B with procurement requirements** — Enterprises often need to buy from a specific entity
- **Highly regulated products** — Some industries have specific seller requirements
- **White-label requirements** — If your brand must be everywhere
- **Complex contractual relationships** — Custom terms, SLAs, etc.

## The Bottom Line

Merchant of Record lets you sell software without becoming a payments/tax/compliance expert. The tradeoff is some loss of control and visibility.

For indie developers and small teams, this tradeoff is almost always worth it. You're outsourcing the parts of the business that don't make your product better.

---

## Learn More

- [How It Works](./how-it-works.md) — Technical overview
- [Why Not Stripe?](./why-not-stripe.md) — Compare approaches
- [FAQ](./faq.md) — More questions answered

Questions about MoR specifically? hello@billai.dev


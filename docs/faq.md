# FAQ

Real questions, honest answers.

---

## Getting Started

### Do I need a company to use BillAI?

No. You can sign up and receive payouts as an individual. Many of our users are solo developers without formal business entities.

If you have a company, that works too—we can pay out to business accounts.

### What countries do you support?

We support payouts to most countries where standard banking works. Some regions have restrictions due to international banking limitations.

Check our signup flow for the current list, or email us if you're unsure.

### How long does setup take?

Most developers are set up and ready to accept payments within an hour. The actual integration (adding payment links, checking access) takes minutes.

### Is there a free tier or trial?

We don't charge until you make money. No monthly fees, no setup costs. If you're making $0, you pay $0.

---

## Payments & Pricing

### How much do you charge?

We take a percentage of each transaction. The exact rate depends on your volume and use case.

We're transparent about this during onboarding. No hidden fees.

### When do I get paid?

Payouts happen on a regular schedule (timing varies by region and payment method). It's not instant, but it's predictable.

Think of it like any other payment platform—there's a settlement period.

### What payment methods do customers have?

- Credit and debit cards (Visa, Mastercard, Amex)
- Apple Pay
- Google Pay
- Additional regional methods depending on customer location

### What currencies do you support?

Customers can pay in their local currency. You receive payouts in your preferred currency.

We handle the conversion.

### What happens if a payment fails?

We automatically retry failed payments with smart timing. Customers get notified. You don't have to do anything.

If payment ultimately fails, access is revoked after a grace period.

---

## Features & Limitations

### Can I offer free trials?

Yes. You can configure trial periods for subscriptions. Customers enter payment info upfront, but aren't charged until the trial ends.

### Can I offer discounts or coupons?

Yes. You can create discount codes through the dashboard.

### Can I do one-time purchases AND subscriptions?

Yes. You can have multiple products with different billing models.

### Can I change prices for existing subscribers?

You can change prices for new subscribers at any time. For existing subscribers, you have options:

- Grandfather them at the old price
- Migrate them to the new price (we help with communication)

### Do you support team/organization billing?

Not yet. Currently, billing is per-user. Team billing is on our roadmap.

### Can customers upgrade/downgrade plans?

Yes. We handle proration automatically.

### Do you support refunds?

Yes. You can issue refunds through the dashboard, or customers can request them directly from us.

---

## Technical

### Do I need to handle webhooks?

No. Our model is pull-based—you call `checkAccess()` when you need to know payment status. No webhook handlers to build.

If you *want* webhooks, we can discuss it, but most use cases don't need them.

### How do I identify users?

You pass a user identifier (email, user ID, etc.) when customers check out. That same identifier is used when checking access.

We don't manage your user accounts—just the association between your users and their payment status.

### What if your API is down?

Cache access status locally with a reasonable TTL. If our API is unreachable, fall back to cached data.

We have high uptime, but design defensively.

### Is there rate limiting?

Yes, but generous. Normal usage won't hit limits. If you're doing something unusual (millions of requests), talk to us.

### Do you have SDKs?

We provide SDKs for popular languages/frameworks. For everything else, it's a simple REST API.

---

## Security & Compliance

### Is this PCI compliant?

Yes. We handle all payment data. Card numbers never touch your servers.

You don't need to worry about PCI compliance.

### Where is data stored?

Payment data is stored securely with industry-standard encryption. We don't store your users' app data—only billing-related information.

### Can I see my customers' payment methods?

No. You can see that they paid, when, and for what. You can't see card numbers or payment details.

This is intentional—it keeps you out of PCI scope.

### What about GDPR?

We're compliant. Customers can request their billing data be deleted. We have a DPA available if you need one.

---

## Business & Legal

### Who owns the customer relationship?

It's nuanced:

- **Product relationship:** You own this entirely
- **Payment relationship:** We're the merchant of record

Your customers are your customers. We just handle the money part.

### What if a customer wants an invoice?

They can request invoices from us. Invoices come from BillAI (we're the merchant of record).

### What about chargebacks?

We handle them. We'll reach out if we need information about the transaction, but the dispute process is our responsibility.

We also absorb chargeback fees.

### Can I use this for physical products?

We're optimized for digital products and services. Physical products have shipping, inventory, and return logistics we don't handle.

Technically possible, but not recommended.

### What products are NOT allowed?

Standard restrictions apply:
- Illegal products or services
- Adult content (with some exceptions—ask us)
- Gambling
- Certain regulated industries

We'll let you know during onboarding if your product is a concern.

---

## Comparisons

### How is this different from Stripe?

Stripe is a payment processor. You're the merchant. You handle taxes, compliance, disputes.

We're a merchant of record. We're the merchant. We handle all that stuff.

[Full comparison →](./why-not-stripe.md)

### How is this different from Gumroad?

Similar model (both MoR), but different focus:

- Gumroad: Digital products, downloads, creators
- BillAI: SaaS, AI apps, recurring revenue, usage-based billing

We're built for developers building software products.

### How is this different from Paddle?

Similar model. Paddle is more enterprise-focused with longer onboarding. We're built for indie developers who want to ship fast.

### Can I migrate from Stripe?

Yes, but there's no automated migration. You'd:

1. Set up products in BillAI
2. Point new customers to BillAI checkout
3. Optionally migrate existing customers (we can help)

For small products, many developers just start fresh with new customers.

---

## Support

### How do I get help?

- Email: hello@billai.dev
- Twitter/X: @billai_dev

We're a small team, so response times vary. But we read everything.

### Do you have live chat?

Not currently. Email is the best way to reach us.

### What if something breaks?

Email us. We'll fix it fast. Payments are important—we take reliability seriously.

---

## Still Have Questions?

Email us: hello@billai.dev

We're happy to chat about your use case before you commit to anything.


# How It Works

A plain-English explanation of what BillAI does and how the pieces fit together.

---

## The Big Picture

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Your App  │────▶│   BillAI    │────▶│  Your Bank  │
└─────────────┘     └─────────────┘     └─────────────┘
       │                   │
       │                   ▼
       │            ┌─────────────┐
       └───────────▶│  Customer   │
                    └─────────────┘
```

**Your app** tells BillAI what to sell.  
**Customers** pay BillAI directly.  
**BillAI** handles everything in the middle.  
**You** receive payouts.

## The Merchant of Record Model

This is the key concept. BillAI is the "merchant of record" for your sales.

In plain terms:
- When a customer buys your product, they're legally buying from BillAI
- We issue the receipt, handle refunds, deal with chargebacks
- We're responsible for sales tax, VAT, and compliance
- We then pay you your share

This is how app stores work. When you buy an app on the App Store, you're buying from Apple, not the developer. Apple handles the money stuff and pays out the developer.

[More details on Merchant of Record →](./merchant-of-record.md)

## What We Handle

### Payment Processing
- Credit cards, debit cards
- Apple Pay, Google Pay
- Regional payment methods
- Currency conversion

### Billing Operations
- Subscription management
- Usage tracking and metering
- Failed payment recovery
- Proration on plan changes

### Compliance
- PCI DSS compliance (you never touch card data)
- Sales tax calculation and remittance
- VAT handling for EU customers
- Invoice generation

### Customer Service (Billing-Related)
- Refund requests
- Payment disputes
- Receipt inquiries

## What You Handle

### Your Product
- Building the actual thing people pay for
- User authentication
- Feature access control

### Customer Relationships
- Support for product issues (not billing)
- Communication with your users
- Product decisions

## The Data Flow

### When Someone Pays

1. User clicks your payment link
2. They land on BillAI's hosted checkout
3. They enter payment info (we store it, not you)
4. Payment processes
5. BillAI records the purchase
6. Your `checkAccess()` call now returns `active: true`

### When You Check Access

1. Your app calls `checkAccess(userId)`
2. BillAI looks up their payment status
3. Returns active/inactive with relevant details
4. Your app decides what to show

### When You Get Paid

1. We collect payments throughout the period
2. We deduct our fee and any refunds
3. We initiate a transfer to your bank
4. You receive funds (timing depends on your region)

## Usage-Based Billing Flow

For AI apps, usage-based pricing often makes more sense than flat subscriptions.

```
User makes request
       │
       ▼
Your app processes it
       │
       ▼
Report usage to BillAI ──▶ billai.reportUsage({ units: 1 })
       │
       ▼
BillAI tracks cumulative usage
       │
       ▼
End of billing period: BillAI charges based on total usage
```

You don't need to track usage yourself. Just report each unit as it happens.

## Security Model

### What We Store
- Customer payment methods (tokenized)
- Purchase history
- Usage records

### What We Don't Store
- Your users' app data
- Your product content
- Anything beyond billing

### What You Store
- Mapping of your user IDs to paid status (via our API)
- That's optional—you can just call our API each time

## Failure Handling

### Payment Fails
- We retry automatically with smart timing
- We notify the customer
- Access doesn't immediately revoke (grace period)
- You can query the status if you want to handle it specially

### Our Service Goes Down
- We have status pages you can monitor
- Design your app to degrade gracefully
- Cache access status locally with reasonable TTL

### You Need a Refund Processed
- Customer contacts us directly, or
- You can trigger refunds through the dashboard
- We handle the money movement

## What This Looks Like in Practice

### Simple SaaS App

```
User signs up (free)
       │
       ▼
Uses free tier features
       │
       ▼
Hits paywall ──▶ "Upgrade for $9/month"
       │
       ▼
Clicks link ──▶ BillAI checkout
       │
       ▼
Pays ──▶ Redirected back to your app
       │
       ▼
checkAccess() returns active
       │
       ▼
Premium features unlocked
```

### Usage-Based AI Tool

```
User signs up (free credits included)
       │
       ▼
Makes AI requests ──▶ reportUsage() each time
       │
       ▼
Runs out of credits
       │
       ▼
"Buy 1000 more credits for $10"
       │
       ▼
BillAI checkout ──▶ Credits added
       │
       ▼
Continue using
```

## Comparison to Building It Yourself

| Task | DIY | With BillAI |
|------|-----|-------------|
| Payment processing | Set up Stripe, handle webhooks | Done |
| Subscription logic | Build it | Done |
| Tax compliance | Figure it out per jurisdiction | Done |
| Failed payments | Build retry logic | Done |
| Refunds | Handle manually | Done |
| PCI compliance | Your responsibility | Our responsibility |
| Time to launch | Days to weeks | Minutes |

## Limitations

Be aware of what we don't do:

- **Custom checkout UI** — You use our hosted checkout
- **Complex B2B billing** — No custom contracts, POs, net-30
- **Multi-product bundles** — One product per checkout (for now)
- **White-labeling** — Customers see "BillAI" on their statement

If you need these, you might need Stripe. [See our comparison →](./why-not-stripe.md)

## Next Steps

- [Quickstart](./quickstart.md) — Start integrating
- [FAQ](./faq.md) — Common questions
- [Merchant of Record](./merchant-of-record.md) — Legal details

---

*Still have questions about how it works? Email hello@billai.dev*


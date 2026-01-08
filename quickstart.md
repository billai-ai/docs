# Quickstart

Get from "I want to charge for my AI app" to "people are paying me" as fast as possible.

**Time to integrate: ~15 minutes**

---

## Prerequisites

- An AI app (or any software, really)
- A way to identify your users (email, user ID, etc.)
- A bank account to receive payouts

That's it. No Stripe account. No business registration. No tax ID.

## Step 1: Create Your Product

First, define what you're selling. BillAI supports three models:

### Subscription
```
createProduct({
  name: "Pro Plan",
  type: "subscription",
  interval: "monthly",
  price: 19.00
})
```

### Usage-Based (Pay Per Use)
```
createProduct({
  name: "API Credits",
  type: "usage",
  unitPrice: 0.01,
  unitName: "request"
})
```

### One-Time Purchase
```
createProduct({
  name: "Lifetime Access",
  type: "one-time",
  price: 99.00
})
```

> **Note:** These are conceptual examples. Actual implementation details provided after signup.

## Step 2: Add Payment Links

Once your product exists, you get a hosted checkout page. Add it anywhere:

### Simple Link
```html
<a href="https://pay.billai.dev/your-product-id">
  Upgrade to Pro
</a>
```

### With User Context
```html
<a href="https://pay.billai.dev/your-product-id?user_id=123&email=user@example.com">
  Upgrade to Pro
</a>
```

Passing the user context lets us associate the purchase with your user automatically.

### Redirect After Payment
```html
<a href="https://pay.billai.dev/your-product-id?success_url=https://yourapp.com/welcome">
  Upgrade to Pro
</a>
```

## Step 3: Check Access

When a user tries to access paid features, verify their payment status:

```javascript
// Pseudocode - actual SDK provided after signup
async function canAccessPremiumFeature(userId) {
  const status = await billai.checkAccess({
    userId: userId,
    product: "pro-plan"
  })
  
  return status.active
}
```

### Response Examples

**Active subscription:**
```json
{
  "active": true,
  "type": "subscription",
  "expiresAt": "2024-02-15T00:00:00Z"
}
```

**No access:**
```json
{
  "active": false
}
```

**Usage-based:**
```json
{
  "active": true,
  "type": "usage",
  "remainingCredits": 450
}
```

## Step 4: Track Usage (If Usage-Based)

For pay-per-use products, report usage as it happens:

```javascript
// After processing an AI request
await billai.reportUsage({
  userId: userId,
  product: "api-credits",
  units: 1
})
```

BillAI handles the metering and billing automatically.

## That's It

Seriously. The integration is:

1. One API call to define your product
2. One link for users to pay
3. One API call to check if they paid
4. (Optional) One API call to report usage

No webhooks to handle. No subscription lifecycle management. No proration calculations.

## What Happens Behind the Scenes

When a user clicks your payment link:

1. They see a hosted checkout page (looks professional, we promise)
2. They pay with card, Apple Pay, Google Pay, etc.
3. We process the payment and handle all the tax/compliance stuff
4. The `checkAccess` call immediately returns `active: true`
5. We send you money on a regular schedule

You don't need to care about any of this. It just works.

## Common Patterns

### Soft Paywall
```javascript
if (await canAccessPremiumFeature(userId)) {
  return generateAdvancedResponse()
} else {
  return {
    message: "Upgrade for advanced features",
    upgradeUrl: "https://pay.billai.dev/your-product-id"
  }
}
```

### Hard Paywall
```javascript
if (!await canAccessPremiumFeature(userId)) {
  redirect("https://pay.billai.dev/your-product-id")
}
```

### Metered AI Responses
```javascript
const credits = await billai.getCredits(userId)

if (credits.remaining <= 0) {
  return "Out of credits. Buy more?"
}

const response = await generateAIResponse(prompt)
await billai.reportUsage({ userId, units: 1 })

return response
```

## Next Steps

- [How It Works](./how-it-works.md) — Understand the full picture
- [FAQ](./faq.md) — Common questions answered
- [Why Not Stripe?](./why-not-stripe.md) — Compare your options

---

*Questions about integration? Email hello@billai.dev*


# Merchant of Record

## What "Merchant of Record" Means

The Merchant of Record (MoR) is the legal entity that sells goods or services to the end customer. This entity:

- Appears on customer payment statements
- Receives customer funds directly
- Bears responsibility to the end customer for the purchased product or service
- Handles refunds and chargebacks

## How This Model Applies in BillAI

**The developer is the Merchant of Record.**

When you use BillAI to monetize your application:

- You (the developer) receive customer funds directly into your Stripe connected account
- You are the party responsible to the end customer for the purchased product or service
- Customer card statements reflect your Stripe connected account, not BillAI

**BillAI is not the Merchant of Record.**

BillAI provides technical infrastructure for payment processing and collects a platform application fee. BillAI does not receive customer funds as the seller and does not assume seller obligations.

### Payment Architecture

- Payments use Stripe Connect Express with direct charges
- Products and prices are created inside your connected Stripe account
- Checkout sessions are created in your connected account context
- Funds flow directly to your connected account
- Platform fee is collected via `application_fee_amount` at payment time

## Responsibilities Handled by BillAI

- Technical infrastructure for payment processing
- Hosted checkout sessions via Stripe Connect
- Access control and entitlements management
- Platform fee collection at payment time

## Responsibilities NOT Handled by BillAI

- Acting as the seller to end customers
- Receiving customer funds on your behalf (funds go directly to your account)
- Processing refunds (TODO: clarify if any tooling is provided beyond Stripe dashboard)
- Handling chargebacks on your behalf
- Assuming any seller obligations to end customers

## What Developers Are Still Responsible For

As the Merchant of Record, you are responsible for:

- **Refunds and chargebacks** — Handle these directly via your Stripe dashboard
- **Customer support** — You are the party responsible to the end customer
- **API key security** — Securing your own API keys and user mappings
- **User identity mapping** — Correctly mapping real users to `user_id` identifiers

### Refund Handling

Refund processing via BillAI's API is not available. Handle refunds manually or via your Stripe dashboard.

## Common Misconceptions

| Misconception | Reality |
|---------------|---------|
| "BillAI handles my refunds" | You handle refunds directly via Stripe. BillAI does not process refunds on your behalf. |
| "BillAI is the seller" | BillAI provides infrastructure only. You are the seller and Merchant of Record. |
| "Customers pay BillAI" | Funds flow directly to your connected Stripe account. BillAI collects only a platform fee. |

---

> **Disclaimer:** This is a high-level overview and not legal advice. Consult with qualified legal and tax professionals for your specific situation.

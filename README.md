# RecVue (recvue)

RecVue is an enterprise revenue management platform - RevOS, the Revenue Operating System - that unifies complex billing, revenue recognition, order-to-cash, usage-based monetization, and partner settlements for the office of the CFO. It automates recurring, usage, milestone, and hybrid billing models and recognizes revenue in compliance with **ASC 606** and **IFRS 15**, with performance-obligation tracking, allocation, deferral, and audit trails.

RecVue is API-first and publishes a documented, RESTful developer API at [developer.recvue.com](https://developer.recvue.com/): JSON responses, OAuth2 client-credentials authentication (token at `/api/scim/oauth/token`), a Bulk API for large data sets, official Node/Ruby/JavaScript/Python client libraries, and an `llms.txt` index for AI agents. Production base URL is `https://api.recvue.com/api/v2.0`; a sandbox is available at `https://sandbox-api.recvue.com/api/v2.0`.

**Access model:** the API reference is public, but RecVue is an enterprise product. Production and sandbox tenants, API credentials, and RevOS modules are provisioned through a direct sales process - there is no public self-service signup or pricing. RecVue is a Palo Alto company (founded 2016) serving large enterprises in telecom, transportation and logistics, technology, AI infrastructure, and business services.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/recvue/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/recvue/refs/heads/main/apis.yml)

## Tags

- Revenue Recognition
- ASC 606
- Billing
- Order-to-Cash
- Revenue Management
- Usage-Based Billing
- Partner Settlements
- IFRS 15
- Subscription Billing
- Enterprise

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

The logical APIs below are grouped from RecVue's public reference (120+ documented operations) around the highest-value revenue use cases. All share base URL `https://api.recvue.com/api/v2.0` and OAuth2 client-credentials auth. See `openapi/recvue-openapi.yml` for the modeled surface; base URLs, auth, and the `GET /orders` and token endpoints are confirmed verbatim, while other paths/payloads are honestly modeled from the documented operations.

### RecVue Revenue Recognition API

Configure and track ASC 606 / IFRS 15 revenue recognition - revenue-contract amendment setup (performance-obligation and compliance controls) and amendment audit history. Revenue schedules, allocation, and deferral run via the concurrent-program engine.

- **Human URL:** [https://developer.recvue.com/reference/getrevcontractamendsetup](https://developer.recvue.com/reference/getrevcontractamendsetup)
- **Base URL:** `https://api.recvue.com/api/v2.0`
- **Tags:** Revenue Recognition, ASC 606, IFRS 15, Revenue Contracts

### RecVue Billing API

Generate and manage invoices through bill runs (CREATED to PROCESSING to COMPLETED), retrieve invoice and billing-line detail, export bill-run artifacts (PDF/XML/CSV/tax), and approve or reject invoices. Supports subscription, usage, one-time, milestone, tiered, and hybrid billing.

- **Human URL:** [https://developer.recvue.com/reference/getbillrun](https://developer.recvue.com/reference/getbillrun)
- **Base URL:** `https://api.recvue.com/api/v2.0`
- **Tags:** Billing, Bill Runs, Invoicing

### RecVue Billing Schedules API

Retrieve, create, update, and delete billing schedules - the dated, quantity-bearing records that drive one-time, milestone, and contingent billing.

- **Human URL:** [https://developer.recvue.com/reference/getbillingschedule](https://developer.recvue.com/reference/getbillingschedule)
- **Base URL:** `https://api.recvue.com/api/v2.0`
- **Tags:** Billing Schedules, Milestone Billing, Deferred Billing

### RecVue Orders API

The order-to-cash core - create, read, update, delete, upsert-by-external-reference, activate, terminate, and amend orders and order lines, and manage order types (which define billing and revenue rules).

- **Human URL:** [https://developer.recvue.com/reference/getorder](https://developer.recvue.com/reference/getorder)
- **Base URL:** `https://api.recvue.com/api/v2.0`
- **Tags:** Orders, Order-to-Cash, Contracts, Amendments

### RecVue Usage and Deliveries API

Ingest and manage consumption data for usage-based billing - load usage records into batches routed to the Usage Hub, query/update/delete batch details, and manage usage/delivery (ORDER_DELIVERIES) records that feed billing and revenue.

- **Human URL:** [https://developer.recvue.com/reference/createbatchdetails](https://developer.recvue.com/reference/createbatchdetails)
- **Base URL:** `https://api.recvue.com/api/v2.0`
- **Tags:** Usage-Based Billing, Usage Ingestion, Deliveries, Metering

### RecVue Pricing API

Manage price lists (standard, customer, revenue, hierarchical), tier-pricing configurations (volume, quantity, usage, multi-dimensional), attribute-based pricing rules, and pricing formulas.

- **Human URL:** [https://developer.recvue.com/reference/getpricelists](https://developer.recvue.com/reference/getpricelists)
- **Base URL:** `https://api.recvue.com/api/v2.0`
- **Tags:** Pricing, Price Lists, Tiered Pricing, Pricing Rules

### RecVue Customers and Accounts API

Create, read, and update customer accounts, sites (BILL_TO, SHIP_TO, SELL_TO), and contacts, with partner and payment-term validation. Includes supplier/vendor records for partner settlement.

- **Human URL:** [https://developer.recvue.com/reference/getcustaccountsusingget](https://developer.recvue.com/reference/getcustaccountsusingget)
- **Base URL:** `https://api.recvue.com/api/v2.0`
- **Tags:** Customers, Accounts, Sites, Contacts

### RecVue Invoices and Adjustments API

Create or update invoices for manual AR integration, search invoices for adjustments, run standard/manual adjustment processes, manage transaction types (INV, CM, DM), and update payment and billing lines with AR transaction IDs and GL dates.

- **Human URL:** [https://developer.recvue.com/reference/createinvoice](https://developer.recvue.com/reference/createinvoice)
- **Base URL:** `https://api.recvue.com/api/v2.0`
- **Tags:** Invoices, Adjustments, AR Integration, Credit Memos

## Authentication

OAuth2, `client_credentials` grant. Request an access token from `https://api.recvue.com/api/v2.0/api/scim/oauth/token` using a Basic auth header (client_id:client_secret) or client_id/client_secret form params, then send the token as an `Authorization: Bearer` header. See `authentication/recvue-authentication.yml`.

## Common Properties

- [Authentication](authentication/recvue-authentication.yml)
- [LinkedIn](https://www.linkedin.com/company/recvue)
- [Website](https://www.recvue.com/)
- [Documentation](https://developer.recvue.com/)
- [Plans](plans/recvue-plans-pricing.yml)
- [Rate Limits](rate-limits/recvue-rate-limits.yml)
- [Fin Ops](finops/recvue-finops.yml)

## Review

Does RecVue expose a documented public WebSocket API? **No.** RecVue's API is request/response REST (JSON) over HTTPS, plus a Bulk API and asynchronous concurrent programs; job completion is surfaced by status polling or an HTTP callback webhook. No WebSocket/SSE transport is documented. See `review.yml`.

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com

# WhatsApp API Partner and Minimum Pricing Plan

Research date: 2026-07-01

Scope: Build a WhatsApp Business Platform partner plan that keeps message pricing as low and stable as possible while staying inside official Meta/WhatsApp rules. All references in this document are official Meta, WhatsApp, or Meta for Developers URLs.

## 1. Executive Decision

Our recommended path is:

1. Start as a WhatsApp Tech Provider.
2. Build a low-cost Cloud API platform with Embedded Signup, template governance, billing/cost reporting, and routing that maximizes free service windows.
3. Upgrade to Tech Partner when Meta eligibility is available.
4. Pursue Solution Partner only if we need to manage client billing through line-of-credit sharing.

Reason: Meta's public partner page separates the ecosystem into Tech Partners and Solution Partners. Tech Providers/Tech Partners are for third-party developers building solutions on top of WhatsApp Business Platform. Solution Partners provide end-to-end services and are the partner type that can extend a line of credit to businesses for payment.

Official source: https://whatsappbusiness.com/partners/become-a-partner/

## 2. Pricing Reality

We cannot force Meta's official message rates to remain fixed. We can make customer pricing stable by:

- Passing Meta message charges through transparently instead of hiding them.
- Charging our margin as a fixed SaaS/platform fee, onboarding fee, support fee, or integration fee.
- Using a price engine that reads Meta's current rate card by country, currency, category, and volume tier.
- Designing message flows to use free service messages, free utility replies, and free entry-point windows.
- Avoiding wrong category classification. Mislabeling a marketing message as utility is not a pricing strategy; it is a policy and account-quality risk.

Official pricing source: https://whatsappbusiness.com/products/platform-pricing/

Official developer pricing source and rate cards: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing

## 3. Message Categories

Meta lists four WhatsApp Business Platform message categories: Marketing, Utility, Authentication, and Service.

| Category | Main use | Examples | Pricing impact | Cost strategy |
|---|---|---|---|---|
| Service | Responding to customer-initiated support/sales messages inside the customer service window | Answer questions, product availability, account support, booking help | Meta says service messages are not charged during the 24-hour customer service window. The window resets with each user message. | Push customers to start chats first. Resolve as much as possible inside the 24-hour window. |
| Utility | Non-promotional transactional or requested updates | Order confirmation, delivery update, payment reminder, account alert, opt-in/opt-out confirmation, feedback request | Charged when delivered outside the free conditions. Meta says utility messages sent in response to users are not charged. Eligible for volume tiers. | Move real transactional flows to utility templates. Send them inside the customer service window when possible. |
| Authentication | One-time passcodes and identity verification | Login OTP, account recovery OTP, transaction verification | Charged per delivered message. Eligible for volume tiers. Some markets have Authentication-International pricing. | Use only for OTP/security. Consolidate volume where eligible for tiers. |
| Marketing | Promotional, awareness, conversion, retargeting, re-engagement | Discounts, product recommendations, abandoned cart, loyalty offer, upsell | Usually the most expensive category. No utility/auth volume-tier benefit. | Use only for opted-in, high-intent campaigns. Prefer Click-to-WhatsApp entry points where commercially sensible. |

Official category pages:

- Marketing: https://whatsappbusiness.com/products/conversation-categories/marketing/
- Utility: https://whatsappbusiness.com/products/conversation-categories/utility/
- Authentication: https://whatsappbusiness.com/products/conversation-categories/authentication/
- Service: https://whatsappbusiness.com/products/conversation-categories/service/
- Template categorization: https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-categorization

## 4. Current Egypt Pricing Snapshot in USD

The official USD rate card pulled from Meta's developer pricing page is labeled "effective July 1, 2026". The official page should always be treated as the live source of truth because generated CSV links can expire.

Egypt rates in USD per delivered message:

| Market | Marketing | Utility | Authentication | Authentication-International | Service |
|---|---:|---:|---:|---:|---:|
| Egypt | 0.0644 | 0.0036 | 0.0036 | 0.0650 | 0.00 when sent as service messages inside the customer service window |

Meaning:

- Marketing in Egypt is about 17.9x the price of Utility or Authentication.
- 100,000 marketing messages cost about 6,440 USD in Meta fees.
- 100,000 utility messages cost about 360 USD before any higher-volume tier discounts.
- Service replies inside the customer service window should be treated as the minimum-price path because Meta does not charge for them.

Official source: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing

## 5. Egypt Volume Tiers for Utility and Authentication

Meta provides volume tiers for utility and authentication messages. Tier rates apply only to messages inside that tier, not retroactively to all messages.

Egypt utility tiers in USD:

| Monthly utility messages | Rate |
|---:|---:|
| 0 to 100,000 | 0.0036 |
| 100,001 to 1,000,000 | 0.0034 |
| 1,000,001 to 4,500,000 | 0.0032 |
| 4,500,001 to 40,000,000 | 0.0031 |
| 40,000,001 to 80,000,000 | 0.0029 |
| 80,000,001+ | 0.0027 |

Egypt authentication tiers in USD:

| Monthly authentication messages | Rate |
|---:|---:|
| 0 to 300,000 | 0.0036 |
| 300,001 to 2,000,000 | 0.0034 |
| 2,000,001 to 10,000,000 | 0.0032 |
| 10,000,001 to 20,000,000 | 0.0031 |
| 20,000,001 to 40,000,000 | 0.0029 |
| 40,000,001+ | 0.0027 |

Egypt authentication-international tiers in USD:

| Monthly authentication-international messages | Rate |
|---:|---:|
| 0 to 300,000 | 0.0650 |
| 300,001 to 2,000,000 | 0.0618 |
| 2,000,001 to 10,000,000 | 0.0585 |
| 10,000,001 to 20,000,000 | 0.0553 |
| 20,000,001 to 40,000,000 | 0.0520 |
| 40,000,001+ | 0.0488 |

Official source: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing

## 6. Minimum-Price Message Routing Rules

Implement these rules in code before sending any message:

1. If the user messaged us and the 24-hour customer service window is open, send a service message when the reply is support/sales/service.
2. If the user messaged us and the response is a real transactional update, use a utility template inside the window when a template is needed.
3. If the user entered from a Click-to-WhatsApp ad or a Facebook Page call-to-action button, use the 72-hour free entry-point window when eligible.
4. If the message is an OTP or verification code, use authentication. Do not mix OTP text into utility or marketing.
5. If the content promotes, retargets, upsells, cross-sells, gives discounts, or drives re-engagement, use marketing and reserve it for high-intent opted-in users.
6. Outside the customer service window, use approved templates only and charge/forecast by the recipient country and template category.
7. Do not send duplicate notifications. Use idempotency keys, delivery receipts, and event state before sending another billable message.

Official sources:

- Pricing and free windows: https://whatsappbusiness.com/products/platform-pricing/
- Message templates: https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/overview
- Template categorization: https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-categorization

## 7. Product Design for Lowest Customer Cost

Build the product around inbound-first journeys:

- Website WhatsApp button, QR codes, order-status pages, invoices, packaging, and email links should ask the user to start the WhatsApp chat.
- Use Click-to-WhatsApp ads where paid acquisition is already justified, because Meta states that when users message from eligible ads or a Facebook Page CTA, messages in the following 72 hours are not charged.
- Route support, pre-sales, FAQ, order tracking, returns, and account questions through the customer service window.
- Convert call-center and SMS status traffic into utility flows where the content is truly transactional.
- Keep marketing campaigns smaller, segmented, and conversion-measured because marketing is the expensive category.

Official source: https://whatsappbusiness.com/products/platform-pricing/

## 8. Stable Customer Pricing Model

Use three billing layers:

1. Meta pass-through fee
   - Exact Meta fee based on delivered messages, recipient market, category, and volume tier.
   - Shown separately in invoices and dashboards.

2. Fixed platform fee
   - Our margin should come from SaaS access, seats, inbox, chatbot, analytics, templates, CRM integration, SLA support, onboarding, and training.
   - This keeps our promise of minimum message price credible.

3. Optional prepaid wallet or budget cap
   - Customers set a monthly maximum spend.
   - The system pauses non-critical marketing before budget is exceeded.
   - Utility/auth/service flows continue according to customer policy.

Avoid:

- Hidden per-message markup if the mission is minimum pricing.
- Unlimited bundled marketing packages unless we reserve the right to adjust by country/category.
- Promising fixed Meta rates for long periods. Meta controls the official rate cards.

## 9. Partner Path

### Phase A: Direct Cloud API build for our own business

Goal: Prove the product before partner approval.

Tasks:

- Create/verify Meta Business Portfolio.
- Create a Meta app with WhatsApp.
- Set up WhatsApp Cloud API, test number, webhooks, templates, and delivery reporting.
- Build the core message router and pricing engine.
- Implement customer service window tracking and free-entry-point tracking.

Official sources:

- Cloud API overview: https://developers.facebook.com/documentation/business-messaging/whatsapp/about-the-platform
- Get started: https://developers.facebook.com/documentation/business-messaging/whatsapp/get-started

### Phase B: Become a Tech Provider

Goal: Onboard client businesses to our solution.

Tasks:

- Apply through the WhatsApp Tech Provider path.
- Pass App Review for advanced access to required WhatsApp permissions.
- Implement Embedded Signup so clients can connect their business assets.
- Add secure token storage, webhooks, audit logs, data deletion, support workflows, and error handling.
- Create an App Review screencast showing the end-to-end customer onboarding and messaging flow.

Official sources:

- Become a Tech Provider: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/get-started-for-tech-providers
- Embedded Signup overview: https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/overview
- Embedded Signup implementation: https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/implementation
- App Review sample submission: https://developers.facebook.com/docs/whatsapp/solution-providers/app-review/sample-submission/

### Phase C: Upgrade to Tech Partner

Goal: Move from Tech Provider to partner status when eligible.

Tasks:

- Maintain clean policy record, customer quality, and support process.
- Track active customers, message quality, delivered volumes, template approval rates, and business outcomes.
- Use the App Dashboard "Become a Partner" path when Meta makes upgrade eligibility available.

Official source: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/upgrade-to-tech-partner/

### Phase D: Solution Partner decision

Goal: Only pursue this path if we need end-to-end services and billing control.

Why it matters:

- Meta's partner page says Solution Partners offer end-to-end solutions and can extend a line of credit to businesses for payment.
- If we remain a Tech Provider, the cleaner low-cost model is customer-paid Meta fees plus our fixed platform fee.

Official sources:

- Partner ecosystem: https://whatsappbusiness.com/partners/become-a-partner/
- Get started as Solution Partner: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/get-started-for-solution-partners/

## 10. Compliance Requirements

Minimum compliance rules:

- Obtain user opt-in before sending business-initiated template messages.
- Opt-in must clearly identify the business and the kind of messages the user agrees to receive.
- Keep messages expected, timely, and relevant.
- Use the correct template category.
- Monitor quality ratings, blocks, spam reports, failed deliveries, and template rejections.
- Maintain unsubscribe/opt-out controls for marketing.
- Follow WhatsApp Business Messaging Policy and Commerce Policy.

Official sources:

- Opt-in: https://developers.facebook.com/documentation/business-messaging/whatsapp/getting-opt-in
- About platform and opt-in: https://developers.facebook.com/documentation/business-messaging/whatsapp/about-the-platform
- Policy enforcement: https://developers.facebook.com/documentation/business-messaging/whatsapp/policy-enforcement
- WhatsApp Business Policy: https://www.whatsapp.com/legal/business-policy/
- WhatsApp Commerce Policy: https://www.whatsapp.com/legal/commerce-policy/

## 18. Global WhatsApp API Partner and Provider Landscape

Last checked: 2026-07-01

Use this list to benchmark the market outside Egypt. The official directory-of-record is Meta's WhatsApp Business Platform Partner Showcase. It lists 50+ trusted partners and allows filtering by region, industry, and capabilities, but it may require Facebook login:

https://business.facebook.com/messaging/partner-showcase

Important rule: before signing a commercial agreement or positioning a company as an official current partner, re-check the company in Meta's Partner Showcase because partner tiers, regions, and capabilities can change.

| # | Company | Main website | Main region / focus | Public WhatsApp/partner evidence |
|---:|---|---|---|---|
| 1 | Infobip | https://www.infobip.com/ | Global CPaaS, enterprise messaging, omnichannel automation | https://www.infobip.com/whatsapp-business |
| 2 | Twilio | https://www.twilio.com/ | Global developer-first APIs and communications platform | https://www.twilio.com/en-us/messaging/channels/whatsapp |
| 3 | Bird / MessageBird | https://bird.com/ | Global communications platform, API and marketing/service workflows | https://bird.com/en-us/products/whatsapp/ |
| 4 | Vonage | https://www.vonage.com/ | Global communications APIs and conversational commerce | https://www.vonage.com/communications-apis/messages/features/whatsapp/ |
| 5 | Sinch | https://sinch.com/ | Global CPaaS, messaging, verification, omnichannel customer engagement | https://sinch.com/messaging/whatsapp-business-api/ |
| 6 | CM.com | https://www.cm.com/ | Europe/global CPaaS, messaging API, mobile service cloud | https://www.cm.com/whatsapp/whatsapp-business-platform/ |
| 7 | 360dialog | https://360dialog.com/ | Europe/global WhatsApp API access, partner platform, agency tooling | https://360dialog.com/whatsapp-api |
| 8 | Gupshup | https://www.gupshup.ai/ | India/global conversational messaging and enterprise WhatsApp platform | https://www.gupshup.ai/whatsapp-api |
| 9 | Wati | https://www.wati.io/ | SMB and mid-market WhatsApp growth platform, strong Asia/India presence | https://www.wati.io/whatsapp-business-api/ |
| 10 | respond.io | https://respond.io/ | Global customer conversation management, WhatsApp Cloud API onboarding | https://respond.io/whatsapp-business-api |
| 11 | tyntec | https://www.tyntec.com/ | Europe/global messaging and WhatsApp Business API connectivity | https://www.tyntec.com/helpcenter/docs/channels/whatsapp-business/self-service/ |
| 12 | Route Mobile | https://routemobile.com/ | India/global CPaaS, enterprise WhatsApp Business Platform | https://routemobile.com/products/enhanced-business-messaging/whatsapp-business-solution/ |
| 13 | Zenvia | https://zenvia.com/ | Latin America customer cloud and WhatsApp customer engagement | https://zenvia.com/en/whatsapp/ |
| 14 | Blip | https://www.blip.ai/ | Brazil/Latin America conversational AI and WhatsApp automation | https://www.blip.ai/en/whatsapp/ |
| 15 | Yellow.ai | https://yellow.ai/ | Global enterprise conversational automation and WhatsApp AI/chatbot use cases | https://yellow.ai/whatsapp-api/ |
| 16 | Haptik | https://www.haptik.ai/ | India/global enterprise AI agents and WhatsApp customer journeys | https://www.haptik.ai/whatsapp-enterprise |
| 17 | Botmaker | https://botmaker.com/ | Latin America/global WhatsApp automation and BSP tooling | https://botmaker.com/en/whatsapp-business-platform-api |
| 18 | SleekFlow | https://sleekflow.io/ | Asia/global omnichannel social commerce and WhatsApp AI agents | https://sleekflow.io/en-us/channels-integrations/whatsapp |
| 19 | AiSensy | https://aisensy.com/ | India/global WhatsApp marketing, broadcasts, automation, SMB/mid-market | https://aisensy.com/whatsapp-business-api |
| 20 | Interakt | https://www.interakt.shop/ | India/global WhatsApp CRM, marketing, sales, support automation | https://www.interakt.shop/whatsapp-business-api/ |
| 21 | Clickatell | https://www.clickatell.com/ | Global chat commerce and WhatsApp API solutions | https://www.clickatell.com/products/whatsapp/ |
| 22 | Plivo | https://www.plivo.com/ | Global communications APIs and WhatsApp messaging | https://www.plivo.com/whatsapp/pricing/ |
| 23 | SendPulse | https://sendpulse.com/ | Global SMB chatbot, marketing automation, WhatsApp API provider | https://sendpulse.com/features/chatbot/whatsapp-business |
| 24 | Trengo | https://trengo.com/ | Europe/global shared inbox, AI agents, customer service on WhatsApp | https://trengo.com/products/whatsapp |
| 25 | MessageMedia | https://messagemedia.com/ | Australia/APAC business messaging, now part of Sinch | https://support.messagemedia.com/hc/en-us/articles/9224631333903-Social-Messaging-What-are-the-different-ways-to-use-WhatsApp |

How to use this list:

- Benchmark product positioning: API-first providers like Twilio, 360dialog, Bird, Infobip, Sinch, CM.com, Route Mobile, and Vonage are important for technical buyers.
- Benchmark SMB pricing and onboarding: Wati, AiSensy, Interakt, SendPulse, Trengo, SleekFlow, respond.io, and Gallabox-style products show how lower-friction onboarding and packaged dashboards are sold.
- Benchmark regional go-to-market: Blip, Zenvia, Botmaker, Route Mobile, Gupshup, Wati, AiSensy, and Interakt show strong regional plays outside Egypt.
- Benchmark low-price promise: 360dialog, Plivo, and several API-first providers publicly emphasize transparent pricing or pass-through Meta fees. We should compete with this by keeping Meta charges transparent and taking margin from fixed platform value.
- Benchmark enterprise capability: Infobip, Sinch, Twilio, Vonage, Bird, CM.com, Route Mobile, and Clickatell are the stronger references for enterprise SLAs, omnichannel routing, verification, and integrations.

Competitive takeaway for our plan:

The market is already crowded. Our differentiation should not be "we provide WhatsApp API" only. It should be:

1. Transparent Meta pass-through pricing.
2. A strong Arabic-first and MENA-first operating model.
3. Cost controls that route messages into service windows and utility/auth tiers correctly.
4. Partner/agency tooling for onboarding multiple customers.
5. Clean compliance, opt-in, template review, and customer spend dashboards.

## 11. System Architecture

Required modules:

- Customer onboarding module: Embedded Signup, customer WABA/phone metadata, permissions, webhook registration.
- Message router: category decision, free-window decision, country pricing decision, budget decision.
- Template manager: template creation, category review, approval status, localization, versioning.
- Pricing engine: official rate-card import, tier calculation, estimate API, invoice line-item API.
- Ledger: delivered-message events, chargeable/free classification, customer balance, monthly invoice.
- Budget controls: customer caps, campaign caps, emergency stop, marketing throttles.
- Quality monitor: opt-outs, blocks, spam reports, delivery rate, read rate, conversion rate.
- Admin review: manual approval for new marketing templates and high-volume campaigns.

Core data to store per message:

- Customer ID
- WABA ID
- Phone number ID
- Recipient country/market
- Template ID and category
- Whether user service window was open
- Whether free entry-point window was open
- Sent timestamp
- Delivered timestamp
- Chargeable/free classification
- Meta rate-card version
- Applied tier
- Estimated cost and final cost

## 12. Cost Governance Rules

Create these internal rules:

- Rate card is checked at least monthly and before any customer quote.
- Any Meta rate-card change creates a new internal pricing version.
- Quotes show "Meta fees are pass-through and may change when Meta updates official rate cards."
- Marketing campaigns require estimated cost, target audience, opt-in source, expected revenue, and approval.
- Utility/auth flows require category review before launch.
- All customers get a live dashboard showing delivered, free, paid, category split, and estimated month-end cost.

## 13. 90-Day Execution Plan

Days 1-15:

- Build direct Cloud API prototype.
- Import Meta USD rate card.
- Implement Egypt pricing calculator.
- Implement service-window tracking.
- Draft opt-in and template policies.

Days 16-30:

- Build template manager and message router.
- Add delivery webhook processing.
- Add invoice/ledger model.
- Launch internal test with one WABA and one phone number.

Days 31-60:

- Implement Embedded Signup flow.
- Prepare Tech Provider App Review materials.
- Add customer onboarding screens.
- Add budget caps and customer pricing dashboards.

Days 61-90:

- Submit for Tech Provider requirements/App Review.
- Pilot with 2-3 friendly businesses.
- Measure category mix, free-message ratio, delivered cost, template approval rate, and quality signals.
- Decide whether we need an existing Solution Partner relationship for billing while our own partner status matures.

## 14. KPIs

Pricing KPIs:

- Percentage of messages sent as free service messages.
- Percentage of utility messages sent inside the customer service window.
- Marketing cost per conversion.
- Utility/auth average cost after tiers.
- Customer monthly spend variance versus forecast.

Partner/business KPIs:

- Embedded Signup completion rate.
- Template approval rate.
- Message delivery rate.
- Block/report rate.
- Customer support response time.
- Gross margin from fixed platform fees, not Meta message markup.

## 15. Main Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Meta changes rates | Customer invoices change | Versioned rate cards, pass-through model, monthly pricing notice |
| Wrong category use | Template rejection, quality issues, account restrictions | Template review workflow and category rules |
| Too much marketing traffic | High cost and user blocks | Segmentation, caps, ROI approval, opt-out controls |
| Partner approval delay | Cannot onboard at scale as intended | Start with direct Cloud API for own business, pilot carefully, work with existing Solution Partner if needed |
| Billing complexity | Customer disputes | Separate Meta fees, platform fees, taxes, and budget caps |

## 16. Final Recommendation

The minimum-price promise should be:

"We pass through Meta's official WhatsApp message rates with no hidden message markup, optimize every flow for free service windows and utility/auth volume tiers, and charge our business margin as a transparent platform fee."

For Egypt, the practical minimum paid route is utility/authentication at 0.0036 USD per delivered message before higher-volume discounts, while the true minimum route is service messaging at 0.00 USD when the user starts the conversation and the business replies inside the customer service window.

## 17. Official Reference URLs

- WhatsApp Business Platform Pricing: https://whatsappbusiness.com/products/platform-pricing/
- Meta Developer Pricing and Rate Cards: https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing
- Become a WhatsApp Business Platform Partner: https://whatsappbusiness.com/partners/become-a-partner/
- Become a Tech Provider: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/get-started-for-tech-providers
- Solution Partner overview: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/overview
- Get started as Solution Partner: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/get-started-for-solution-partners/
- Upgrade to Tech Partner: https://developers.facebook.com/documentation/business-messaging/whatsapp/solution-providers/upgrade-to-tech-partner/
- Embedded Signup overview: https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/overview
- Embedded Signup implementation: https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/implementation
- App Review sample submission: https://developers.facebook.com/docs/whatsapp/solution-providers/app-review/sample-submission/
- WhatsApp Cloud API get started: https://developers.facebook.com/documentation/business-messaging/whatsapp/get-started
- About WhatsApp Business Platform: https://developers.facebook.com/documentation/business-messaging/whatsapp/about-the-platform
- Marketing messages: https://whatsappbusiness.com/products/conversation-categories/marketing/
- Utility messages: https://whatsappbusiness.com/products/conversation-categories/utility/
- Authentication messages: https://whatsappbusiness.com/products/conversation-categories/authentication/
- Service messages: https://whatsappbusiness.com/products/conversation-categories/service/
- Template fundamentals: https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/overview
- Template categorization: https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-categorization
- Opt-in: https://developers.facebook.com/documentation/business-messaging/whatsapp/getting-opt-in
- Policy enforcement: https://developers.facebook.com/documentation/business-messaging/whatsapp/policy-enforcement
- WhatsApp Business Policy: https://www.whatsapp.com/legal/business-policy/
- WhatsApp Commerce Policy: https://www.whatsapp.com/legal/commerce-policy/

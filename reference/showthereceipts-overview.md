# ShowTheReceipts

Business operations software for solo service operators — mobile detailers, pressure washers, and field service trades who need professional invoicing, scheduling, and payments without the bloat or the big-SaaS price tag.

> Full-stack app with a React/Vite frontend, Express backend, Supabase/Postgres, Stripe, Resend, and an Astro marketing site.

## What It Is

ShowTheReceipts is a purpose-built workspace for solo operators and small crews in field service trades. It's designed for the person running their own mobile detailing route, pressure washing schedule, or similar service business who needs to look professional, stay organized, and get paid — without paying $50–$100/month for software built for enterprise teams.

The core loop: a client requests a job → the owner schedules it → shows up and does the work → sends an invoice or runs a quick charge on-site → gets paid. Everything lives in one place.

It is not a generic invoicing tool. The feature decisions — AI flyer scanning, mobile-first quick charges, public job request pages, photo uploads on job sites, tiered service pricing — are driven by the specific daily reality of running a field service business as a solo operator or small team.

The product is split into:

- `invoice` — the authenticated web app (dashboard, scheduling, invoicing, quick charge)
- `invoice-backend` — the Node/Express API, email delivery, PDF generation, and Stripe integration
- `invoice-marketing` — the public marketing site

## Comprehensive Feature List & Capabilities

This section provides a highly detailed breakdown of every feature available to end users, designed for comparative analysis against other field service software (e.g., Jobber, Housecall Pro, Square).

### 1. Job Requests & Public Intake (Client-Facing & Operator Preview)
- **Public Request Portals:** Dedicated, branded URLs for each operator to accept inbound work requests.
- **Live Public Preview:** Operators can view exactly what their clients will see via an in-app interactive preview of their public intake page.
- **Multiple Intake Templates (Themes):**
  - **Standard:** Clean and simple form layout.
  - **Hybrid:** Premium dark-mode layout combining a portfolio image gallery with the intake form.
  - **Tabs:** Segmented tabbed layout for categorizing multiple services.
  - **Lightweight:** Minimalist and low-friction form for rapid requests.
- **Client Photo Uploads:** Clients can attach up to 3 reference photos of the work needed (e.g., a dirty driveway, a damaged car bumper) directly from their phone.
- **Automated Contact Capture:** Intake forms automatically collect client details, location, and requested start times.

### 2. Preset Service Catalogs & AI Flyer Import
- **AI Flyer & PDF Parser (Magic AI):** Upload a promotional flyer (image or PDF) and let Gemini Vision automatically extract all service packages, pricing tiers, features, and add-ons. Generates a fully populated service catalog in seconds with an intelligent auto-merge deduplication system.
- **Dynamic Pricing Models:**
  - **Flat Pricing:** A single, set price for the preset service.
  - **Tiered Models:** Multiple variants for the same service (e.g., Sedan: $100, SUV: $120, Truck: $150).
  - **Range Pricing:** A minimum and maximum price range display (e.g., $100 - $200).
- **Preset Descriptions & Features:** Each preset can have bulleted feature lists describing what the service includes.
- **Upgrades & Add-ons:** Independent supplementary services (e.g., "Pet Hair Removal") that clients can optionally select. Upgrades can also have their own Flat or Tiered pricing models and link intelligently to specific presets.

### 3. Scheduling & Dispatch (Operator-Facing)
- **Request Inbox:** A dedicated queue for reviewing incoming client requests before converting them into scheduled jobs.
- **Interactive Calendar:** Day, week, and month schedule views optimized for both desktop and mobile.
- **Accidental Unschedule Protection:** A hybrid safety system featuring an immediate "Undo" action toast, plus fallback preservation of the client's originally requested time if a job is accidentally moved to the unscheduled bucket.
- **Job Detail Workspaces:**
  - Comprehensive view of a scheduled job, including client-provided photos, timeline events, and operator notes.
  - Job status tracking (e.g., Pending, In Progress, Completed).
  - One-click "Schedule-to-Invoice" flow that converts a completed job into a ready-to-send invoice.
- **CRM & Client Auto-Sync:** Walk-up customers and job requesters can be seamlessly promoted to saved clients in the CRM. Includes lifetime revenue tracking per client.

### 4. Invoicing & Quotes (Operator & Client-Facing)
- **Split-Panel Invoice Builder:** Desktop-optimized dual-pane view showing the line-item editor on one side and a live HTML/PDF preview on the other.
- **Quotes vs. Invoices:** Toggle seamlessly between sending an estimate/quote for approval and sending a final invoice.
- **Recurring & Installments:** Setup automated recurring invoices or flexible payment schedules for ongoing service contracts.
- **AI-Assisted Line Item Extraction:** Upload a photo of a handwritten estimate or text block, and the AI automatically parses it into structured invoice line items.
- **Smart Reminders:** Automated, timezone-aware nudge sequences for overdue invoices.
- **8 Professional Themes:** High-end templates to differentiate from generic invoice PDFs (e.g., Artisan, Luxury Editorial, Modern Studio, Botanical, Clean Minimalist).

### 5. Mobile Quick Charges (Field Operations)
- **Walk-Up Payments:** A highly streamlined, mobile-first flow designed for charging a client on-site in seconds.
- **Tap-to-Add Presets:** Instantly add catalog services, tiered variants, and upgrades directly from the mobile quick charge screen.
- **Custom & Free Items:** Instantly add bespoke charges or zero-dollar records to the charge.
- **Instant Receipts:** Auto-generates and emails professional receipts immediately upon payment capture.

### 6. Client Portals & Payment (Client-Facing)
- **Live Job Portals:** Real-time web pages where clients can track the status of their job phase by phase.
- **Stripe Checkout Integration:** Secure credit card, Apple Pay, and Google Pay processing natively tied to invoices and quick charges. Support for Stripe Customer Portals to manage subscriptions.
- **Paid-Outside Claim Flow:** Clients or operators can mark an invoice as paid via cash/check/Venmo outside of Stripe, keeping the internal ledger perfectly accurate.
- **Passcode-Protected Share Links:** Send secure, expiring, passcode-protected links to accountants, partners, or stakeholders to view financial data.

### 7. Analytics & Observability (Operator & Admin)
- **Revenue Dashboards:** Charts and metrics tracking income, outstanding balances, profit analysis, and job conversion rates.
- **Ledger Exports:** One-click CSV/JSON exports and "End-of-Year" ZIP generation for tax reporting.
- **Activity Feed:** A chronological timeline of all business events (invoices sent, payments received, jobs requested).
- **Admin Observability Panel:** For platform owners to track system health, API latency, background jobs, and webhook failures.

### 8. Multi-Tier SaaS Billing & Subscription Management
- **Tiered Plans:** Support for Starter ($15/mo), Pro ($39/mo), and Teams ($89/mo) with deeply integrated feature gating and usage limits (clients, invoices, AI credits).
- **Self-Serve Stripe Portals:** Paid users have a "Manage via Stripe" portal allowing them to autonomously upgrade, downgrade, or swap between monthly/annual intervals.
- **Webhook Synchronization:** Real-time sync via Stripe's `customer.subscription.updated` webhook to instantly adjust app access limits based on portal changes.
- **Compact Upgrade UX:** Free users see a highly optimized side-by-side feature grid for seamless upgrading without overwhelming vertical scroll.

## Complete Application Routing Table

### Marketing Site Routes
| Route | Purpose |
| --- | --- |
| `/` | Landing page |
| `/pricing` | Public pricing page |
| `/templates` | Public template showcase |
| `/resources` | Resources and guides |
| `/contact` | Public contact form |
| `/privacy` | Privacy policy |
| `/security` | Security policy |
| `/terms` | Terms of service |

### App Public Routes
| Route | Purpose | Features & Access |
| --- | --- | --- |
| `/` | Root redirect | Routes to login or dashboard based on session state |
| `/login` | Login page | Email/password & OAuth login |
| `/sign-up` | Sign-up page | Account creation |
| `/auth/callback` | OAuth callback | Handles OAuth redirection |
| `/forgot-password` | Password reset request | Initiates password recovery |
| `/update-password` | Password update form | Secure password entry |
| `/confirmation` | Auth confirmation | Success page for auth flows |
| `/feedback/paid-outside` | Paid-outside confirmation | Client flow for claiming cash/check payments |
| `/public/invoice/:id` | Public invoice view | Interactive invoice/quote view, PDF download, pay button |
| `/public/invoice/:id/live` | Live job portal view | Status tracking and live updates for active jobs |
| `/public/quick-charge/:id` | Public quick charge view | Mobile-optimized checkout flow for walk-up payments |
| `/share/:linkId` | Passcode-protected share | Secure external sharing for accountants/partners |
| `/request/:userId` | Public job request (Standard) | Standard intake form with presets and photos |
| `/request/:userId/hybrid` | Public job request (Hybrid) | Premium dark-mode layout with portfolio gallery |
| `/request/:userId/tabs` | Public job request (Tabs) | Tabbed layout for categorizing services |
| `/request/:userId/lightweight` | Public job request (Light) | Minimalist form for quick, low-friction requests |
| `/demo/home-bakery` | Demo Environment | Interactive marketing sandbox for Home Bakery use-case |
| `/demo/mobile-detailing` | Demo Environment | Interactive marketing sandbox for Mobile Detailing use-case |

### Protected App Routes (Operator Workspace)
| Route | Purpose | Core Functionality |
| --- | --- | --- |
| `/onboarding` | First-run setup | Configures business name, logo, presets generation, and Stripe connect |
| `/dashboard` | Main analytics dashboard | Revenue charts, recent activity, snapshot cards |
| `/dashboard/invoices` | Invoice & quote builder | Split-panel editor, AI extraction, themes |
| `/dashboard/invoices/:id/edit` | Invoice edit workspace | Modify existing invoices |
| `/dashboard/activity` | Activity feed | Chronological timeline of all system events |
| `/dashboard/schedule` | Scheduling & request inbox | Calendar views, inbound request queue management |
| `/dashboard/schedule/jobs/:id` | Job detail workspace | Photos, notes, status changes, invoice generation |
| `/dashboard/clients` | Client directory | CRM, client history, revenue per client |
| `/dashboard/templates` | Template library | Manage visual themes for invoices and emails |
| `/dashboard/settings` | Settings area | Branding, preview public pages, manage preset pricing tiers, addons |
| `/admin/observability` | Admin observability panel | System health, API latency, failure tracking |

### Backend API Surface
| Area | Routes |
| --- | --- |
| **Health and ping** | `/api/ping`, `/api/observability/health` |
| **AI Processing** | `/api/ai/generate` |
| **Billing & Stripe** | `/api/billing/checkout`, `/api/billing/invoice-checkout`, `/api/billing/portal`, `/api/billing/webhook` |
| **Stripe Connect** | `/api/connect/stripe/account`, `/api/connect/stripe/onboarding-link`, `/api/connect/stripe/status` |
| **Email & Notifications** | `/api/contact`, `/api/emailer`, `/api/emailer/preview-nudge` |
| **Data Exports** | `/api/export/ledger/csv`, `/api/export/ledger/json`, `/api/export/eoy`, `/api/export/share-link`, `/api/export/share/:id/*` |
| **Invoice Management** | `/api/invoices`, `/api/invoices/:id`, `/api/invoices/:id/status`, `/api/invoices/:id/public`, `/api/invoices/:id/checkout`, `/api/invoices/:id/schedule/:scheduleId/checkout`, `/api/invoices/:id/convert`, `/api/invoices/public/paid-outside`, `/api/invoices/process-nudges`, `/api/invoices/mark-overdue`, `/api/invoices/:id/live/*` |
| **Job Requests** | `/api/job-requests/public/presets`, `/api/job-requests/public`, `/api/job-requests/intake-link`, `/api/job-requests`, `/api/job-requests/:id`, `/api/job-requests/:id/accept`, `/api/job-requests/:id/decline` |
| **PDF Generation** | `/api/pdf/:id`, `/api/pdf/:id/public` |
| **Quick Charges** | `/api/quick-charges`, `/api/quick-charges/:id`, `/api/quick-charges/:id/public`, `/api/quick-charges/:id/create-checkout`, `/api/quick-charges/:id/mark-paid`, `/api/quick-charges/:id/send-receipt`, `/api/quick-charges/save-customer-as-client` |
| **Settings** | `/api/settings` |
| **Webhooks** | `/api/webhooks/resend` |

## Desktop vs Mobile Experience

| Area | Desktop | Mobile |
| --- | --- | --- |
| **Dashboard** | Full analytics layout with charts, cards, and workspace navigation | Mobile dashboard tabs and condensed cards for fast phone use |
| **Invoices and Quotes** | Split-panel builder with live preview and richer workspace controls | Faster navigation to core invoice actions and review screens |
| **Jobs and Scheduling** | Full schedule page with request inbox, job detail, and broader management controls | Tap-first schedule access designed for on-the-go review and updates |
| **Public Job Requests** | Full intake experience with presets, photos, and contact capture | Same public request flow optimized for smaller screens and quick submission |
| **Quick Charges** | Full charge management with presets, custom items, and client promotion | Mobile-first charge creation for field work and ad hoc payments |
| **Public Client Views** | Complete invoice, live portal, and share-link experiences | Responsive public views for clients submitting updates or paying from a phone |

## Technology Stack

### Frontend (`/invoice`)
| Area | Stack |
| --- | --- |
| Framework | React 19 + Vite |
| Language | TypeScript |
| Routing | React Router 7 |
| State | Zustand + TanStack React Query |
| Styling | Tailwind CSS 4 + shadcn/ui + Radix primitives |
| Motion | Framer Motion + tailwindcss-animate |
| Visualization | Recharts |
| Forms / UI | Radix dialog, select, tabs, popover, switch, calendar, Sonner |
| Auth / data | Supabase client |
| Observability | Sentry |

### Backend (`/invoice-backend`)
| Area | Stack |
| --- | --- |
| Runtime | Node.js + Express 5 |
| Language | TypeScript via `tsx` |
| Auth | Supabase JWT validation |
| Email | Resend + React Email |
| PDF | `@react-pdf/renderer` + Puppeteer support |
| Payments | Stripe Checkout, Portal, Connect, and webhooks |
| Validation | Zod |
| Background work | PQueue, Piscina, cron-driven jobs |

### Marketing Site (`/invoice-marketing`)
| Area | Stack |
| --- | --- |
| Framework | Astro 6 |

## Database and Schema

The full generated schema is documented in `docs/system-overview.md` and is driven by the SQL in `sql/` and `cron-jobs/`.

Key data groups:
- **Identity and billing:** `user_subscriptions`, `subscription_tiers`
- **Core sales records:** `clients`, `invoices`, `entries`, `payment_schedules`, `invoice_payments`, `recurring_invoices`
- **Job and service workflow:** `job_requests`, `job_request_photos`, `jobs`, `job_photos`, `job_status_events`
- **Mobile money tools:** `quick_charges`, `receipts`, `expenses`
- **Supporting data:** `attachments`, `templates`, `settings`, `profiles`

Important RPCs and triggers:
- `create_invoice_with_atomic_number`
- `update_invoice_with_entries`
- `create_payment_schedule`
- `decrement_user_magic_credits`
- `add_magic_credits_on_renewal`
- `get_actionable_nudge_batch`

## Repository Structure

```text
/invoice               React app (Vite + TypeScript)
/invoice-backend       Express API, email service, Stripe, PDF generation
/invoice-marketing     Astro marketing site
/sql                   Database migrations, RPCs, triggers, and schema helpers
/cron-jobs             Scheduled SQL and HTTP job definitions
/docs                  Generated system docs and audits
/e2e                   End-to-end test specs
/additional-files      Legal copy and external text assets
/legacy                Archived or deprecated implementation files
/AGENT.md              Project conventions and architecture rules
```

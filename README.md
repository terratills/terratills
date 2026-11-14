# TerraTills Authenticated User Dashboard
> **Nigeria-First Agricultural Services Marketplace**

TerraTills is a unified agricultural marketplace application connecting Nigerian farmers, landowners, machinery fleet owners, agricultural labour coordinators, and agronomy educators.

---

## 🌿 Non-Negotiable Product Rules Implemented
1. **Unified Account & Dashboard**: No separate "Farmer", "Labourer", or "Landowner" account silos. A single user can offer services across categories and request services from others in the same account.
2. **Contextual Roles**: Customer and Provider are dynamic roles on an individual booking or request, not permanent account types.
3. **Multi-Category Ownership**: User can own listings in Farmland Leasing, Machinery Rental, Farm Labour, and Agricultural Training.
4. **Independent State Machines**:
   - **Booking State**: `draft` → `pending_provider_response` → `accepted` → `awaiting_payment` → `confirmed` → `in_progress` → `awaiting_completion_confirmation` → `completed` (Exceptions: `declined`, `cancelled`, `disputed`, `expired`).
   - **Payment State**: `not_required` → `pending` → `processing` → `successful` (Exceptions: `failed`, `refunded`, `reversed`, `on_hold`).
   - **Settlement State**: `not_eligible` → `awaiting_completion_confirmation` → `eligible` → `paid` (Exceptions: `on_hold`, `failed`).
5. **No Pre-payment on Request**: Submitting a booking request creates a pending inquiry only; provider must accept scope and terms before payment is unlocked.
6. **Server-Side Payment Verification**: Processed via the **Bach Payment Provider Adapter**; browser redirects are never treated as proof of payment.
7. **Platform Secured Holding**: Complies with regulatory frameworks; funds are not referred to as legal escrow.
8. **AI Assistant Guardrails**: Assists discovery, entity extraction, and grounded platform cost estimates without executing privileged or financial actions.
9. **Independent Dual Completion**: Customer and Provider confirm completion independently; neither can confirm for the other.

---

## 🚀 Quick Start Instructions

### 1. Start the Server
```bash
# Start backend API & production static frontend
npm start
```
The server will start on `http://localhost:5000`.

### 2. Development Mode
```bash
# Run backend server and Vite client concurrently with hot reloading
npm run dev
```

### 3. Run Acceptance Tests
```bash
npm test
```

---

## 📂 Visual Design System Integration
Built using the visual design system extracted from `new.html`:
- **Forest Palette**: `#0F5338` (Forest Default), `#F0F8F4` (Forest 50), `#DBEFE5` (Forest 100), `#062619` (Forest 900), `#1E6F48` (Leaf).
- **Surface**: `#F8FAFC` and `#F7F9F8` warm slate-tinted canvas.
- **Card Styling**: Rounded 24px (`rounded-3xl`) and 32px (`rounded-4xl`) with forest-tinted `shadow-card` (`0 8px 24px -4px rgba(15, 83, 56, 0.08)`).
- **Agro-Weather Integration**: Nigerian regional weather card with temperature, high/low, moon & stars, sun arc SVG, humidity, pressure, and wind.
- **Mobile Bottom Navigation**: Matching dock with iOS home indicator pill.

---

## 🏛️ All 45 Logical Destinations Implemented

| Destination | Route | Description |
| :--- | :--- | :--- |
| 1 | `/dashboard` | Dashboard Overview with metrics, Agro-weather, recent bookings, owned services |
| 2 | `/dashboard/explore` | Explore Services, category discovery, featured offers carousel |
| 3 | `/dashboard/explore/search` | Search Results with query chips, state filters, sort, pagination |
| 4 | `/dashboard/explore/category/:slug` | Service Category view (Farmland, Machinery, Labour, Training) |
| 5 | `/dashboard/listings/:listingId` | Listing Details with specs, gallery viewer, provider trust, book/save CTAs |
| 6 | `/dashboard/bookings/new/:listingId` | Validated multi-step booking request form |
| 7 | `/dashboard/bookings/:bookingId/confirmation` | Booking confirmation receipt and provider response notice |
| 8 | `/dashboard/bookings` | My Bookings with status tabs and customer/provider role filters |
| 9 | `/dashboard/bookings/:bookingId` | Booking Details with immutable contract snapshot and timeline |
| 10 | `/dashboard/bookings/:bookingId/messages` | Booking conversation thread |
| 11 | `/dashboard/bookings/:bookingId/completion` | Dual independent completion confirmation panel & dispute trigger |
| 12 | `/dashboard/services` | My Services across categories with status tabs |
| 13 | `/dashboard/services/new` | Multi-step service creation form with verification metadata |
| 14 | `/dashboard/services/:listingId/edit` | Edit Service listing (preserves historical snapshots) |
| 15 | `/dashboard/services/:listingId` | Service Management overview |
| 16 | `/dashboard/services/:listingId/availability` | Service availability calendar, blackout dates, lead times |
| 17 | `/dashboard/services/:listingId/performance` | Service performance metrics (views, enquiries, conversion rate) |
| 18 | `/dashboard/service-requests` | Incoming requests list with status groups |
| 19 | `/dashboard/service-requests/:requestId` | Request details: accept terms, propose counter-price, decline |
| 20 | `/dashboard/messages` | Messages inbox with search and unread indicators |
| 21 | `/dashboard/messages/:conversationId` | Split-pane / full-view chat conversation |
| 22 | `/dashboard/finance` | Financial overview (Gross revenue, net earnings, customer spend) |
| 23 | `/dashboard/finance/transactions/:transactionId` | Transaction details and receipt modal |
| 24 | `/dashboard/finance/earnings` | Provider earnings breakdown ledger |
| 25 | `/dashboard/finance/payouts` | Payouts history and withdrawal request via Bach adapter |
| 26 | `/dashboard/finance/payment-methods` | Customer payment cards and provider NUBAN payout accounts |
| 27 | `/dashboard/reviews` | Reviews overview (Received, Given, Awaiting review) |
| 28 | `/dashboard/reviews/new/:bookingId` | Write Review form with category-specific ratings |
| 29 | `/dashboard/saved` | Saved/bookmarked listings |
| 30 | `/dashboard/notifications` | Notifications with deep links to exact records |
| 31 | `/dashboard/support` | Help Centre with searchable FAQs |
| 32 | `/dashboard/support/new` | Create Support Ticket form |
| 33 | `/dashboard/support/:ticketId` | Support ticket conversation thread |
| 34 | `/dashboard/profile` | Public user profile with credentials and active services |
| 35 | `/dashboard/profile/edit` | Edit profile information |
| 36 | `/dashboard/verification` | Verification Centre for land, machinery, and identity |
| 37 | `/dashboard/verification/:type` | Verification submission form |
| 38 | `/dashboard/settings` | Account settings index |
| 39 | `/dashboard/settings/security` | Security settings, password change, active sessions |
| 40 | `/dashboard/settings/notifications` | Notification channel preferences (In-app, Email, SMS) |
| 41 | `/dashboard/settings/privacy` | Privacy and phone visibility controls |
| 42 | `/dashboard/settings/locations` | Agricultural address book (farmlands, depots, home) |
| 43 | `/dashboard/settings/preferences` | Regional, language, and currency preferences |
| 44 | `/dashboard/settings/account` | Account deactivation inspection |
| 45 | `/dashboard/assistant` | AI Agricultural Assistant grounded in real platform inventory |


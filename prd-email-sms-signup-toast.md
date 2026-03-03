# PRD: Email & SMS Signup Toast
### E-Commerce Web Platform — First-Visit Subscriber Acquisition

---

| | |
|---|---|
| **Product** | E-Commerce Web Platform |
| **Document Type** | Product Requirements Document (PRD) |
| **Status** | Completed |
| **Date** | 2019 |
| **Surface** | Desktop web · Mobile web |
| **Author** | Digital Product |
| **Stakeholders** | Marketing · UX · Engineering · Analytics · CRM |

---

## Table of Contents

1. [Overview](#1-overview)
2. [Background & Problem Statement](#2-background--problem-statement)
3. [Goals & Success Metrics](#3-goals--success-metrics)
4. [Scope](#4-scope)
5. [User Personas](#5-user-personas)
6. [Functional Requirements](#6-functional-requirements)
7. [Non-Functional Requirements](#7-non-functional-requirements)
8. [A/B Test Design](#8-ab-test-design)
9. [Dependencies & Risks](#9-dependencies--risks)
10. [Future Considerations](#10-future-considerations)

---

## 1. Overview

This document defines the requirements for a first-visit email and SMS signup toast — a non-blocking, dismissible notification targeting new visitors to the e-commerce web platform to drive direct subscriber acquisition across DIY and Pro customer segments.

This was the first native email capture mechanism built on the platform. Prior to this feature, subscriber acquisition relied on in-store loyalty sign-up forms and third-party data sharing partnerships — with no owned digital capture surface on the site itself. The feature was validated through an A/B test before a phased rollout.

---

## 2. Background & Problem Statement

### 2.1 Current State

Analytics data showed a consistent pattern: users who arrived via email campaigns converted at a meaningfully higher rate than users from other acquisition channels. Despite this signal, the platform had no owned digital mechanism to grow its subscriber base directly. Subscriber acquisition prior to this feature came from two sources: in-store loyalty sign-up forms and third-party data sharing partnerships (such as change-of-address programs). Neither provided a direct, on-platform capture surface that the digital team could control, iterate on, or integrate with the broader personalization roadmap.

### 2.2 The Opportunity

A first-visit toast — targeted at uncached users who had not previously encountered the prompt — offered a low-friction, non-disruptive acquisition mechanism at the moment of highest receptivity: a user's first engagement with the platform.

The feature also created an opportunity to capture channel preference data across two distinct customer segments. The platform was in the early stages of consolidating separate DIY and Pro web experiences onto a single unified platform. The DIY and Pro segments had historically operated under separate domains with separate marketing channels. A self-identification mechanism within the signup flow provided additive signal on how these audiences were already overlapping on the DIY platform — informing, but not driving, the broader consolidation strategy already underway.

### 2.3 Mobile Extension

Mobile web visitors represented a distinct acquisition opportunity. In addition to email, mobile users were offered the option to provide a phone number for SMS opt-in — a channel with higher open rates and more immediate engagement than email for promotional and transactional communications.

---

## 3. Goals & Success Metrics

### 3.1 Goals

- Launch a native, on-platform email and SMS acquisition mechanism for first-time visitors
- Capture channel segment preference (DIY vs. Pro) at point of signup
- Validate the feature's impact on conversion rate through a controlled A/B test before full rollout
- Establish baseline subscriber acquisition metrics for future optimization

### 3.2 Success Metrics

| Metric | Baseline | Target | Measurement |
|---|---|---|---|
| Form submission rate | 0 (no prior native mechanism) | Establish baseline | Analytics |
| Dismissal rate | 0 | Establish baseline; inform UX iteration | Analytics |
| Conversion rate — email-acquired users vs. control | Existing email campaign CVR | Maintain or improve | Analytics |
| A/B test: CVR variant vs. control | Pre-test CVR | Measurable lift in variant | A/B test analytics |

---

## 4. Scope

### 4.1 In Scope — V1

- **Toast component:** Non-blocking, bottom-of-screen toast targeting first-visit uncached users
- **Desktop variant:** Email input field + DIY/Pro segment checkbox + submit CTA
- **Mobile web variant:** Email input field + phone number field (SMS opt-in) + DIY/Pro segment checkbox + submit CTA
- **Suppression logic:** Cookie-based; toast does not re-display to users who have previously seen or dismissed it
- **Dismiss behavior:** Explicit dismiss control (X); dismissed state persisted via cookie
- **Initial placement:** Homepage only
- **A/B test:** Toast (variant) vs. no toast (control); phased rollout following test validation
- **Segment routing:** Form submissions routed to separate DIY and Pro email/SMS lists based on checkbox selection

### 4.2 Out of Scope — V1

- Appearance on non-homepage pages (scoped for post-launch expansion)
- Personalized toast experience based on user identity or browsing behavior (post-consolidation phase)
- Native app integration
- Double opt-in email confirmation flow
- Preference center or subscription management UI
- Re-engagement prompt for users who dismissed without submitting

---

## 5. User Personas

### 5.1 The First-Time DIY Shopper

A homeowner or renter visiting the platform for the first time — likely arriving via organic search, paid search, or direct navigation. They are browsing for home improvement products or project inspiration. They have no established relationship with the brand's digital channels.

- **Needs:** Low-friction way to stay connected; content and offers relevant to home projects
- **Success:** Submits email; receives DIY-relevant campaigns that drive return visits and conversion

### 5.2 The First-Time Pro Visitor

A contractor, tradesperson, or small business owner visiting the DIY platform — potentially unaware that a separate Pro-specific domain exists, or using the DIY site for its broader product catalog. They have distinct purchasing patterns, higher average order values, and different content needs than DIY shoppers.

- **Needs:** Relevant Pro offers and communications; recognition of their professional context
- **Success:** Self-identifies as Pro; is routed to Pro marketing channel; receives Pro-relevant campaigns
- **Note:** Pro self-identification via the checkbox provided additive signal on cross-segment audience overlap during the platform consolidation period — informing audience sizing estimates without serving as the primary driver of the consolidation decision.

### 5.3 The Mobile-First Shopper

A user accessing the platform on a mobile device — more likely to engage with SMS than email given mobile context. May be in a task-oriented shopping session with low tolerance for interruption.

- **Needs:** Immediate value signal; fast interaction; optional SMS opt-in without friction
- **Success:** Submits phone number for SMS; dismisses without frustration if not interested

---

## 6. Functional Requirements

### 6.1 Toast Component

| Feature | Description | Priority |
|---|---|---|
| Toast placement | Fixed, bottom of viewport; non-blocking; does not obscure primary content or navigation | P0 |
| First-visit targeting | Displays only to users with no suppression cookie set | P0 |
| Suppression cookie | Set on first display; prevents re-display on subsequent visits or after dismiss | P0 |
| Dismiss control | X button closes toast; suppression cookie set on dismiss | P0 |
| Animation | Slides up from bottom on page load; slides down on dismiss | P1 |
| Delay trigger | Toast appears after a configurable delay post-pageload (not immediate) | P1 |

### 6.2 Desktop Variant — Email Signup

| Feature | Description | Priority |
|---|---|---|
| Email input field | Standard email input; validation on submit | P0 |
| DIY / Pro checkbox | Single checkbox or toggle allowing user to self-identify as DIY or Pro | P0 |
| Submit CTA | Primary action button; triggers form submission and cookie suppression | P0 |
| Confirmation state | Toast transitions to confirmation message post-submit | P0 |
| Legal / consent copy | Required opt-in disclosure copy per CRM and legal requirements | P0 |

### 6.3 Mobile Web Variant — Email + SMS Signup

| Feature | Description | Priority |
|---|---|---|
| Email input field | Standard email input; validation on submit | P0 |
| Phone number input field | Tel input; optional field; SMS opt-in | P0 |
| DIY / Pro checkbox | Same as desktop variant | P0 |
| Submit CTA | Submits both email and phone if provided | P0 |
| Confirmation state | Toast transitions to confirmation message post-submit | P0 |
| Legal / consent copy | Must include separate SMS consent disclosure per legal and carrier requirements | P0 |

### 6.4 Segment Routing

| Feature | Description | Priority |
|---|---|---|
| DIY list routing | Submissions with DIY selection routed to DIY email/SMS CRM list | P0 |
| Pro list routing | Submissions with Pro selection routed to Pro email/SMS CRM list | P0 |
| Default routing | If no selection made, route to DIY list as default | P1 |

---

## 7. Non-Functional Requirements

**Performance:** Toast component must not impact page load metrics. JavaScript for toast must be loaded asynchronously and must not block rendering. LCP and CLS must not be negatively impacted by toast animation.

**Accessibility:** Toast must be keyboard-dismissible (Escape key). Form inputs must have appropriate labels. Dismiss button must have descriptive aria-label. Toast must not trap focus.

**Cookie compliance:** Suppression cookie must respect user cookie preferences. Toast must not display if user has opted out of non-essential cookies.

**CRM integration:** Form submissions must integrate with CRM platform in real time. Segment routing (DIY/Pro) must be captured as a list attribute. Failed submissions must be queued for retry; user must not be shown an error state for transient failures.

**SMS compliance:** Phone number collection must comply with TCPA requirements. SMS consent must be explicitly captured and stored. Carrier opt-out (STOP) must be supported.

---

## 8. A/B Test Design

The toast was validated through a controlled A/B test before phased rollout.

| | Control | Variant |
|---|---|---|
| Experience | No toast displayed | Toast displayed on first visit |
| Target | First-time uncached visitors, homepage | First-time uncached visitors, homepage |
| Split | 50/50 | 50/50 |
| Primary KPI | Conversion rate | Conversion rate |
| Secondary KPIs | — | Form submission rate · Dismissal rate |
| Decision criteria | Measurable CVR lift in variant; no negative impact on primary CVR | — |

**Rollout approach:** Following test validation, the toast was ramped up incrementally — increasing traffic exposure before full rollout — to monitor for edge cases and downstream CRM integration issues at scale.

---

## 9. Dependencies & Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Toast perceived as intrusive; high dismissal rate | Medium | Medium | Configurable delay trigger; non-blocking placement; clear dismiss control |
| CRM integration failures causing data loss | Low | High | Retry queue for failed submissions; monitoring and alerting on submission failures |
| SMS compliance gaps (TCPA) | Low | High | Legal review of consent copy before launch; carrier opt-out support required |
| Cookie suppression not persisting across sessions | Low | Medium | QA suppression behavior across browsers and session types before launch |
| DIY/Pro checkbox ignored by users — low segmentation signal | Medium | Low | Default routing to DIY list; segment data treated as directional, not definitive |
| Performance regression from toast JavaScript | Low | Medium | Async load; performance benchmarking pre-launch |

---

## 10. Future Considerations

| Capability | Description |
|---|---|
| Expanded page targeting | Roll out beyond homepage to category and product pages within the shopping funnel — including global footer placement as a persistent low-friction capture point |
| Personalized experience | Post-consolidation: replace DIY/Pro checkbox with personalization token-based segmentation; serve pre-segmented toast to known user types without requiring self-identification |
| Re-engagement prompt | Targeted re-prompt for users who dismissed without submitting — triggered by return visit or engagement threshold |
| Preference center | Allow subscribers to update channel preferences (DIY/Pro, email/SMS) post-signup |
| A/B test: messaging variants | Test different value propositions in toast headline (offers vs. content vs. tips) to optimize submission rate |

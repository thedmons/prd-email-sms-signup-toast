# PRD: Email & SMS Signup Toast
### E-Commerce Web Platform — First-Visit Subscriber Acquisition

---

## Overview

This repository contains the Product Requirements Document for a first-visit email and SMS signup toast — a non-blocking, dismissible notification targeting new visitors to a large home improvement retailer's e-commerce platform to drive direct subscriber acquisition across DIY and Pro customer segments.

This was the first native email and SMS capture mechanism built on the platform. Prior to this feature, subscriber acquisition relied on in-store loyalty sign-up forms and third-party data sharing partnerships — with no owned digital capture surface on the site itself. The feature was validated through a controlled A/B test before phased rollout.

📄 **[Read the full PRD →](./prd-email-sms-signup-toast.md)**

---

## What This Demonstrates

**Data-driven feature origination** — The feature was directly motivated by analytics showing email-acquired users converted at a measurably higher rate than other acquisition channels. The PRD traces the decision from that signal through scoping, test design, and rollout — not a feature request, but a product bet grounded in behavioral data.

**Dual-surface feature design** — Desktop and mobile web variants were scoped with distinct experiences: desktop captured email with DIY/Pro self-identification, while mobile extended the form to include SMS opt-in with separate TCPA-compliant consent copy. Treating mobile as a distinct surface — not a responsive adaptation — reflects how channel behavior differs across form factors.

**Controlled rollout discipline** — Rather than shipping directly, the feature was introduced through a 50/50 A/B test (toast vs. no toast) with conversion rate as the primary KPI and form submission and dismissal rates as secondary signals. Phased ramp-up followed test validation before full rollout.

**User segmentation at point of capture** — DIY and Pro customers had historically operated under separate domains. The checkbox-based self-identification in V1 — later replaced by personalization token-based segmentation post-consolidation — reflects deliberate thinking about how to build segmentation infrastructure incrementally without waiting for a fully unified platform.

**Building an owned digital acquisition channel** — Prior to this feature, subscriber acquisition came from in-store loyalty forms and third-party data sharing partnerships — neither of which gave the digital team a surface to control, optimize, or integrate with the platform's personalization roadmap. The PRD documents the case for building a first-party, on-platform capture mechanism as a strategic capability, not just a conversion tactic.

---

## Document Metadata

| | |
|---|---|
| **Product** | E-Commerce Web Platform |
| **Document Type** | Feature PRD |
| **Status** | Completed |
| **Date** | 2019 |
| **Surface** | Desktop web · Mobile web |
| **Platform** | In-house headless CMS · React · Google Cloud |

---

## Related Artifacts

| Artifact | Description |
|---|---|
| [PRD: E-Commerce CMS Platform Migration](https://github.com/thedmons/prd-ecommerce-cms-migration) | Platform PRD for the broader e-commerce migration this feature was built within — AEM to in-house headless CMS on Google Cloud |

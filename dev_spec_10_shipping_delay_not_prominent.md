# Shipping delay not prominent — dev spec
Site: allbirds.com · Priority 10 · High · Effort: Medium (2-5 days)

## Problem
The product page for the Anytime Ankle Sock does not prominently display the 'up to 30 days to ship' notice, which is only in the sitewide body text, potentially causing expectation mismatch and support inquiries.

## Evidence (from the live site)
> Body sample from homepage: 'Due to increased demand, orders may take up to 30 days to ship.' This is not visible in the product page's H1s, CTAs, or visible copy.

## Current state
h1: Anytime Ankle Sock; cta: Learn More; notes: No mention of shipping delay on the product page.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: Add a shipping delay notice near the price or add-to-cart button.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a shipping delay notice near the price or add-to-cart button.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_shipping_delay_not_prominent` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

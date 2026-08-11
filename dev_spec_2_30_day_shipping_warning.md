# 30-Day Shipping Warning — dev spec
Site: allbirds.com · Priority 2 · High · Effort: Medium (2-5 days)

## Problem
The prominent 'orders may take up to 30 days to ship' warning creates a major objection that could deter immediate purchases.

## Evidence (from the live site)
> Body sample: 'Due to increased demand, orders may take up to 30 days to ship.'

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Warning is visible in body text, likely near top of page.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Soften the message: 'Free shipping on orders over $100' and add a trust element like 'Ships within 30 days' or a progress indicator.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Soften the message: 'Free shipping on orders over $100' and add a trust element like 'Ships within 30 days' or a progress indicator.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_30_day_shipping_warning` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

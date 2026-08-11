# Free shipping threshold hidden — dev spec
Site: allbirds.com · Priority 5 · High · Effort: Medium (2-5 days)

## Problem
The homepage hero promotes 'Free ground shipping' without disclosing the $100 minimum order, creating an expectation gap that may lead to cart abandonment or distrust at checkout.

## Evidence (from the live site)
> Body sample: 'Free ground shipping on orders over $100' appears in the body text, but the hero H1s and CTAs ('Shop All', 'Shop Womens', 'Shop Mens') do not mention the threshold.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Hero copy omits the $100 threshold, while the body text mentions it.

## Required change
h1: Wildly Comfortable. Super Natural. Free Shipping Over $100.; cta: Shop All; notes: Include the threshold in the hero or near the CTA to set accurate expectations.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Include the threshold in the hero or near the CTA to set accurate expectations.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_free_shipping_threshold_hidden` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

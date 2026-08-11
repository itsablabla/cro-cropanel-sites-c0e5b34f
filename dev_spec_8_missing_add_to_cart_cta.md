# Missing Add-to-Cart CTA — dev spec
Site: allbirds.com · Priority 8 · Urgent · Effort: Medium (2-5 days)

## Problem
The product page for 'Anytime Ankle Sock' lacks an explicit 'Add to Cart' or 'Buy Now' call to action, preventing direct purchase.

## Evidence (from the live site)
> The 'ctas' array for '/products/anytime-ankle-sock' includes 'Shop All', 'Shop Womens', 'Shop Mens', 'Shop Socks', 'Shop Women's Sale', 'Shop Men's Sale', 'Learn More', 'Sign Up', 'Shop + -', but does not include 'Add to Cart' or 'Buy Now'.

## Current state
h1: Anytime Ankle Sock; cta: No direct purchase CTA (e.g., Add to Cart) found.; notes: Users cannot easily add the product to their cart from this page, creating a critical path blockage.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: Implement a clear and prominent 'Add to Cart' or 'Buy Now' button on the product page to facilitate immediate purchase.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Implement a clear and prominent 'Add to Cart' or 'Buy Now' button on the product page to facilitate immediate purchase.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_missing_add_to_cart_cta` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

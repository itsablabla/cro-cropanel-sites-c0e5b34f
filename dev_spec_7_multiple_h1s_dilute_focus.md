# Multiple H1s dilute focus — dev spec
Site: allbirds.com · Priority 7 · High · Effort: Low (0.5-2 days)

## Problem
The homepage has 7 H1 tags, including 'www.allbirds.com is blocked' repeated, which confuses both users and search engines, diluting the primary message and harming SEO.

## Evidence (from the live site)
> h1s array includes 'Wildly Comfortable. Super Natural.' and four instances of 'www.allbirds.com is blocked'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Multiple H1s, including error text, on the homepage.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Ensure only one H1 per page, remove error text from H1s, and use H2s for subheadings.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Ensure only one H1 per page, remove error text from H1s, and use H2s for subheadings.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_multiple_h1s_dilute_focus` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

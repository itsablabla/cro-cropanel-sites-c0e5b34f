# Vague hero copy — dev spec
Site: allbirds.com · Priority 4 · High · Effort: Low (0.5-2 days)

## Problem
The hero H1 'Wildly Comfortable. Super Natural.' is a brand slogan that doesn't communicate product benefits or address visitor intent, causing confusion and reducing conversion.

## Evidence (from the live site)
> H1: 'Wildly Comfortable. Super Natural.'; CTA: 'Shop All'

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: The hero lacks clarity about what Allbirds sells (shoes) and why it's better. Visitors arriving with intent to buy shoes may not see a clear path.

## Required change
h1: Comfortable Shoes, Naturally Made; cta: Shop Men's Shoes; notes: Make the product category explicit and lead with a key benefit (comfort) and differentiator (natural materials). Use a more specific CTA to guide visitors.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Make the product category explicit and lead with a key benefit (comfort) and differentiator (natural materials). Use a more specific CTA to guide visitors.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_vague_hero_copy` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

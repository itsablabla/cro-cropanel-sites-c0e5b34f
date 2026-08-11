# Redundant Hero CTAs — dev spec
Site: allbirds.com · Priority 3 · High · Effort: Medium (2-5 days)

## Problem
Multiple 'Shop' CTAs in the hero section and navigation dilute the primary user path and create decision fatigue.

## Evidence (from the live site)
> The 'ctas' array for '/' contains 'Shop All', 'Shop Womens', 'Shop Mens', 'SHOP MEN', 'SHOP WOMEN'.
> The primary H1 is 'Wildly Comfortable. Super Natural.'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: Shop All, Shop Womens, Shop Mens, SHOP MEN, SHOP WOMEN; notes: Too many similar 'Shop' CTAs compete for attention, especially 'Shop Mens' vs 'SHOP MEN' and 'Shop Womens' vs 'SHOP WOMEN', making the primary action unclear.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Consolidate primary 'Shop' CTAs to a single, clear option (e.g., 'Shop All' or distinct 'Shop Men' and 'Shop Women' if they lead to different hero experiences). Remove redundant 'Shop' links from the main hero area to streamline the user's choice.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Consolidate primary 'Shop' CTAs to a single, clear option (e.g., 'Shop All' or distinct 'Shop Men' and 'Shop Women' if they lead to different hero experiences). Remove redundant 'Shop' links from the main hero area to streamline the user's choice.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_redundant_hero_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

# Blocked H1s — dev spec
Site: allbirds.com · Priority 1 · Urgent · Effort: Medium (2-5 days)

## Problem
Multiple H1s display 'www.allbirds.com is blocked' due to bot detection, undermining trust and confusing users.

## Evidence (from the live site)
> Multiple H1s: 'Wildly Comfortable. Super Natural.', 'www.allbirds.com is blocked' (repeated 4 times). This indicates a technical issue where the page is blocked or not rendering properly, leading to duplicate H1s.
> H1s include 'www.allbirds.com is blocked' repeated 4 times; body sample shows 'Due to increased demand, orders may take up to 30 days to ship.'

## Current state
h1: Wildly Comfortable. Super Natural. (plus 4 instances of 'www.allbirds.com is blocked'); cta: Shop All; notes: The presence of 'blocked' text in H1s is a technical glitch that undermines credibility and may confuse screen readers.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All; notes: Fix the technical issue causing the 'blocked' text. Ensure only one H1 per page and that it clearly communicates the value proposition.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Fix the technical issue causing the 'blocked' text. Ensure only one H1 per page and that it clearly communicates the value proposition.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_blocked_h1s` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.

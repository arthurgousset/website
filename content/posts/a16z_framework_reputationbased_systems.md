---
title: "🧵 A Framework for Reputation-based Models with a16z"
date: 2021-10-21T12:00:00+01:00
draft: false
tags: ["a16z", "reputation"]
---

## Reference

[A Novel Framework for Reputation-Based Systems](https://future.a16z.com/reputation-based-systems/)

## TL;DR:

- **Paradox**: easily transferable reputation (liquidity) = less meaningful reputation (signal)
- **Solution**: `reputation points` (cannot be traded) + `liquidity coins` (can be traded)
- Users receive non-tradable `reputation points` (= for signalling) that pay **dividends** in the form of a tradable `liquidity coin`. Demand for liquidity coins makes having many reputation points desirable.
- 3 **parameters** for **dividend design**:
    1. the “**size**” of overall dividends (how many coins are issued across all users?) [n.b: doesn’t have to be asymptotically bound],
    2. the “**supply**” of dividends (how regularly are coins issued?) [n.b: preferably regularly],
    3. the “**distribution**” of dividends across users (how does coin receipt relate to point ownerships?) [n.b: linearly = 1:1, convex = favours the rich, concave = favours the poor]
- (ideally) dividend design satisfies: `marginal value (to platform)` = `marginal value (to user)` [n.b: this favours early contributors, but early contributors != most valuable to the platform]
- Two improvements Down pointing backhand index
- Two improvement Electric light bulb:
    1. **depreciating** points over time can help, or
    2. points can be **zero-sum**, i.e. users maintain/lose points as a function of their engagement relative to others
- but (!) don‘t overfinancialise it: (after all) it "should" be product-market fit that motivates users to use the platform not profit, i.e. optimise for engagement (=users) not profit generation (= speculators)

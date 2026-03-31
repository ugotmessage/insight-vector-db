# Valuation Brief Usage

## Purpose
`valuation_brief` is a human-facing decision support card.

It is used after a stock becomes interesting enough to deserve deeper review. Its purpose is to help the user quickly identify which names still have upside and which ones are already expensive.

## Why this is not a core self-improvement card
This card is highly useful for human workflow, but it is not the best primitive for self-improvement because:
- it mixes real-time price anchoring with judgment
- it depends on current market price freshness
- it is more of a decision brief than a reusable atomic research unit

So it should be treated as a user-facing card, not the central machine-learning card.

## Recommended placement in the pipeline
Use it after one of these conditions:
- a stock is explicitly recommended
- the same stock appears across multiple sources
- the stock belongs to an active research topic
- the user wants a shortlist of potentially attractive names

Recommended flow:
- raw_source -> episode -> insight
- raw_source -> stock_pick
- insight / stock_pick / research_topic -> valuation_brief

## What this card is good for
- quickly filtering for stocks with room to run
- checking whether the current price still leaves upside
- comparing valuation attractiveness across several mentioned names
- generating a watchlist with priority order

## Suggested follow-up actions
Based on `next_action`, the system can:
- move the stock to watchlist
- request deeper research
- wait for pullback
- archive if upside is insufficient

## Key rule
Do not generate `valuation_brief` for every mentioned stock.
Use it only for names with enough context or enough importance.

## Example user query enabled by this card
- 幫我把最近提到的股票中，還有肉的挑出來
- 哪些標的目前評價仍合理，不只是題材熱
- 哪些股票可以列入 watchlist，等拉回再看

# Stock Pick Card Usage

## Why this card exists
Some financial content does not just discuss themes or industries. It explicitly recommends stocks.

That kind of content should not be stored only as general `insight` cards, because you will want to track:
- who recommended the stock
- what the recommendation direction was
- why it was recommended
- the expected holding period
- whether the recommendation later worked or failed

## Recommended handling
### 1. Keep the original research cards
Still generate:
- `episode`
- `insight`
- `analyst_report` if needed

### 2. Add stock_pick cards only when the recommendation is explicit
Examples:
- 「這檔可以買」
- 「這檔列入觀察名單」
- 「這裡先不要碰」
- 「可以續抱但不要追」
- 「回檔可布局」

### 3. One stock pick card = one speaker + one stock + one action
Do not merge multiple stocks or multiple speakers into one card.

## Relationship to other cards
Recommended structure:
- raw_source -> episode -> insight
- raw_source -> episode -> analyst_report
- raw_source -> episode/article -> stock_pick

## Why not merge into analyst_report?
Because `analyst_report` is for human reading.
`stock_pick` is for tracking, scoring, later validation, and portfolio follow-up.

## Suggested downstream usage
A stock_pick card can later generate:
- candidate_stock card
- validation card
- hit-rate tracking by speaker
- strategy review notes

## Status lifecycle
Suggested statuses:
- active
- watching
- expired
- invalidated
- hit_target
- stopped_out

## Example future questions this enables
- Which analyst has the best hit rate on AI server names?
- Which recommended stocks failed because timing was wrong rather than thesis wrong?
- Which watchlist ideas later became valid entries?

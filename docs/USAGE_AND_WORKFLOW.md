# Usage and Workflow

## 1. Project purpose
This project turns raw financial content into reusable research cards, then promotes those cards into research topics, hypotheses, rules, and validation records.

The system is designed for two parallel lines:
- Opportunity line: find investable themes and candidate stocks
- Learning line: create testable hypotheses and refine the research system over time

## 2. End-to-end workflow

### Step 1: ingest raw source
Input examples:
- video transcript
- article
- podcast transcript
- broker report
- user note

Output:
- `raw_source` card

### Step 2: build episode card
Use the raw source to create an `episode` card.
This is the structured overview of one program or one source unit.

Output:
- `episode` card

### Step 3: extract insight cards
From the transcript or source text, extract multiple `insight` cards.
Each card must represent:
- one speaker
- one topic
- one clear viewpoint

Output:
- one or more `insight` cards

### Step 4: extract counterviews
Generate `counterview` cards only when there is a meaningful challenge, missing assumption, valuation concern, or alternative explanation.

Output:
- zero or more `counterview` cards

### Step 5: promote to research topic
If multiple insight cards suggest an expandable theme, create a `research_topic` card.
A valid topic should have follow-up research value and identifiable beneficiary chains.

Output:
- zero or more `research_topic` cards

### Step 6: generate hypothesis cards
Transform insights and counterviews into `hypothesis` cards.
A hypothesis must be testable and should define:
- trigger or condition
- expected outcome
- evaluation window
- validation method

Output:
- zero or more `hypothesis` cards

### Step 7: validate
Run event study, backtest, or case review, then write the result into a `validation` card.

Output:
- one or more `validation` cards

### Step 8: update rules
When multiple insights and validations support the same reusable pattern, generate a `rule` card.

Output:
- zero or more `rule` cards

## 3. Minimal working flow for MVP
For the first MVP, only implement this path:

1. raw_source
2. episode
3. insight
4. research_topic

This is enough to support:
- semantic search
- topic memory
- repeated theme detection

## 4. Recommended working order

### Phase A: structure only
- define schemas
- define prompts
- define example cards

### Phase B: extraction scripts
- raw -> episode
- episode/raw -> insight
- insight cluster -> research_topic

### Phase C: learning loop
- insight -> counterview
- insight + counterview -> hypothesis
- hypothesis -> validation
- insight + validation -> rule

## 5. Suggested repository layout

```text
/docs
  /architecture
  /schemas
  /prompts
/examples
/scripts
/config
/data
```

## 6. How to use examples
Start with `examples/001_probe_theme/`.
Read the files in this order:
1. `raw_source.json`
2. `episode.json`
3. `insight_001.json`
4. `insight_002.json`
5. `counterview_001.json`
6. `research_topic_001.json`
7. `hypothesis_001.json`
8. `rule_001.json`
9. `validation_001.json`

This shows how one transcript fragment can evolve into a complete research chain.

## 7. Operating rules
- Raw content should be stored once and remain unchanged.
- Every higher-level card must reference upstream ids.
- Do not merge multiple speakers into one insight card.
- Do not create research topics from weak repetition alone.
- Do not create hypotheses that cannot be tested.
- Preserve counterviews instead of forcing one narrative.

## 8. Current status
Currently available in this repo:
- architecture docs
- card schemas
- prompt specs
- one full example chain

Not yet added:
- actual extraction scripts
- embedding pipeline
- vector database integration
- scheduler and automation

## 9. Next implementation targets
1. add `scripts/extract_episode.py`
2. add `scripts/extract_insights.py`
3. add `scripts/promote_topic.py`
4. add `scripts/generate_hypothesis.py`
5. add `scripts/store_to_vector_db.py`

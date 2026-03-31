# Analyst Report Card Usage

## Purpose
`analyst_report` is a human-facing card.

It is designed for reports that are meant to be read directly by the user, rather than primarily used for retrieval, clustering, or validation.

This card should be used only for selected programs or selected content sources where a polished analyst-style report is useful.

## When to use
Use `analyst_report` when:
- the user wants a readable professional report
- the content is a selected YouTube program, article, or transcript
- the goal is summary + investment interpretation for human review

Do not use `analyst_report` as a replacement for:
- `insight` cards
- `hypothesis` cards
- `rule` cards

Those cards remain the machine-oriented research units.

## Source handling
### YouTube source
If the source is a YouTube video:
- use `@YouTube`
- generate a standard analysis-video style report

### Article or transcript source
If the source is an article or transcript:
- generate the report directly from the provided content
- do not invent facts that are not present in the source

## Output sections
An `analyst_report` card should contain:
1. executive summary
2. key data and metrics
3. bull case
4. bear case / risks
5. key opinions by speaker
6. fact vs opinion notes
7. trading takeaways and mentioned targets

## Relationship to other cards
Recommended relationship:
- raw_source -> episode -> analyst_report
- raw_source -> episode -> insight

This means the same source can generate both:
- machine cards for the research system
- human report cards for direct reading

## Example
See:
- `examples/001_probe_theme/analyst_report_001.json`
- `docs/prompts/analyst_report.prompt.md`
- `docs/schemas/analyst_report.schema.json`

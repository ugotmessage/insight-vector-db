# insight-vector-db 導覽

這個 repo 是一套 **卡片化（card-based）財經研究系統**。

核心目標有兩條線：
- **Machine cards**：給 OC / AI 做研究、召回、驗證、升級
- **Human-facing cards**：給你直接閱讀、快速挑題材、挑股票、做決策輔助

---

## 先看哪裡

### 1. 想快速懂整體架構
先看：
- `docs/USAGE_AND_WORKFLOW.md`
- `docs/architecture/card-flow.md`
- `docs/architecture/system-manifest.md`

### 2. 想看卡片長什麼樣
先看：
- `examples/001_probe_theme/`

建議閱讀順序：
1. `raw_source.json`
2. `episode.json`
3. `insight_001.json`
4. `insight_002.json`
5. `counterview_001.json`
6. `research_topic_001.json`
7. `hypothesis_001.json`
8. `rule_001.json`
9. `validation_001.json`
10. `analyst_report_001.json`
11. `valuation_brief_001.json`

### 3. 想看所有 schema
在：
- `docs/schemas/`

### 4. 想看所有 prompt
在：
- `docs/prompts/`

---

## 卡片分類

## A. Machine cards（系統核心卡）
這些卡是給系統做：
- 向量檢索
- 主題升級
- 假說生成
- 驗證
- 規則更新

主要包括：
- `raw_source`
- `episode`
- `insight`
- `counterview`
- `research_topic`
- `hypothesis`
- `rule`
- `validation`
- `stock_pick`

---

## B. Human-facing cards（給你看的卡）
這些卡的重點是：
- 給你直接閱讀
- 讓你快速掌握內容
- 讓你快速挑出值得研究或還有肉的股票

主要包括：
- `analyst_report`
- `valuation_brief`

### analyst_report
用途：
- 把節目 / 文章 / 逐字稿整理成專業人類閱讀報告
- 適合快速看 bull / bear / key opinions / key metrics

相關文件：
- `docs/schemas/analyst_report.schema.json`
- `docs/prompts/analyst_report.prompt.md`
- `docs/ANALYST_REPORT_USAGE.md`

### valuation_brief
用途：
- 給你快速看某檔股票現在還有沒有肉
- 用現價、雙年 EPS、PEG、催化劑、風險做 one-pager 判斷
- 很適合用來讓 OC 幫你挑 shortlist

相關文件：
- `docs/schemas/valuation_brief.schema.json`
- `docs/prompts/valuation_brief.prompt.md`
- `docs/VALUATION_BRIEF_USAGE.md`

---

## 常見流程

### 1. 一般節目 / 文章
`raw_source -> episode -> insight`

### 2. 有反方觀點
`insight -> counterview`

### 3. 題材開始成形
`insight cluster -> research_topic`

### 4. 想做可驗證研究
`insight + counterview -> hypothesis -> validation -> rule`

### 5. 有明確推薦持股
`source -> stock_pick`

### 6. 想整理成給你看的專業摘要
`source -> analyst_report`

### 7. 想挑出還有肉的股票
`insight / stock_pick / research_topic -> valuation_brief`

---

## 使用建議

### 如果你要的是 AI 自我提升
優先看：
- `insight`
- `counterview`
- `research_topic`
- `hypothesis`
- `validation`
- `rule`

### 如果你要的是人類決策效率
優先看：
- `analyst_report`
- `stock_pick`
- `valuation_brief`

---

## 目前 repo 狀態
已完成：
- 架構文件
- 主要 schema
- 主要 prompt
- 一組完整 example chain
- analyst_report / stock_pick / valuation_brief 的獨立定義

尚未完成：
- scripts
- embedding pipeline
- vector DB integration
- scheduler / automation

---

## 下一步最值得做
1. 建 `scripts/` 骨架
2. 做 `extract_episode.py`
3. 做 `extract_insights.py`
4. 做 `extract_stock_picks.py`
5. 做 `generate_analyst_report.py`
6. 做 `generate_valuation_brief.py`
7. 接向量資料庫

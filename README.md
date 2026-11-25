# claude_code_rules

給 Claude Code 用的通用守則：一份 `CLAUDE.md`、四份 rules、四個 skills，可套用在任何專案。

守則內容以英文撰寫；其中規定 Claude 回覆使用者、提問與撰寫使用者文件時，一律使用台灣用語的繁體中文。

## 內容

| 路徑 | 載入時機 | 內容 |
|---|---|---|
| `CLAUDE.md` | 每次對話 | 語言、提問方式、四項工作原則、誠實與驗證、回報格式，最後一節留給專案專屬說明 |
| `.claude/rules/code-style.md` | 每次對話 | 註解、結構、命名與錯誤處理、變更衛生、安全底線、效能主張 |
| `.claude/rules/workflow.md` | 每次對話 | 計畫、範圍、測試、除錯、量測與查證、subagent 交辦、review、Git |
| `.claude/rules/writing.md` | 每次對話 | 通用寫作規則、台灣繁體中文用語、英文規則、畫面上的文字 |
| `.claude/rules/ui.md` | 編輯 HTML／CSS／JSX／TSX／Vue／Svelte 時 | UI 的 Floor／Reflex／Finish 三級準則與檢查流程 |
| `.claude/skills/ui-design` | 建立或修改介面時 | 設計方向、字體、色彩、版面、動效、狀態、控制項、RWD、交付前檢查 |
| `.claude/skills/ui-audit` | 審查既有介面時 | 嚴重度分級、設計評分（40 分）與技術評分（20 分）、報告格式 |
| `.claude/skills/deslop-writing` | 撰寫或修改文章、文件、文案時 | 偵測／修改／起草三種模式、中英文的 AI 寫作特徵、註解清理 |
| `.claude/skills/web-quality` | 開發或審查 web 應用與網路服務時 | 安全檢查清單、可靠性、效能預算、爬蟲與自動化 |

## 使用方式

套用到單一專案：把 `CLAUDE.md` 與 `.claude/` 複製到專案根目錄，再改寫 `CLAUDE.md` 最後的 `## Project` 一節。

```bash
cp -r CLAUDE.md .claude /path/to/your/project/
```

套用到本機所有專案：把內容放到 `~/.claude/`（`~/.claude/CLAUDE.md`、`~/.claude/rules/`、`~/.claude/skills/`），各專案的 `CLAUDE.md` 只寫專案專屬的部分。

專案已有 `CLAUDE.md` 或 `.claude/` 時請手動合併，不要直接覆蓋。

## 幾個刻意的取捨

- **提問**：需要使用者決定的問題列在回覆最前面並附建議答案；可以自己查到或選項明確的，集中在最後一題列出預設值，使用者只需確認是否更改。
- **結構門檻**（函式約 50 行、檔案約 300 行、巢狀 3 層）只當作撰寫新程式碼時的警訊，不為了門檻重構既有程式碼。
- **UI 分級**：Floor 絕不出貨；Reflex 預設避免，有產品專屬理由可破例並記錄；Finish 不阻擋出貨。
- **註解**：只解釋「為什麼」，不留 `TODO`；未完成的事項在回覆中列出。
- **資料**：不捏造任何數字、名稱、引言或來源；示意內容一律標示。
- **效能與安全的數字門檻**只放在 `web-quality` skill，不套用到腳本、嵌入式或離線工具。
- 不安裝任何外掛、hook 或腳本；只有純文字規則。

## 出處

本守則是閱讀下列專案後重新整理、改寫而成，並非逐字複製；各專案的工具、hook、偵測器與安裝流程都沒有納入。

| 專案 | 授權 | 取用的部分 |
|---|---|---|
| [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) | 該 repo 未標示授權 | 四項工作原則：先想清楚、簡單優先、手術式修改、目標導向 |
| [miqdadbadjuber/anti-slop](https://github.com/miqdadbadjuber/anti-slop) | MIT | purpose test、註解清理、文案與 UI 的 AI 特徵、無障礙與 RWD 硬性項目 |
| [elangalfarez/no-slop](https://github.com/elangalfarez/no-slop) | MIT | 不捏造／少說／有理由才做／看過才說完成、工程與架構準則、流程與回報、寫作規則、控制項做法、安全檢查 |
| [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | Apache-2.0 | 設計基本功（字體、色彩、版面、動效、狀態）、依介面類型決定設計力道、critique 與 audit 的評分方式 |
| [nutlope/hallmark](https://github.com/nutlope/hallmark) | MIT | UI 的 Floor／Reflex／Finish 分級 |

授權資訊取自各 repo 在 GitHub 上的標示（2026-11-25 查詢）。

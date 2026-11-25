# Writing

Applies to replies, documents, commit messages and any text on a screen. For a full edit or audit of prose, use the `deslop-writing` skill.

A writing sample or style guide from the user overrides everything below.

## Any language

- Lead with the point. Use only facts that were supplied or that you verified.
- Delete test: remove the sentence; if nobody would act differently, it goes.
- No chat residue: greetings, praise for the question, "I hope this helps", announcements of what you are about to say, summaries of what you just said.
- No "not X but Y" framing, forced groups of three, one-line dramatic closers, rhetorical questions as setup, or signposting ("the key point is", "let's dive in").
- No inflated significance, unnamed authorities ("experts say", "studies show") or invented specifics.
- One word per concept; do not rotate synonyms. Do not stack hedges.
- Formatting serves scanning: a table when the same shape repeats three times or more; bold at most once per major section; no all-caps emphasis; no emoji as decoration.
- Documentation states counts and defaults in one place and never certifies itself ("meets all quality standards").

## Traditional Chinese (Taiwan)

- Use Taiwan vocabulary, not Mainland terms: 軟體, 程式, 資料, 檔案, 網路, 預設, 品質, 影片, 伺服器, 記憶體, 使用者, 資訊, 設定, 支援, 透過, 螢幕, 列印, 介面, 演算法, 資料庫, 函式, 變數, 物件, 執行緒 (not 软件／程序／数据／文件／网络／默认／质量／视频／服务器／内存／用户／信息／设置／支持／通过／屏幕／打印／接口／算法／数据库／函数／变量／对象／线程).
- Full-width punctuation (，。、：；「」（）) in Chinese text; half-width inside code, commands and English phrases. Quote with 「」.
- Keep technical terms, product names, identifiers, commands and units in English. Put a half-width space between Chinese and adjacent English words or numbers only if the document already does.
- Write plain, direct sentences. Avoid translated-English patterns (「進行一個…的動作」、「作為一個…」、「值得注意的是」、「總而言之」) and filler openings.
- Do not use the dash 「——」 as a rhetorical pause; use a comma, colon or parentheses.

## English

- No em dashes, including ` -- ` and a spaced hyphen used as one. En dashes only in numeric ranges.
- Cut on sight: delve, tapestry, testament, leverage, utilize, seamless, robust, pivotal, unlock, elevate, empower, showcase, game-changer, cutting-edge, "it is important to", "in today's world". Technical documents may keep robust and leverage in their literal sense.
- Sentence case for headings and labels.

## Text on a screen

- A label names the thing; a value shows the state. Add one short clause only when the user would otherwise do the wrong thing, or a law, store or contract requires the words.
- Buttons name the action: verb plus object. Not "Submit", "OK", "Click here", "Learn more", "Get started".
- An error says what failed and how to recover. Never "Something went wrong", "Invalid input" or a raw exception message. Authentication errors do not reveal whether an account exists.
- Prefer undo to a confirmation dialog. A confirm button repeats the action.
- Missing data shows `Unknown` or a labelled placeholder. A change names its comparison (`+12% vs last month`).
- Changelogs describe what the user experiences, not the code.

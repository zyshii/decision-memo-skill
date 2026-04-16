# Notion Workflow

This file defines how the skill publishes memos to Notion. Follow the procedure exactly — Notion structure is meant to stay consistent across projects and over time.



## Project Prefix Table

Maintain a running table of project-to-prefix mappings. Extend it whenever a new project appears.

| Project | Prefix | Notion Parent Page |
|---|---|---|
| (project 1 name) | (2-4 letter prefix) | (parent page reference) |
| (project 2 name) | (2-4 letter prefix) | (parent page reference) |

When the user names a project not in the table:
1. Ask: "What prefix would you like to use for this project going forward?" (suggest one derived from the name, e.g., first 2-4 letters or an acronym)
2. Ask: "Do you have a Notion parent page for this project, or should I ask where to put it?"
3. Record the answer in the table for future calls.

Prefix conventions:
- 2-4 uppercase letters
- Derived from the project name (acronym, initials, or truncation)
- Unique across the user's project set

## ID Assignment

Format: `[PREFIX]-NNN` for Full Mode, `[PREFIX]-Q-NNN` for Quick Capture.

To assign the next ID:
1. Fetch the `Decision Memos — [Project]` index page
2. Read the index table to find the highest existing number for that mode
3. Increment by 1
4. Pad to 3 digits (001, 002, ..., 099, 100)

Full and Quick sequences are independent: `PREFIX-001` and `PREFIX-Q-001` can coexist.

## Directory Structure

```
[Project parent page]
  ├── [Project] — Case Study Draft (existing)
  └── Decision Memos — [Project] (index page)
       ├── [Quick Captures] (optional subpage, if Quick mode memos exist)
       │    ├── PREFIX-Q-001 · ...
       │    └── PREFIX-Q-002 · ...
       ├── PREFIX-001 · [Full memo title]
       └── PREFIX-002 · [Full memo title]
```

Quick captures nest under a `Quick Captures` subpage to keep the index clean. Full memos sit directly under the index.

## Index Page Structure

Every project's `Decision Memos — [Project]` page has the same structure:

### Content

```markdown
**用途**：记录 [Project] 项目中的关键设计决策，供 portfolio case study 和 BQ 面试叙事复用。

**模板版本**：v2

**使用原则**：
- Part A 写真实（内部复盘，可以包含政治判断和自我批评）
- Part B 写视角（对外叙事，保留决策逻辑、剥离敏感信息）
- 真实优先于漂亮，权衡优先于结果
- 不知道就写「不知道」

---

## Memo Index

<table header-row="true">
<tr>
<td>ID</td>
<td>Title</td>
<td>模式</td>
<td>重要性</td>
<td>我的角色</td>
<td>状态</td>
</tr>
(rows appended per memo)
</table>
```

When creating a new memo, update this table with a new row. When a Quick memo is upgraded to Full, update the existing row rather than creating a duplicate.

## Publish Procedure

### Step 1 — Locate or create the index page

1. Fetch the project parent page
2. Check children for `Decision Memos — [Project]`
3. If exists, use its ID
4. If not, create it as a child of the project parent page with the standard content template above and icon `🧭`

### Step 2 — For Quick Capture mode: locate or create Quick Captures subpage

1. Fetch the index page
2. Check children for `Quick Captures`
3. If not exists, create it as a child of the index page, icon `⚡`

### Step 3 — Create the memo page

- Parent: index page (for Full) or Quick Captures subpage (for Quick)
- Title format: `[PREFIX]-NNN · [Short title]` or `[PREFIX]-Q-NNN · [Short title]`
- Icon: pick based on memo theme (examples: 🔄 for pivots, 🏛️ for governance, 🤝 for collaboration, 🧩 for problem-framing, ⚖️ for tradeoffs, 🚧 for constraints)
- Content: rendered from the appropriate template

### Step 4 — Update the index table

Append a row with:
- ID
- Title (matching the page title, minus the ID prefix)
- 模式: `Full` or `Quick`
- 重要性: 🔴 High / 🟡 Medium / 🟢 Low
- 我的角色: from the memo's metadata
- 状态: ✅ 已完成 / 🟡 搭建中 / 🟠 进行中

Use `notion-update-page` with `update_content` to insert the new row before the closing `</table>` tag.

### Step 5 — Return the link

After successful creation, return the memo URL to the user in the form:

> ✅ 已创建：[`PREFIX-NNN · Title`](notion URL)
>
> Index 页已同步更新。

## Upgrade Procedure (Quick → Full)

When the user asks to upgrade a Quick memo to Full:

1. Fetch the Quick memo content
2. Extract existing fields into the Full template structure
3. Identify gaps (sections not in Quick that Full requires)
4. Interview only for the gaps — do not re-ask what's already captured
5. Create a new Full memo with a fresh Full ID (`PREFIX-NNN`, next in sequence)
6. On the original Quick memo page, add a callout at the top:

   > 📄 This Quick Capture has been expanded into Full Memo [`PREFIX-NNN`](link). See there for the complete retrospective.

7. Update the index row: change 模式 from `Quick` to `Full → PREFIX-NNN`, or update the row to reflect the new Full ID

Do not delete the Quick memo — preserving the original capture is useful for seeing how the user's thinking evolved.

## Error Handling

If a Notion operation fails:
- Report the failure to the user with the specific step that failed
- Do not attempt silent retries of destructive operations
- For read operations, retry once with broader search terms if the first attempt returned nothing
- If the user's Notion doesn't have the expected structure (e.g., no project parent page), ask how they'd like to set it up rather than guessing

## Privacy Notes

Memos contain potentially sensitive content (company names, stakeholder dynamics, internal politics). The skill's Notion workflow assumes the user's Notion is private to them. Do not export memo content outside Notion without explicit user request.

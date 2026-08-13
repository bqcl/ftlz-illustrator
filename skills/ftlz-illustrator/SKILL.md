---
name: ftlz-illustrator
description: Analyze Markdown articles and generate Chinese Markdown prompts for public-account illustrations with a consistent uploaded character reference, pure white backgrounds, rounded comic typography, and structured prompt sections. Use when the user uploads or pastes a .md article and wants illustration suggestions, cover/explainer/flow/comparison/path visual plans, confirmation before final prompts, or any prompt-only image workflow that should not call an image generation API.
---

# FTLZ Illustrator

Create reusable `.md` image prompts for public-account article illustrations. The normal workflow is: read a Markdown article, analyze where illustrations would help, ask the user to adjust or confirm the illustration plan, then generate one Markdown prompt per approved image. Do not generate images or call image backends.

The user will usually copy each generated prompt into ChatGPT Image or another image tool together with their own uploaded character reference image.

## Core Rules

- Output Chinese Markdown prompt files or Chinese prompt text only.
- Do not generate images. Never invoke `imagegen`, API backends, or external generation scripts.
- When given a Markdown article, analyze the article first and propose an illustration plan before final prompts.
- Do not create final prompt files until the user confirms the plan, unless the user explicitly says "直接生成提示词", "不用确认", or equivalent.
- Assume the user may upload a character reference image separately. Refer to it generically as "随同上传的角色参考图"; never require a specific filename.
- Treat the uploaded reference image as a character asset only. It defines the character identity, clothing, proportions, and overall temperament; it must not define composition, machinery, background, props, or layout unless the user explicitly says so.
- Do not include bundled character images, personal assets, local paths, account names, real names, contact information, or private article drafts in the skill output.
- Default aspect ratio is `16:9` unless the user specifies another ratio.
- Default background is pure white with generous whitespace.
- Always include the character unless the user explicitly asks for a no-character image.
- Keep Chinese text short, large, rounded, and legible. Prefer labels and title words over paragraphs.

## Article Workflow

Use this workflow when the user uploads or pastes a `.md` article.

1. Read the Markdown article.
2. Analyze:
   - title or working title
   - article type: narrative, technical, historical, tutorial, opinion, research, or mixed
   - core thesis in one sentence
   - 3-5 key points
   - sections where an illustration would improve comprehension, pacing, or shareability
3. Recommend an illustration plan before writing final prompts.
4. Ask the user to confirm, remove, add, reorder, or revise the plan.
5. After confirmation, generate one `.md` prompt per approved image.
6. Remind the user to upload the character reference image together with each prompt when generating in ChatGPT Image.

## Illustration Plan Format

Present the plan in Chinese:

```text
我建议生成 X 张图：

1. [位置]: [文章开头/某小节后/结尾]
   类型: [cover/flow/comparison/explainer/path-or-location/scene]
   作用: [这张图解决什么理解问题]
   画面概念: [一句话构图]
   文字标签: ["标签1", "标签2", "标签3"]

请确认：保留/删除/调整哪几张？确认后我再生成每张图对应的 .md prompt。
```

If the article is short, recommend 1-2 images. For a long article, recommend 3-5 images unless the user asks for more. Avoid over-illustrating.

## Pattern Selection

Choose the pattern that best fits each approved image:

- Cover: article header, main concept, or share image.
- Flow: steps, workflows, methods, tool usage.
- Comparison: two versions, before/after, competing interpretations.
- Explainer: abstract ideas, technical concepts, historical clues.
- Path Or Location: maps, directions, origins, routes, textual evidence chains.
- Scene: narrative, mood, or character-led metaphor.

Read `references/prompt-patterns.md` when choosing or explaining patterns.
Read `references/visual-style.md` for the default illustration style.
Read `references/typography.md` for all on-image Chinese text rules.

## Direct Prompt Workflow

If the user asks for a single prompt without providing an article, skip the article analysis and generate the prompt directly. If the request is broad, offer 1-3 visual concepts first.

## Standard Prompt Format

Use this section order for every final prompt:

```text
请根据随同上传的角色参考图生成一张公众号文章配图插画。上传的参考图只用于确定人物角色形象，不用于参考构图、背景、道具或其他画面元素。

STRUCTURE:
[用一到两句话描述整体构图。]

NODES:
[列出必须出现的视觉节点和准确的短文字标签。]

RELATIONSHIPS:
[说明节点之间如何连接，以及角色正在做什么。]

CHARACTER:
严格参考随同上传的角色参考图中的人物角色，只保持人物身份、发型、服装、比例和整体气质一致。参考图只作为人物角色资产，不包含也不决定背景、道具或画面构图。请在新画面中自然地重绘这个角色，而不是复刻参考图的排列方式或设定图布局。

STYLE:
[使用 references/visual-style.md 的风格基底，并根据文章主题调整。]

TYPOGRAPHY:
[使用 references/typography.md 的文字规范，并列出所有需要准确生成的中文标签。]

BACKGROUND:
纯白背景，保留充足留白，不使用复杂纹理、纸张底色、渐变背景或深色背景。

ASPECT:
16:9 横向构图。

CONSTRAINTS:
[准确性、可读性、角色一致、身体和手部完整、道具原创、画面不拥挤。]

AVOID:
[错误中文、真实 logo、二维码、长文本块、杂乱背景、错误肢体、畸形手指、模糊小字。]
```

## Prompt Quality Checklist

Before finalizing, verify:

- The prompt says the uploaded image is only for character reference.
- The composition is specific enough to draw without seeing the article.
- Every on-image Chinese label is listed exactly and kept short.
- There is a clear role for the character: explainer, observer, operator, guide, comparer, or discoverer.
- The background is explicitly pure white.
- The aspect ratio is present.
- The avoid list includes real logo, QR code, long text, clutter, bad anatomy, and malformed fingers.

## File Output

When the user asks for files, save prompts under a prompt-specific folder:

```text
prompts/
  01-cover.md
  02-flow.md
  03-comparison.md
```

For a single prompt, use `01-illustration-prompt.md` unless the user requests another filename. For an article, use stable numbered files matching the approved plan.

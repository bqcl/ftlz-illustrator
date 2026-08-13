# Typography

Use these rules whenever the prompt includes on-image Chinese text.

## Text Hierarchy

- Main title: large rounded bold black Chinese characters, optional white outer stroke plus subtle mint-green or sky-blue secondary outline.
- Section headings: black rounded bold characters inside white rounded rectangles or pill labels with colored outlines.
- Step labels: 2-5 Chinese characters when possible, placed below icons or inside pill labels.
- Speech bubbles: short phrases only, ideally under 8 Chinese characters.
- Arrow labels: 2-4 characters, placed near the arrow.

## Readability Rules

- List every required Chinese text string exactly in `NODES` or `TYPOGRAPHY`.
- Use short words rather than long sentences.
- Avoid body paragraphs, footnotes, dense annotations, tiny text, and decorative filler text.
- Prefer fewer text blocks when the image should survive small mobile preview.
- If the idea can be conveyed by icons, arrows, or expressions, reduce text.

## Default Typography Prompt

```text
中文文字采用圆润厚实的漫画字风格。主标题和重要标签使用粗黑圆字，可带白色外描边和浅绿色或浅蓝色辅助描边。步骤标签放在白底圆角胶囊框或圆形图标下方，黑色圆润粗字，必须短、准、清楚。不要出现小号密集文字。
```

## Avoid

- Thin formal fonts
- Songti-style serious document typography
- calligraphy or brush lettering unless requested
- neon cyberpunk typography unless requested
- long paragraphs
- tiny captions
- unclear or invented Chinese text

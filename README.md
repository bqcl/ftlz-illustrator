# ftlz-illustrator

`ftlz-illustrator` is a Codex skill for creating Chinese Markdown prompts for public-account article illustrations. The intended workflow is: upload or paste a Markdown article, let the skill analyze it and suggest several illustration ideas, confirm or revise the plan, then generate one `.md` prompt for each approved image.

It does not call image generation APIs. You copy each generated prompt into ChatGPT Image or another image tool together with your own uploaded character reference image.

## What It Does

- Analyzes `.md` articles before writing final prompts.
- Proposes an illustration plan and waits for confirmation.
- Generates structured Chinese image prompts in Markdown.
- Uses a consistent uploaded character reference workflow.
- Defaults to pure white backgrounds and 16:9 horizontal illustrations.
- Adds rounded comic-style Chinese typography rules.
- Supports covers, flows, comparisons, explainers, path/location visuals, and simple scenes.

## Privacy And Assets

This repository intentionally does not include any character artwork, sample private article drafts, personal account names, local machine paths, API keys, or generation history.

When using the skill, upload your own character reference image separately. The prompt will refer to it generically as "随同上传的角色参考图" so the workflow does not depend on a specific filename.

## Installation

Copy `skills/ftlz-illustrator` into your Codex skills directory, for example:

```text
~/.codex/skills/ftlz-illustrator
```

Then invoke it with:

```text
Use $ftlz-illustrator to analyze this Markdown article, suggest illustration ideas, and after I confirm, generate the Chinese .md prompts.
```

## License

MIT. See `LICENSE`.

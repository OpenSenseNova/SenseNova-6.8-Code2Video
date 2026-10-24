# Dense Prompt

[English](README.md) | [简体中文](README.zh-CN.md)

Use [the template](dense_prompt_template.md) with **Claude Opus 5.5** (recommended) or another strong model to turn a video request into a detailed production prompt. Replace `{{USER_INSTRUCTION}}` with the original request and `{{ASSETS_JSON}}` with the asset inventory (`[]` if empty). Send the populated template as one user message.

## Usage example

Run from the repository root to prepare the message:

```python
import json
from pathlib import Path

instruction = "Create a 15-second animation explaining how a rainbow forms."
assets = []  # Optional: [{"path": "assets/reference.mp4", "type": "video", "note": "Style reference"}]
template = Path("prompts/dense_prompt_template.md").read_text(encoding="utf-8")
message = template.replace("{{USER_INSTRUCTION}}", instruction).replace(
    "{{ASSETS_JSON}}", json.dumps(assets, ensure_ascii=False)
)
Path("request.md").write_text(message, encoding="utf-8")
```

Give `request.md` to the model and save its JSON reply as `response.json`, without Markdown code fences. Then extract the production prompt:

```python
result = json.loads(Path("response.json").read_text(encoding="utf-8"))
if result["is_video_request"]:
    Path("prompt_dense.md").write_text(result["dense_prompt"], encoding="utf-8")
```

Pass `prompt_dense.md` to Claude Code with the `code-video` skill. Asset paths must match files under the final task's `assets/` directory; this stage sends the inventory text, not the files. For non-video requests, the model returns `is_video_request: false` and `dense_prompt: null`.

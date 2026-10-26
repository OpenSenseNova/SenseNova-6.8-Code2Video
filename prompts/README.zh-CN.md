# Enhance prompt

[English](README.md) | [简体中文](README.zh-CN.md)

将[Enhance prompt 模板](enhance_prompt.md)交给 **Claude Opus 5.5**（推荐）或其他强模型，把视频需求扩写成详细制作 prompt。将 `{{USER_INSTRUCTION}}` 替换为原始需求，`{{ASSETS_JSON}}` 替换为素材清单（无素材填 `[]`），再将完整模板作为一条用户消息发送。

## 调用示例

在仓库根目录运行，生成待发送的消息：

```python
import json
from pathlib import Path

instruction = "制作一个 15 秒的动画，解释彩虹是如何形成的。"
assets = []  # 有素材时可填：[{"path": "assets/reference.mp4", "type": "video", "note": "风格参考"}]
template = Path("prompts/enhance_prompt.md").read_text(encoding="utf-8")
message = template.replace("{{USER_INSTRUCTION}}", instruction).replace(
    "{{ASSETS_JSON}}", json.dumps(assets, ensure_ascii=False)
)
Path("request.md").write_text(message, encoding="utf-8")
```

将 `request.md` 交给模型，把返回的 JSON 保存为 `response.json`，不包含 Markdown 代码块标记。再提取制作 prompt：

```python
result = json.loads(Path("response.json").read_text(encoding="utf-8"))
if result["is_video_request"]:
    Path("dense_prompt.md").write_text(result["dense_prompt"], encoding="utf-8")
```

将 `dense_prompt.md` 交给加载了 `code-video` skill 的 Claude Code。素材路径须对应最终任务的 `assets/` 目录；此阶段只发送素材清单文字，不发送文件本身。非视频请求返回 `is_video_request: false`、`dense_prompt: null`。

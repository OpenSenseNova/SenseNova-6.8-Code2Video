<div align="center">

<img src="media/launch/title.gif" width="100%" alt="SenseNova 6.8 Code2Video">

# SenseNova 6.8 Code2Video

**A first step toward code-driven video creation with small open models**

[![Hugging Face](https://img.shields.io/badge/Hugging_Face-Weights_%C2%B7_Trajectories-ffd21e?style=flat-square&logo=huggingface&logoColor=black)][hf] ![27B](https://img.shields.io/badge/Params-27B-db2777?style=flat-square) ![512K](https://img.shields.io/badge/Context-512K-0891b2?style=flat-square) [![Discord](https://img.shields.io/badge/Discord-OpenSenseNova-5865F2?style=flat-square&logo=discord&logoColor=white)][discord]

**English** · [简体中文](README.zh-CN.md)

<a href="media/launch/sensenova_codevideo_launch_film.mp4"><img src="media/launch/sensenova_codevideo_launch_film.gif" width="100%" alt="SenseNova 6.8 Code2Video launch film"></a>

**[▶ Watch the 90-second launch film](media/launch/sensenova_codevideo_launch_film.mp4)** &nbsp;·&nbsp; **[🤗 Hugging Face][hf]**

<sub>The launch film was made by SenseNova 6.8 Code2Video, and so was every video that appears in it. The full films are in <a href="media/showcase/"><code>media/showcase/</code></a>.</sub>

</div>

## Overview

We present SenseNova 6.8 Code2Video, a lightweight open model for code-driven video creation. The model builds and renders videos by generating executable code, and currently focuses on short videos implemented entirely in code. Preliminary results show good visual composition and motion choreography in motion design, suggesting the potential of lightweight models for programmatic video creation.

We chose code as the entry point to video creation partly for its ability to connect different models and creative tools. Beyond building and rendering visual content directly, code can call image generation, video generation, 3D modelling and video editing models and tools, chaining generation, editing and compositing into a complete creative workflow.

We believe code can become a common language between ideas and finished work. Our long-term goal is a model that coordinates different generative models and creative tools through code to create digital content across media. SenseNova 6.8 Code2Video is a first step in this direction. Next, we will scale the model further and extend these abilities to editing, compositing, animation and 3D content creation.

We release the following as a reference for researchers:

| Resource | Description | Location |
|---|---|---|
| 🤗 **Model weights** | SenseNova 6.8 Code2Video, fine-tuned from Qwen3.8-27B, 512K context | [Hugging Face][hf] · [Weights](#model-weights) |
| 📘 **Deployment** | Serving commands and recommended harness settings | [Deployment](#deployment) |
| 🧩 **Skill** | `code-video`: workflow, eight craft guides and rendering/checking tools | [`skills/code-video`](skills/code-video/SKILL.md) · [Skill](#skill) |
| ✍️ **Prompt enhancement** | Template that expands a short request into a production brief | [`prompts/`](prompts/README.md) · [Prompt enhancement](#prompt-enhancement) |
| 🎞️ **Trajectories** | Full production trajectories (messages, tool calls, rendered review images) | [Hugging Face](https://huggingface.co/sensenova/SenseNova-6.8-Code2Video) |

## Why a code model

### Limits of generative models

Generative models now produce convincing lighting, materials and motion, but they generate the whole clip in one black-box sampling process:

- **No grounding.** The model learns how the world looks from images, not how it works from equations, so motion can look plausible and still be physically wrong.
- **Hard to edit.** Size, timing and trajectory stay implicit. Changing one detail means re-prompting and resampling the whole clip, and the rest of the clip changes with it.
- **Inexact content.** On-screen text, formulas, charts and data values must be exactly right, yet are easily garbled.

### Advantages of code, and the outlook

- **Easy to modify.** Every element is a named object in the code. Resizing, retiming, rerouting or restyling one element takes a few lines, and everything else stays exactly as it was; see [Keep refining](#-keep-refining-after-the-first-cut) below.
- **Precise, controllable content.** Text is typeset verbatim, formulas and data come from the source, and coordinates, durations, beats and camera paths are explicit numbers that can be checked against the brief. Each frame is a pure function of `t`, so the same code always renders the same film.
- **Precise physical modelling.** Motion, collisions and light are computed from equations rather than guessed from appearance, so the physics on screen holds up. On top of this, textures, characters and backgrounds from generative models can be brought in and placed and timed by code, for richer and more polished pictures.
- **Lower cost, faster polished films.** A frame is drawn by a program on ordinary hardware, and an edit re-renders only what it touches, so rendering is far cheaper than sampling a video model. A production run still takes hours of agent time today; we aim to train the model to reach a polished film in fewer turns.
- **Beyond this release.** A code render can serve as a fast previs that fixes layout, motion and camera for a video model to render on top of, and because every quantity is known, the same programs can produce exactly labelled data (depth, camera poses, multi-view renders) for world models and 3D/4D reconstruction.

## 🎬 Showcase

<img src="media/launch/wall.gif" width="100%" alt="Nine films made by SenseNova 6.8 Code2Video">

<div align="center">

<a href="media/showcase/forest_landslide.mp4">Can a Forest Hide a Landslide?</a> · <a href="media/showcase/fourier_light_painting.mp4">Fourier Light Painting</a> · <a href="media/showcase/signal_noise_shape.mp4">Signal / Noise / Shape</a><br>
<a href="media/showcase/paper_and_ink_bookshop.mp4">Paper &amp; Ink</a> · <a href="media/showcase/clock_clock.mp4">Clock Clock</a> · <a href="media/showcase/golden_spiral_sunflower.mp4">Golden Spiral and Sunflower</a><br>
<a href="media/showcase/paper_sea.mp4">Paper Sea</a> · <a href="media/showcase/a_to_z.mp4">A to Z</a> · <a href="media/showcase/robot_night_lamp.mp4">Robot and the Night Lamp</a>

<sub>Click a title for the full film with sound.</sub>

</div>

### 🔁 Keep refining after the first cut

This is where code differs most from generative models. With a generative model, one change means re-prompting and resampling, and the parts you liked may change too. Here every note becomes a code edit, so the change is precise and everything else is untouched.

The first cut isn't the end. Once a film is delivered, SenseNova 6.8 Code2Video takes your notes (a new look, extra elements, different pacing), edits the code in the same project and renders again, so every round makes the film fuller and richer.

We asked it for a retro airport split-flap board, then turned it into a more designed piece with two rounds of notes:

<table>
<tr>
<td align="center" valign="top" width="33%"><a href="media/launch/departures_v1.mp4"><img src="media/launch/departures_v1.gif" width="100%" alt="First cut"></a><br><b>First cut</b><br><sub>A dark board under a spotlight</sub></td>
<td align="center" valign="top" width="33%"><a href="media/launch/departures_v2.mp4"><img src="media/launch/departures_v2.gif" width="100%" alt="Round 2"></a><br><b>Round 2</b><br><sub>Restyled as a bright pastel hotel lobby</sub></td>
<td align="center" valign="top" width="33%"><a href="media/launch/departures_v3.mp4"><img src="media/launch/departures_v3.gif" width="100%" alt="Round 3"></a><br><b>Round 3</b><br><sub>A plane overhead and travellers with luggage</sub></td>
</tr>
</table>

Each round takes one short note; the copy, timing and flip mechanics we didn't ask to change stay exactly as they were.

## Model weights

SenseNova 6.8 Code2Video is built on Qwen3.8-27B. It supports a 512K context, handles context compaction well and can sustain sessions of over a thousand turns. Download the weights from [Hugging Face][hf]:

```bash
huggingface-cli download sensenova/SenseNova-6.8-Code2Video --local-dir /path/to/SenseNova-6.8-Code2Video
```

## Deployment

### [LightLLM](https://github.com/ModelTC/LightLLM)

```bash
docker run --rm --gpus all --ipc=host -p 8000:8000 \
  -v /path/to/SenseNova-6.8-Code2Video:/model \
  ghcr.io/modeltc/lightllm:main \
  python -m lightllm.server.api_server \
    --model_dir /model \
    --tp 4 \
    --max_req_total_len 524288 \
    --host 0.0.0.0 --port 8000
```

### [vLLM](https://github.com/vllm-project/vllm)

```bash
docker run --rm --gpus all --ipc=host -p 8000:8000 \
  -e VLLM_ALLOW_LONG_MAX_MODEL_LEN=1 \
  -v /path/to/SenseNova-6.8-Code2Video:/model \
  vllm/vllm-openai:latest \
    --model /model \
    --tensor-parallel-size 4 \
    --max-model-len 524288 \
    --reasoning-parser qwen3 \
    --enable-auto-tool-choice \
    --tool-call-parser qwen3_coder \
    --host 0.0.0.0 --port 8000
```

### [SGLang](https://github.com/sgl-project/sglang)

```bash
docker run --rm --gpus all --ipc=host -p 8000:8000 \
  -e SGLANG_ALLOW_OVERWRITE_LONGER_CONTEXT_LEN=1 \
  -v /path/to/SenseNova-6.8-Code2Video:/model \
  lmsysorg/sglang:latest \
  python -m sglang.launch_server \
    --model-path /model \
    --tp-size 4 \
    --context-length 524288 \
    --reasoning-parser qwen3 \
    --tool-call-parser qwen3_coder \
    --host 0.0.0.0 --port 8000
```

### Recommended harness: Claude Code

A complete film is a long-horizon task: the model writes and renders code, reviews the frames and revises, turn after turn. SenseNova 6.8 Code2Video sustains runs of **more than 10 hours and more than 2,000 turns**. Configure Claude Code for runs of that length:

| Setting | Value | Configuration |
|---|---|---|
| Context window | 512K | `CLAUDE_CODE_MAX_CONTEXT_TOKENS=524288` |
| Auto-compaction | 0.8 | `CLAUDE_AUTOCOMPACT_PCT_OVERRIDE=80` |
| Max output | 64K | `CLAUDE_CODE_MAX_OUTPUT_TOKENS=65536` |
| Turns per run | 2,000+ | `--max-turns 2000` or more |
| Time per run | 10 h+ | `timeout 10h` or more |

Set the context window explicitly, since Claude Code otherwise treats an unknown model as a 200K model. With compaction at 0.8 and 64K of output, every request stays within the 512K server limit.

Put the endpoint and these variables in a private settings file, and supply the credential through `ANTHROPIC_AUTH_TOKEN` or `ANTHROPIC_API_KEY`:

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://your-endpoint.example.com",
    "ANTHROPIC_MODEL": "your-deployed-model-name",
    "CLAUDE_CODE_MAX_CONTEXT_TOKENS": "524288",
    "CLAUDE_AUTOCOMPACT_PCT_OVERRIDE": "80",
    "CLAUDE_CODE_MAX_OUTPUT_TOKENS": "65536"
  },
  "model": "your-deployed-model-name"
}
```

Avoid slow shell initialization: every Bash call starts a new shell.

## Skill

The [`code-video`](skills/code-video/SKILL.md) skill turns production into an explicit, checkable workflow: write a spec, render every frame as a function of time, review contact sheets as images, and verify the delivered file. The skill covers eight craft guides: explainers, stylized looks, simulations, characters, 3D scenes, motion graphics, sound and narration, and music sync. The skill is fixed: the same version is used for every task.

**Install the skill.** The `code-video` skill is in this repository under [`skills/code-video`](skills/code-video/). Copy it into `.claude/skills/code-video` inside your task folder (project-level installation). Set `TASK` to the absolute path of your task folder:

```bash
TASK=/absolute/path/to/a-new-video-task
git clone https://github.com/OpenSenseNova/SenseNova-6.8-Code2Video.git
mkdir -p "$TASK/.claude/skills"
cp -r SenseNova-6.8-Code2Video/skills/code-video "$TASK/.claude/skills/"
```

You can also give the address to your agent and let it install the skill, for example:

> *Please install [https://github.com/OpenSenseNova/SenseNova-6.8-Code2Video/tree/main/skills/code-video](https://github.com/OpenSenseNova/SenseNova-6.8-Code2Video/tree/main/skills/code-video) into `.claude/skills/code-video` in the current task folder.*

After installation, **you may need to manually restart the agent service** for the new skill to be loaded.

**Prepare the environment.** You need Claude Code, Node.js 18+, Python 3, ffmpeg/ffprobe and fonts for the video's language. Installing the environment on the first run can take a long time, so install the dependencies before starting production:

```bash
python3 -m pip install -r "$TASK/.claude/skills/code-video/requirements.txt"
cd "$TASK" && npm install playwright && npx playwright install chromium
```

**Start Claude Code.** Launch Claude Code in the task folder with your private settings file; see [Recommended harness](#recommended-harness-claude-code) for the endpoint and parameter settings:

```bash
cd "$TASK"
claude --settings /absolute/path/to/private-settings.json --model your-deployed-model-name
```

## Prompt enhancement

Build `request.md` from the [Enhance prompt template](prompts/enhance_prompt.md) as the [prompts guide](prompts/README.md) shows, send it to Claude Opus 5.5 or another strong model, and save the result as `dense_prompt.md` in the task root.

**Start production.** Once the settings and prompt are ready, run the following command, replacing the settings file path and model name with your actual values.

```bash
cd "$TASK"
claude --settings /absolute/path/to/private-settings.json --model your-deployed-sensenova-code2video-model \
  'Use the project code-video skill. Read .claude/skills/code-video/SKILL.md and dense_prompt.md, then the relevant craft guides. This directory is the project root. Produce the complete video, run the rendering tools and complete at least two visual review passes. Deliver out/final.mp4, SPEC.md, VERIFY.md, a contact sheet, source code and reproduction commands. Continue until the actual video passes verification; report any blockers honestly.'
```

**Watch and revise.** Say what to change in the same session (time point, what is wrong, what you want instead), or come back later with `--continue`; the model edits the same project and renders again.

## Limitations

- **Scope.** The model makes videos that can be written as code: motion graphics, explainers, stylized 2D and 3D scenes, procedural audio. It does not generate photorealistic footage.
- **Cost.** A production run takes hours and a long context. Results depend on the harness configuration (context size, compaction, output limit; see [Deployment](#deployment)).
- **Evaluation.** We report qualitative examples only. We have not yet built a systematic benchmark for code-driven video, and we consider one an important open problem.
- **Gap to frontier models.** The model is clearly behind the strongest proprietary models on visual polish and long-horizon reliability. Narrowing that gap with small open models is the purpose of this release.
- **Prompt enhancement.** The model can enhance prompts on its own, but only at a basic level. Enhancing the prompt with a strong model such as Claude further improves the aesthetic quality of the film.

## Contributors

<table>
<tr>
<td align="center" width="110"><a href="https://github.com/moolean"><img src="https://github.com/moolean.png?size=160" width="80" alt="moolean"><br><sub><b>Tiankuo Yao</b></sub></a></td>
<td align="center" width="110"><a href="https://github.com/syssysyssy"><img src="https://github.com/syssysyssy.png?size=160" width="80" alt="syssysyssy"><br><sub><b>syssysyssy</b></sub></a></td>
<td align="center" width="110"><a href="https://github.com/Mr-Tony921"><img src="https://github.com/Mr-Tony921.png?size=160" width="80" alt="Mr-Tony921"><br><sub><b>Mr.Tony</b></sub></a></td>
<td align="center" width="110"><a href="https://github.com/penghao-wu"><img src="https://github.com/penghao-wu.png?size=160" width="80" alt="penghao-wu"><br><sub><b>Penghao Wu</b></sub></a></td>
<td align="center" width="110"><a href="https://github.com/dder4a42"><img src="https://github.com/dder4a42.png?size=160" width="80" alt="dder4a42"><br><sub><b>Dder</b></sub></a></td>
<td align="center" width="110"><a href="https://github.com/M1M1cooL"><img src="https://github.com/M1M1cooL.png?size=160" width="80" alt="M1M1cooL"><br><sub><b>Ming</b></sub></a></td>
<td align="center" width="110"><a href="https://github.com/shiyigueris-cmyk"><img src="https://github.com/shiyigueris-cmyk.png?size=160" width="80" alt="shiyigueris-cmyk"><br><sub><b>shiyigueris-cmyk</b></sub></a></td>
<td align="center" width="110"><a href="https://github.com/ottolu"><img src="https://github.com/ottolu.png?size=160" width="80" alt="ottolu"><br><sub><b>Lewei Lu</b></sub></a></td>
</tr>
</table>

[hf]: https://huggingface.co/sensenova/SenseNova-6.8-Code2Video
[discord]: https://discord.com/channels/1488006693395628032/1488015977932390520

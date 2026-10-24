<div align="center">

<img src="media/readme/title.gif" width="100%" alt="SenseNova 6.8 Code2Video · Every frame is code. · 把脑洞，码成片">

# Every frame is code

<img src="media/readme/typing_en.svg" width="90%" alt="One model for math explainers / paper-craft films / isometric worlds / kinetic type / data stories / character animation / product promos">

[![Hugging Face](https://img.shields.io/badge/Hugging_Face-Weights_%C2%B7_Trajectories-ffd21e?style=flat-square&logo=huggingface&logoColor=black)][hf] ![27B](https://img.shields.io/badge/Params-27B-db2777?style=flat-square) ![512K](https://img.shields.io/badge/Context-512K-0891b2?style=flat-square) ![Claude Code](https://img.shields.io/badge/Runs_in-Claude_Code-d97757?style=flat-square&logo=anthropic&logoColor=white)

**English** · [简体中文](README.zh-CN.md)

</div>

## 📦 Everything is open

| What | Description | Where |
|---|---|---|
| 🤗 **Model weights** | SenseNova 6.8 Code2Video weights | [Hugging Face][hf] |
| 🎞️ **Trajectories and prompts** | Full production trajectories and prompts for every film | [Hugging Face](https://huggingface.co/sysssyssy/sensenova-codevideo/tree/main/trajectories) |
| 📘 **Deployment guide** | Deployment parameters and instructions | [Hugging Face][hf] |
| 🧩 **Skill** | The fixed code-video production skill: workflow, craft guides and rendering tools | [`skills/code-video`](skills/code-video/SKILL.md) |
| ✍️ **Prompt template** | Turns a one-line idea into a full production brief | [`prompts/`](prompts/README.md) |

<div align="center">

<a href="media/launch/sensenova_codevideo_launch_film.mp4"><img src="media/launch/sensenova_codevideo_launch_film.gif" width="100%" alt="SenseNova 6.8 Code2Video launch film"></a>

**[▶ Watch the 90-second launch film](media/launch/sensenova_codevideo_launch_film.mp4)** &nbsp;·&nbsp; **[🤗 Hugging Face][hf]**

<sub>The launch film was made by SenseNova 6.8 Code2Video, and so was every video that appears in it.</sub>

</div>

<br>

> **Today we are officially launching SenseNova 6.8 Code2Video, the industry's first open-source code-driven video creation model.**
>
> We believe code can become a universal language that connects creative ideas with finished work. SenseNova 6.8 Code2Video is our first step toward general creative intelligence: starting from short films rendered purely from code, it will progressively extend to editing, compositing, animation and broader digital content creation.
>
> We are opening the model weights and the Skill, all of it. Every video in this README was made by SenseNova 6.8 Code2Video in a single run from one prompt plus the skill, and we are open-sourcing the production trajectories and prompts for every film.

## ✨ Why SenseNova 6.8 Code2Video

### 🧑‍💻 No cameras, only code

No cameras, no stock footage. Text, equations, shapes, motion and sound are all written as code, the same moment always renders the same frame, and after the first cut you can change exactly the part you want.

<a href="media/launch/sensenova_codevideo_launch_film.mp4"><img src="media/readme/feature_code.gif" width="100%" alt="The code is written and the picture grows with it"></a>

### 🎨 One model, any style

Math explainers, paper craft, isometric illustration, kinetic type, data visualization, character animation, product promos… change the brief and you change the visual language.

<a href="media/launch/sensenova_codevideo_launch_film.mp4"><img src="media/readme/feature_style.gif" width="100%" alt="One model. Any style."></a>

### 🔁 Keep refining after the first cut

The first cut isn't the end. Once a film is delivered, SenseNova 6.8 Code2Video takes your notes (a new look, extra elements, different pacing), edits the code in the same project and renders again, so every round makes the film fuller and richer.

We asked it for a retro airport split-flap board, then turned it into a more designed piece with two rounds of notes:

<table>
<tr>
<td align="center" valign="top" width="33%"><a href="media/revision/departures_v1.mp4"><img src="media/revision/departures_v1.gif" width="100%" alt="First cut"></a><br><b>First cut</b><br><sub>A dark board under a spotlight</sub></td>
<td align="center" valign="top" width="33%"><a href="media/revision/departures_v2.mp4"><img src="media/revision/departures_v2.gif" width="100%" alt="Round 2"></a><br><b>Round 2</b><br><sub>Restyled as a bright pastel hotel lobby</sub></td>
<td align="center" valign="top" width="33%"><a href="media/revision/departures_v3.mp4"><img src="media/revision/departures_v3.gif" width="100%" alt="Round 3"></a><br><b>Round 3</b><br><sub>A plane overhead and travellers with luggage</sub></td>
</tr>
</table>

Each round takes one short note; the copy, timing and flip mechanics we didn't ask to change stay exactly as they were.

## 🎬 Showcase

<img src="media/readme/wall.gif" width="100%" alt="Nine showcase films playing at once">

<div align="center">

▶ [Fourier Light Painting](media/showcase/fourier_light_painting.mp4) · [Paper Sea](media/showcase/paper_sea.mp4) · [Paper & Ink](media/showcase/paper_and_ink_bookshop.mp4)<br>
[Signal / Noise / Shape](media/showcase/signal_noise_shape.mp4) · [CMYK Halftone](media/showcase/v1_fx09_cmyk_halftone.mp4) · [Can a Forest Hide a Landslide?](media/showcase/dpo_forest_landslide.mp4)<br>
[FRAME / FORM / FLOW](media/showcase/v1_frame_form_flow.mp4) · [Geometry / Risograph](media/showcase/v1_geometry_risograph.mp4) · [A to Z](media/showcase/a_to_z.mp4)

<sub>All nine films were made by SenseNova 6.8 Code2Video. Click a title to watch the full film with sound.</sub>

</div>

## 🚀 Quick start

<table>
<tr>
<td align="center" valign="top" width="33%"><h3>1️⃣ Write the brief</h3>Expand a one-line idea into a full production brief with Claude Opus 5.5 or another strong model and the prompt template</td>
<td align="center" valign="top" width="33%"><h3>2️⃣ Hand it to Claude Code</h3>Connect SenseNova 6.8 Code2Video to Claude Code with the fixed code-video skill and get the finished film in one run</td>
<td align="center" valign="top" width="33%"><h3>3️⃣ Watch, then refine</h3>Say what to change after watching; the model edits the code in the same project and renders again</td>
</tr>
</table>

<details>
<summary><b>Show the full steps and commands</b></summary>

<br>

**Prepare a task folder.** You need Claude Code, Node.js 18+, Python 3, ffmpeg/ffprobe and fonts for the video's language. The skill is fixed; copy it as it is.

```bash
git clone https://github.com/syssysyssy/sensenova-codevideo.git
TASK=/absolute/path/to/a-new-video-task
mkdir -p "$TASK/.claude/skills" "$TASK/assets"
cp -a sensenova-codevideo/skills/code-video "$TASK/.claude/skills/code-video"
python3 -m pip install -r "$TASK/.claude/skills/code-video/requirements.txt"
cd "$TASK" && npm install playwright && npx playwright install chromium
```

**Enhance the prompt.** Build `request.md` from the template as the [prompts guide](prompts/README.md) shows, send it to Claude Opus 5.5 or another strong model, and save the result as `prompt_dense.md` in the task root. For example:

```bash
claude -p --model claude-opus-5-5 "$(cat request.md)" > response.json
```

**Connect to Claude Code.** Point a private settings file at your deployed model (an Anthropic Messages-compatible endpoint, `max model length = 512k`; deployment guide on [Hugging Face][hf]) and supply the credential through `ANTHROPIC_AUTH_TOKEN` or `ANTHROPIC_API_KEY`.

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://your-model-endpoint.example.com",
    "ANTHROPIC_MODEL": "your-deployed-sensenova-code2video-model"
  },
  "model": "your-deployed-sensenova-code2video-model"
}
```

```bash
cd "$TASK"
claude --settings /absolute/path/to/private-settings.json --model your-deployed-sensenova-code2video-model \
  'Use the project code-video skill. Read .claude/skills/code-video/SKILL.md and prompt_dense.md, then the relevant craft guides. This directory is the project root. Produce the complete video, run the rendering tools and complete at least two visual review passes. Deliver out/final.mp4, SPEC.md, VERIFY.md, a contact sheet, source code and reproduction commands. Continue until the actual video passes verification; report any blockers honestly.'
```

**Watch and revise.** Say what to change in the same session (time point, what is wrong, what you want instead), or come back later with `--continue`; the model edits the same project and renders again.

</details>

<br>

<img src="media/readme/wave.svg" width="100%" alt="SenseNova 6.8 Code2Video · Every frame is code · 把脑洞，码成片">

[hf]: https://huggingface.co/sysssyssy/sensenova-codevideo

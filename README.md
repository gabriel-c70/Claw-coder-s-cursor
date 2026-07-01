<div align="center">

<img src="gemnew.png" alt="TipTour cursor actions" width="900" />

# TipTour
## The opensource AI cursor that we will put into claw-coder but with foundational work.

**This and That**

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](./LICENSE)
[![Platform: macOS 14+](https://img.shields.io/badge/Platform-macOS%2014+-black)](https://www.apple.com/macos)

</div>

TipTour is a macOS menu bar companion that understands your screen, listens to your voice, and controls your computer for you.

Hold the hotkey, say what you want, and TipTour can point, click, type, open apps, edit selected text, or act on a freeform highlighted area.

## What You Can Say

- "Open Apple Notes and write a short essay"

Then you can do a freeform highlight by holding Control+Shift and moving your mouse and say
- "Change this word."

- "Move this over there."
- "Click the Blank document."
- "Make this line sound softer."
- "Guide me through exporting this."

TipTour sees the app/window you are working in, understands the highlighted or hovered area, and keeps actions inside that context.

## How It Works

TipTour combines:

- **Gemini Live** for realtime voice, screen understanding, transcription, and tool calling.
- **CUA Driver Core** for reliable computer control: clicks, typing, hotkeys, app launch, URLs, scrolling, and browser coordinates.
- **macOS Accessibility** for native app structure and exact text/element targeting.
- **Focus Highlight** for "this part" commands: hold the highlight hotkey, paint over an area, then ask TipTour to edit or act on it.

The app runs from the macOS menu bar. No dock icon, no main window.

## Controls

- **Ctrl + Option**: toggle voice mode.
- **Ctrl + Shift + drag**: paint a freeform focus highlight.
- **Menu bar icon**: open settings, permissions, and mode toggles.

## Modes

- **Autopilot**: TipTour performs actions for you. On by default.
- **Tour Guide**: TipTour teaches step by step. Off by default.
- **Neko Mode**: optional playful cursor mode. Off by default.

## Privacy

TipTour needs macOS permissions to work:

| Permission | Used For |
|---|---|
| Microphone | Voice input |
| Screen Recording | Visual context for Gemini |
| Accessibility | Reading UI structure and controlling apps |
| Screen Content | ScreenCaptureKit capture |

Source builds require your own Gemini API key. Paste it into the visible “Gemini API key” field in the menu bar panel; TipTour stores it in macOS Keychain.

## Build From Source

Requirements:

- macOS 14+
- Xcode 16+
- Node 20+ only if working on the Cloudflare Worker

Open the project:

```bash
open tiptour-macos.xcodeproj
```

Then in Xcode:

1. Select the `TipTour` scheme.
2. Set your signing team.
3. Press `Cmd+R`.
4. Paste your Gemini API key into the panel.
5. Grant the requested macOS permissions.

Do not build with terminal `xcodebuild` if you are actively testing permissions, because it can invalidate local TCC permission state.

## Worker

The Worker is optional for distribution builds. Source builds do not use the maintainer's Worker URL. To ship your own Worker-backed build, deploy the Worker and set `TipTourWorkerBaseURL` in the app bundle/build settings.

```bash
cd worker
npm install
npx wrangler secret put GEMINI_API_KEY
npx wrangler deploy
```

## Project Notes

For the deeper technical map, coding conventions, and agent instructions, see [AGENTS.md](AGENTS.md).

## Credits

- [CUA](https://github.com/trycua/cua) for computer-use primitives.
- [Gemini Live](https://ai.google.dev/gemini-api/docs/live-api) for realtime voice, vision, and tool calling.
- [oneko](https://github.com/crgimenes/neko) for optional pixel cat sprites.

## License

[MIT](LICENSE)


---

# Claw Coder
## Caution: This is the agent prototype that i built when solo but we are going to aggresively modify it because some or i can say most parts where AI generated so it will obviously break in production.
![claw-coder logo](logo3.png)

### Claw coder is a local first AI agent that turns local coding small LLMs into powerful AI agents that actually work here is how:
#### Claw coder has access to knowledge graph which means it can ingest files and directories and actually map them and understand what each part does to the other without even needing powerful GPUs and the knowledge graph is lightweight which means it runs completely on you laptop

![claw chat displayed](screenshoot1.png)

> - Claw coder has access to tree-sitter + RAG which is put in place just for the coding purpose only but the RAG is designed for both functionalities like for code and documents which means the local model can actually map relationships precisely with the help of knowledge graphs which is a powerful combination
> 
> 
> - Claw coder also has access to tools the elevate its power with real codebases:
## Tools include:

---
- Docker coder execution: Giving an AI agent docker code execution does not only improve coding performance and reasoning but also enables it to execute broken and working code all in isolated environment without destroying your venv.
---
- Search tools: Local AI and all of LLMs in general can't reason beyond their trained data which can lead to hallucinations but when given access to a search tool the hallucinations drop dramatically by up to 70%+ because it now has up_to_date information.
---
- Run tests: LLMs in general not only the local ones can write 1000s of lines of code that do not make sense from even the top to the last line but when given a test tool they can test their code and see where they went wrong and claw-coder is actually good with this coz it can even test html and css code and actually see the output on the web.
---
  - git tools: Not considering git for AI agents can look like something easy to slide and leave on the side because it looks useless but giving git to AI agents is not a luxury necessity but it enables the AI agent to check what changed and where and why and actually be a full AI engineer on your laptop on your lap completely local.
---
  - file tools: These are actually the tools that make an agent code in a real file and clear mistakes and these tools really help the agent just do its work outside the terminal.
---
### These are powerful tools but isn't it better to just use existing agents and configure them?:
### Well this is a good question but the is something to point out:

---

````
|______________________________________________________________________________________________________________________________________________________|
|__________|Runs locally|Repository understanding|Gives performance without compromaising security and privacy  |Code reasoning locally                |
|Cursor    |No          |Yes                     |No                                                            |No                                    |
|Codex     |No          |Yes                     |No                                                            |No                                    |
|Claw-coder|Yes         |Yes                     |Yes                                                           |Yes                                   | 
|Claude    |No          |Yes                     |No                                                            |No                                    |
|__________|____________|________________________|______________________________________________________________|______________________________________|
````
- ### Caution: Claw-Coder is indeed something else, but it is not perfect it can make mistakes and mess up don't be too open to claw-coder with your environment.
- ### But this has been thought of at file stage the AI has a directory called workspace where it works from without destroying your file structure.

---

### Now time to install and have fun with claw-coder.

---
## Install

---

From this directory:

```bash
npm install -g .
claw setup
```
---
For development, use a symlink instead:

```bash
npm link                                                                                              
claw setup
```
---
- `claw setup` installs the Python dependencies from 
  - `requirements.txt`. You also
need Ollama running for chat, embeddings, and vector RAG:
---
```bash
ollama serve
claw <model>
claw <chat model> <embedding modal>
```
---
## Use

```bash
claw doctor
claw languages
claw ingest .
claw graph "tree_sitter imports" 
claw search "where is graph reranking implemented?" --top-k 5
claw chat
```
- This is a screenshot of claw --help with all the commands displayed

![claw --help displayed](screenshoot3.png)

---
Useful options:

```bash
claw ingest ./src --no-vector-rag
claw search "authentication flow" --graph ./my_graph.json --db ./rag_db
claw graph "calls run_terminal" --top-k 10 --depth 3
```

### This is a credit based product so the powerful tools like docker execution and so much more while be credit based.

- To check your usage you run
```bash
claw usage
````

![claw usage displayed](screenshoot2.png)

---
You can also use the longer binary name:

```bash
claw-coder doctor
```
---
Sign in and log in:
```bash
claw login
```
---
> Source Code: [claw-coder](https://github.com/gabriel-c70/Claw-Coder.git) 
>
> You can also contribute and make [claw-coder](https://github.com/gabriel-c70/Claw-Coder.git) the best AI agent ever created by just contributing a line of code.
---

# Caution: we are going to need a mac with macos 15+ because i have macos 12 and can't update my mac coz its too old so renting a monthly mac will work
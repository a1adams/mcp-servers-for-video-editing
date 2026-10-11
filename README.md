# MCP server for video editing: which editors Claude can drive, with transport, edition and operations per server

As of 6 Oct 2026, MCP servers for video editing come in two kinds: community servers that drive a desktop editor you have open (DaVinci Resolve, Premiere Pro, After Effects, CapCut drafts) or FFmpeg on your own machine over stdio, and hosted connectors from Descript, Adobe and Wireflow that edit in the cloud over HTTP. Blackmagic limits external scripting to DaVinci Resolve Studio, so the two Resolve servers here reach the free edition only through a bridge script that runs inside Resolve. For cut, captions and export in one server, the docs reviewed show all three in Descript, Wireflow, ffmpeg-mcp-lite and three of the desktop servers.

1. **[Wireflow](https://www.wireflow.ai/blog/best-mcp-server-for-video-editing-tools-in-2026)**
2. **[Descript MCP](https://help.descript.com/api-and-mcp/mcp)**
3. **[Adobe for creativity](https://developer.adobe.com/adobe-for-creativity/)**
4. **[DaVinci Resolve MCP (samuelgursky)](https://github.com/samuelgursky/davinci-resolve-mcp)**
5. **[DaVinci Resolve MCP Bridge (hiteshK03)](https://github.com/hiteshK03/davinci-resolve-mcp)**
6. **[Premiere Pro MCP Bridge (hetpatel-11)](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP)**
7. **[After Effects MCP Server (Dakkshin)](https://github.com/Dakkshin/after-effects-mcp)**
8. **[VectCutAPI](https://github.com/sun-guannan/VectCutAPI)**
9. **[ffmpeg-mcp-lite](https://github.com/kevinwatt/ffmpeg-mcp-lite)**

The tables below are generated from [`data/tools.json`](data/tools.json). Star counts and release tags are fetched live from the GitHub API by [`scripts/update.js`](scripts/update.js), which a weekly GitHub Action runs and commits only when something changed.

<!-- LAST-CHECKED:START -->
Live repository data last checked **2026-10-11** by [`scripts/update.js`](scripts/update.js), which runs weekly via GitHub Actions.
<!-- LAST-CHECKED:END -->

Maintained by [a1adams](https://github.com/a1adams). Corrections are welcome, see [CONTRIBUTING.md](CONTRIBUTING.md).

## Contents

- [The data](#the-data)
- [Capability scores](#capability-scores)
- [The tools](#the-tools)
  - [Wireflow](#1-wireflow)
  - [Descript MCP](#2-descript-mcp)
  - [Adobe for creativity](#3-adobe-for-creativity)
  - [DaVinci Resolve MCP (samuelgursky)](#4-davinci-resolve-mcp-samuelgursky)
  - [DaVinci Resolve MCP Bridge (hiteshK03)](#5-davinci-resolve-mcp-bridge-hiteshk03)
  - [Premiere Pro MCP Bridge (hetpatel-11)](#6-premiere-pro-mcp-bridge-hetpatel-11)
  - [After Effects MCP Server (Dakkshin)](#7-after-effects-mcp-server-dakkshin)
  - [VectCutAPI](#8-vectcutapi)
  - [ffmpeg-mcp-lite](#9-ffmpeg-mcp-lite)
- [Decision this list supports](#decision-this-list-supports)
- [Scope and evidence](#scope-and-evidence)
- [What each column means](#what-each-column-means)
- [Evidence by cell](#evidence-by-cell)
- [Selection notes](#selection-notes)
- [Acceptance recipe](#acceptance-recipe)
- [Evaluation record](#evaluation-record)
- [Related datasets](#related-datasets)
- [How this list is maintained](#how-this-list-is-maintained)
- [Contributing](#contributing)
- [License](#license)

## The data

One row per tool, one column per thing people actually check before committing. Columns with nothing verified behind them are dropped rather than filled with guesses.

<!-- DATA-TABLE:START -->
| Tool | Claude connection | Free tier | Pricing | Open-source SDK / MCP |
|---|---|---|---|---|
| **[Wireflow](#1-wireflow)** | Streamable HTTP, OAuth 2.1 with PKCE | [check](https://www.wireflow.ai/pricing) | [pricing](https://www.wireflow.ai/pricing) | n/a |
| **[Descript MCP](#2-descript-mcp)** | Remote HTTP, OAuth with a Descript sign-in | [check](https://www.descript.com/pricing) | [pricing](https://www.descript.com/pricing) | [descriptinc/descript-mcp](https://github.com/descriptinc/descript-mcp), 33 ★, pushed 2026-10-01 |
| **[Adobe for creativity](#3-adobe-for-creativity)** | Connector from Claude's directory; transport not named | n/a | n/a | n/a |
| **[DaVinci Resolve MCP (samuelgursky)](#4-davinci-resolve-mcp-samuelgursky)** | Local stdio; opt-in loopback HTTP | n/a | n/a | [samuelgursky/davinci-resolve-mcp](https://github.com/samuelgursky/davinci-resolve-mcp), 3,460 ★, v4.10.4 |
| **[DaVinci Resolve MCP Bridge (hiteshK03)](#5-davinci-resolve-mcp-bridge-hiteshk03)** | Local stdio, bridge script inside Resolve | n/a | n/a | [hiteshK03/davinci-resolve-mcp](https://github.com/hiteshK03/davinci-resolve-mcp), 125 ★, pushed 2026-03-28 |
| **[Premiere Pro MCP Bridge (hetpatel-11)](#6-premiere-pro-mcp-bridge-hetpatel-11)** | Local stdio, CEP panel bridge | n/a | n/a | [hetpatel-11/Adobe_Premiere_Pro_MCP](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP), 673 ★, v1.2.8 |
| **[After Effects MCP Server (Dakkshin)](#7-after-effects-mcp-server-dakkshin)** | Local stdio, bridge panel in After Effects | n/a | n/a | [Dakkshin/after-effects-mcp](https://github.com/Dakkshin/after-effects-mcp), 724 ★, pushed 2026-04-01 |
| **[VectCutAPI](#8-vectcutapi)** | Local stdio | n/a | n/a | [sun-guannan/VectCutAPI](https://github.com/sun-guannan/VectCutAPI), 2,291 ★, v1.5.0 |
| **[ffmpeg-mcp-lite](#9-ffmpeg-mcp-lite)** | Local stdio via uvx | n/a | n/a | [kevinwatt/ffmpeg-mcp-lite](https://github.com/kevinwatt/ffmpeg-mcp-lite), 27 ★, v0.2.0 |
<!-- DATA-TABLE:END -->

## Capability scores

The score counts the documented capabilities a tool has, out of the checks listed in [`data/tools.json`](data/tools.json) under `capabilityChecks`. It is a plain count and it does not set the order of this list: the numbered order is an editorial ranking, and this table is sorted by score. The checks and every answer are in the file, so each cell can be checked. Disagree with a cell? Open an issue naming the tool, the check and the evidence.

<!-- CAPABILITY-SCORES:START -->
| Tool | Runs without a desktop editor | Timeline edits | Captions or subtitles | Render or export | First-party server | Open-source server code | Score |
|------|---|---|---|---|---|---|-------|
| **[Wireflow](#1-wireflow)** | ✅ | ✅ | ✅ | ✅ | ✅ | n/a | **5/6** |
| **[Descript MCP](#2-descript-mcp)** | ✅ | ✅ | ✅ | ✅ | ✅ | n/a | **5/6** |
| **[ffmpeg-mcp-lite](#9-ffmpeg-mcp-lite)** | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ | **5/6** |
| **[Adobe for creativity](#3-adobe-for-creativity)** | ✅ | ✅ | n/a | ✅ | ✅ | n/a | **4/6** |
| **[DaVinci Resolve MCP (samuelgursky)](#4-davinci-resolve-mcp-samuelgursky)** | ❌ | ✅ | ✅ | ✅ | ❌ | ✅ | **4/6** |
| **[DaVinci Resolve MCP Bridge (hiteshK03)](#5-davinci-resolve-mcp-bridge-hiteshk03)** | ❌ | ✅ | ✅ | ✅ | ❌ | ✅ | **4/6** |
| **[Premiere Pro MCP Bridge (hetpatel-11)](#6-premiere-pro-mcp-bridge-hetpatel-11)** | ❌ | ✅ | ✅ | ✅ | ❌ | ✅ | **4/6** |
| **[VectCutAPI](#8-vectcutapi)** | ❌ | ✅ | ✅ | ❌ | ❌ | ✅ | **3/6** |
| **[After Effects MCP Server (Dakkshin)](#7-after-effects-mcp-server-dakkshin)** | ❌ | ✅ | n/a | n/a | ❌ | ✅ | **2/6** |
<!-- CAPABILITY-SCORES:END -->

## The tools

### 1. Wireflow

*hosted MCP; edits the Video Editor node inside a Wireflow workflow*

![Wireflow screenshot](https://assets.wireflow.ai/competitors/wireflow-70f47ccd9660.png?v=r5)

- **What it is:** Wireflow's hosted MCP connector for its node canvas. An agent reads a video node's cut with get_video_timeline, replaces it with edit_video_timeline, previews still frames without rendering, and renders by running the workflow.
- **Limits:** It does not drive a desktop editor. It edits only inside a Wireflow workflow whose video goes through the Video Editor node, and only run_workflow spends credits. Cutting a word out mid-line has no node yet, and custom scene Blocks are not open to outside agents.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://www.wireflow.ai)
  - [Wireflow best MCP server for video editing tools in 2026 page](https://www.wireflow.ai/blog/best-mcp-server-for-video-editing-tools-in-2026)
  - [Docs](https://www.wireflow.ai/docs/mcp)
  - [Pricing](https://www.wireflow.ai/pricing)

Streamable HTTP endpoint from the official connector docs. Add it as a custom connector, then approve the OAuth consent screen:
```text
https://www.wireflow.ai/api/mcp
```

### 2. Descript MCP

*hosted; edits projects in one Descript Drive by prompt*

![Descript MCP screenshot](https://assets.wireflow.ai/competitors/descript-mcp-2752e088be1a.png?v=r5)

- **What it is:** Descript's official MCP server at api.descript.com/v2/mcp, listed in Claude's connector directory. Agents import media, edit with Descript's Underlord co-editor in plain language (trim, add captions, remove filler words), publish a composition and export transcripts or a Premiere Pro or DaVinci Resolve timeline.
- **Limits:** A connection is scoped to one Drive. A finished file cannot be downloaded without publishing to a Descript web link, and imports and AI edits use media minutes and AI credits.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://www.descript.com)
  - [Docs](https://help.descript.com/api-and-mcp/mcp)
  - [Pricing](https://www.descript.com/pricing)
  - [descriptinc/descript-mcp](https://github.com/descriptinc/descript-mcp)

Claude Code command copied from the descript-mcp README (server only, without the bundled skills):
```bash
claude mcp add --transport http descript https://api.descript.com/v2/mcp
```

### 3. Adobe for creativity

*hosted Claude connector; no Adobe app needed*

![Adobe for creativity screenshot](https://assets.wireflow.ai/competitors/adobe-for-creativity-126d028e2044.png?v=r5)

- **What it is:** Adobe's connector for Claude, with 50+ tools across Photoshop, Lightroom, Illustrator, Firefly, Premiere, Express, InDesign and Adobe Stock. Its video workflows resize a clip for a platform and Quick Cut a long video into short highlight clips.
- **Limits:** The video workflows need an Adobe ID; guest mode has about 40 standard tools. The docs describe outcome-level workflows, not track or clip-level timeline tools, and they do not name the transport.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://developer.adobe.com/adobe-for-creativity/)
  - [Docs](https://developer.adobe.com/adobe-for-creativity/getting-started/)
  - [Official source 2](https://developer.adobe.com/adobe-for-creativity/prompts-and-workflows/)
  - [Official source 3](https://developer.adobe.com/adobe-for-creativity/support/)

**Getting started:** no public CLI or SDK to install, so start from the [docs](https://developer.adobe.com/adobe-for-creativity/getting-started/).

### 4. DaVinci Resolve MCP (samuelgursky)

*Resolve 18.5+ Studio, free edition via in-app bridge; stdio; MIT*

![DaVinci Resolve MCP (samuelgursky) screenshot](https://assets.wireflow.ai/competitors/davinci-resolve-mcp-6daf116a3e15.png?v=r5)

- **What it is:** A community server that drives DaVinci Resolve through the official scripting API, with timeline editing, subtitles from audio, render queue and Quick Export tools. It installs with one npx command and configures most MCP clients.
- **Limits:** Blackmagic limits external scripting to Studio. The free edition works only through an in-app bridge script, which the README treats as a path for Resolve 21.0.x because Resolve 21.1 moved Python scripting to Studio.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://github.com/samuelgursky/davinci-resolve-mcp)
  - [Official source 2](https://github.com/samuelgursky/davinci-resolve-mcp/blob/main/docs/reference/api-coverage.md)

Setup command copied from the README. Open DaVinci Resolve Studio first and set External scripting to Local:
```bash
npx davinci-resolve-mcp setup
```

### 5. DaVinci Resolve MCP Bridge (hiteshK03)

*Resolve 18+ free or Studio via in-app bridge; stdio; MIT*

![DaVinci Resolve MCP Bridge (hiteshK03) screenshot](https://assets.wireflow.ai/competitors/davinci-resolve-mcp-bridge-4fa90685311a.png?v=r5)

- **What it is:** A community server built around a bridge script that runs inside Resolve from the Scripts menu, so it works on the free edition. Its 162 tools cover timelines, rendering and tracks, plus local transcription with word-level timestamps.
- **Limits:** You copy the bridge script into Resolve and start it from Workspace, Scripts each session. The repository was last pushed in March 2026, before the Resolve 21.1 change to Python scripting that the samuelgursky README reports.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://github.com/hiteshK03/davinci-resolve-mcp)

Server setup copied from the README (step 2). Copy src/CursorBridge.py into Resolve's scripts folder first:
```bash
git clone https://github.com/hiteshK03/davinci-resolve-mcp.git
cd davinci-resolve-mcp
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 6. Premiere Pro MCP Bridge (hetpatel-11)

*Premiere Pro 2020+ via a CEP panel; stdio; MIT*

![Premiere Pro MCP Bridge (hetpatel-11) screenshot](https://assets.wireflow.ai/competitors/premiere-pro-mcp-bridge-aa6394f95609.png?v=r5)

- **What it is:** A community server with 283 Premiere tools behind search_tools and invoke_tool, covering razor, trim, ripple delete, caption tracks from an SRT, and export through Adobe Media Encoder.
- **Limits:** Premiere Pro, the MCP client and the package must run on the same computer, with the CEP bridge panel open. The UXP plugin is an experimental preview, and anonymous usage telemetry is on unless you opt out.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP)

Install commands copied from the README, run on the same computer as Premiere Pro:
```bash
npm install -g adobe-premiere-pro-mcp
premiere-pro-mcp --install-cep
premiere-pro-mcp --doctor
```

### 7. After Effects MCP Server (Dakkshin)

*After Effects 2022 or later; stdio; MIT*

![After Effects MCP Server (Dakkshin) screenshot](https://assets.wireflow.ai/competitors/after-effects-mcp-server-6e5f0363b4f3.png?v=r5)

- **What it is:** A community server that controls After Effects compositions and layers: create compositions, text and shape layers, set keyframes and expressions, and change layer properties including timing.
- **Limits:** The listed tools work on compositions and layers. They do not include a render, export or caption tool, and the bridge panel has to stay open in After Effects.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://github.com/Dakkshin/after-effects-mcp)

Install steps copied from the README:
```bash
git clone https://github.com/Dakkshin/after-effects-mcp.git
cd after-effects-mcp
npm install
npm run build
npm run install-bridge
```

### 8. VectCutAPI

*CapCut International or Jianying drafts; stdio; Apache-2.0*

![VectCutAPI screenshot](https://assets.wireflow.ai/competitors/vectcutapi-be4e66cee549.png?v=r5)

- **What it is:** A community editing API with an MCP server of 11 tools that builds CapCut or Jianying draft projects: add video with start and end points, audio, text, SRT subtitles, effects and keyframes, then save the draft.
- **Limits:** The MCP tools save a draft rather than render it. The README says final videos render in the vendor's cloud through the API, or you open the draft in CapCut or Jianying.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://github.com/sun-guannan/VectCutAPI)
  - [Docs](https://github.com/sun-guannan/VectCutAPI/blob/main/MCP_Documentation_English.md)

Install and start commands copied from the README:
```bash
git clone https://github.com/sun-guannan/VectCutAPI.git
cd VectCutAPI
pip install -r requirements.txt
pip install -r requirements-mcp.txt
cp config.json.example config.json
python mcp_server.py
```

### 9. ffmpeg-mcp-lite

*FFmpeg on Windows, macOS or Linux; stdio; MIT*

![ffmpeg-mcp-lite screenshot](https://assets.wireflow.ai/competitors/ffmpeg-mcp-lite-1898d28888a1.png?v=r5)

- **What it is:** A community FFmpeg server published on PyPI. Its eight tools trim, merge, convert and compress video, extract audio and frames, and burn SRT, ASS or VTT subtitles into a file.
- **Limits:** It works on files, not on a project timeline, so every edit writes a new output file. FFmpeg has to be installed separately.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://github.com/kevinwatt/ffmpeg-mcp-lite)

Claude Code command copied from the README. Install FFmpeg first:
```bash
claude mcp add ffmpeg uvx ffmpeg-mcp-lite
```

## Decision this list supports

You want Claude, Cursor or another MCP client to cut, caption and export video, and you need to know which editor it can actually drive. This list compares MCP servers for video editing on the details that decide setup: which host app and edition each one needs, how the client connects, which editing operations the docs list, whether the server is first-party, and its licence.

## Scope and evidence

Documentation reviewed on 2026-10-06. This is a Wireflow-maintained resource dataset. Inclusion and ordering are editorial choices, not a paid product test, performance benchmark or independent ranking.

Rows are servers whose job is editing existing footage, not generating new clips; the sibling dataset [mcp-video-generation-servers](https://github.com/a1adams/mcp-video-generation-servers) covers generation. Three rows are hosted connectors published by the editing vendor. Six are community servers, chosen as the most-starred maintained repository for each host app on 6 Oct 2026, with a licence file. Every cell comes from the server's own README, licence file or the vendor's documentation, and the Evidence by cell section links the page for each one. A check means the docs document it. A cross means the docs say it works another way. A dash means not published: the docs reviewed do not document it, which is not proof that it is absent.

The weekly repository job refreshes GitHub stars and release tags for the rows that have a repository. It does not re-check vendor features, editions or plan limits. Follow the official links for current terms.

## What each column means

- **Host app and edition:** the editor or tool that has to be installed and running, and which edition the server needs. It is in each tool's tagline and in Evidence by cell.
- **Transport:** how the MCP client connects, either a local process over stdio or a remote server over HTTP. It is in the Claude connection column of the data table.
- **Runs without a desktop editor:** the server works without a desktop editing app open on your machine.
- **Timeline edits:** the docs list tools that cut, trim or arrange clips on a timeline or in a composition.
- **Captions or subtitles:** the docs list a tool that adds captions or subtitles, or creates them from audio.
- **Render or export:** the docs list a tool that renders or exports a finished file, or publishes one.
- **First-party server:** the company behind the editing app publishes the server.
- **Open-source server code:** the server's own code is in a public repository with a licence file. The licence is in Evidence by cell.
- Stars and the latest release come from the GitHub API for rows with a repository.

## Evidence by cell

**Wireflow**

- Host app and edition: none to install. A Wireflow account; edits happen on the Video Editor node of a Wireflow workflow, in sceneGraph mode. [Claude Connector (MCP)](https://www.wireflow.ai/docs/mcp)
- Transport: Streamable HTTP at https://www.wireflow.ai/api/mcp, with OAuth 2.1 and PKCE. [Claude Connector (MCP)](https://www.wireflow.ai/docs/mcp)
- Runs without a desktop editor: yes. [Claude Connector (MCP)](https://www.wireflow.ai/docs/mcp)
- Timeline edits: yes. get_video_timeline reads every scene and clip with its timing, and edit_video_timeline replaces a video node's cut through a version-checked writer. [Claude Connector (MCP)](https://www.wireflow.ai/docs/mcp)
- Captions or subtitles: yes. The node map lists captions under the Video Editor in sceneGraph mode, and audio:whisper returns word-level timestamps for captions. [Claude Connector (MCP)](https://www.wireflow.ai/docs/mcp)
- Render or export: yes. run_workflow runs the workflow and spends credits; preview_video_frames shows still frames of a video node before you pay to render it. [Claude Connector (MCP)](https://www.wireflow.ai/docs/mcp)
- First-party server: yes. [Claude Connector (MCP)](https://www.wireflow.ai/docs/mcp)
- Open-source server code: not published. [Claude Connector (MCP)](https://www.wireflow.ai/docs/mcp)

**Descript MCP**

- Host app and edition: a Descript account. The connection is scoped to one Drive, and API or MCP use can spend media minutes and AI credits. [Descript MCP overview](https://help.descript.com/api-and-mcp/mcp)
- Transport: remote HTTP server at https://api.descript.com/v2/mcp with OAuth, no API token. [descript-mcp README](https://github.com/descriptinc/descript-mcp)
- Runs without a desktop editor: yes. The assistant can add captions, import media and edit projects without you opening the app. [Descript MCP overview](https://help.descript.com/api-and-mcp/mcp)
- Timeline edits: yes, through prompts. prompt_project_agent edits with Underlord in natural language, including trims. [descript-mcp README](https://github.com/descriptinc/descript-mcp)
- Captions or subtitles: yes. Underlord edits include adding captions, and transcripts export as SRT. [descript-mcp README](https://github.com/descriptinc/descript-mcp) and [Descript MCP overview](https://help.descript.com/api-and-mcp/mcp)
- Render or export: yes, by publishing. publish_project publishes a composition as a shareable link and an exported video or audio file; export_timeline exports a Premiere Pro or DaVinci Resolve timeline. Downloading a finished file without publishing is not supported. [descript-mcp README](https://github.com/descriptinc/descript-mcp) and [Descript MCP overview](https://help.descript.com/api-and-mcp/mcp)
- First-party server: yes. Descript ships official connectors in Claude's and ChatGPT's directories. [descript-mcp README](https://github.com/descriptinc/descript-mcp)
- Open-source server code: not published. The descriptinc/descript-mcp repository holds the client plugin, rules and skills under Apache-2.0, and points at the hosted server. [descript-mcp README](https://github.com/descriptinc/descript-mcp) and [LICENSE](https://github.com/descriptinc/descript-mcp/blob/main/LICENSE)

**Adobe for creativity**

- Host app and edition: no Adobe app needed. Guest users get about 40 standard tools; the resize and Quick Cut video workflows require an Adobe ID, and a few tools require a paid subscription. [Prompts and workflows](https://developer.adobe.com/adobe-for-creativity/prompts-and-workflows/) and [FAQ and support](https://developer.adobe.com/adobe-for-creativity/support/)
- Transport: a connector installed from Claude's connector directory, in Claude chat, Cowork and Claude Desktop. The docs do not name the transport. [Getting started](https://developer.adobe.com/adobe-for-creativity/getting-started/)
- Runs without a desktop editor: yes. [Adobe for creativity](https://developer.adobe.com/adobe-for-creativity/)
- Timeline edits: yes, as a workflow. Quick Cut turns longer videos into short clips such as a 30-second highlight reel. [Prompts and workflows](https://developer.adobe.com/adobe-for-creativity/prompts-and-workflows/)
- Captions or subtitles: not published as a tool. The FAQ's example prompt asks for a 9:16 version "with captions". [FAQ and support](https://developer.adobe.com/adobe-for-creativity/support/)
- Render or export: yes. Resized videos are delivered ready to share, and assets can be downloaded to continue in any Adobe app. [Adobe for creativity](https://developer.adobe.com/adobe-for-creativity/)
- First-party server: yes. [Adobe for creativity](https://developer.adobe.com/adobe-for-creativity/)
- Open-source server code: not published. [Adobe for creativity](https://developer.adobe.com/adobe-for-creativity/)

**DaVinci Resolve MCP (samuelgursky)**

- Host app and edition: DaVinci Resolve 18.5+ on macOS, Windows or Linux. Studio supports external scripting directly; the free edition is reachable through an in-app bridge, treated as a Resolve 21.0.x path. [README](https://github.com/samuelgursky/davinci-resolve-mcp)
- Transport: a local stdio process launched by the MCP client; an opt-in networked transport binds to loopback only. [README](https://github.com/samuelgursky/davinci-resolve-mcp)
- Runs without a desktop editor: no. [README](https://github.com/samuelgursky/davinci-resolve-mcp)
- Timeline edits: yes. Timeline tools include ripple insert, range operations and copy, move and duplicate helpers. [README](https://github.com/samuelgursky/davinci-resolve-mcp)
- Captions or subtitles: yes. CreateSubtitlesFromAudio is covered. [API coverage](https://github.com/samuelgursky/davinci-resolve-mcp/blob/main/docs/reference/api-coverage.md)
- Render or export: yes. Render settings validation, queued render jobs and guarded Quick Export. [README](https://github.com/samuelgursky/davinci-resolve-mcp)
- First-party server: no, a community project; the README credits Blackmagic Design for Resolve and its scripting API. [README](https://github.com/samuelgursky/davinci-resolve-mcp)
- Open-source server code: yes, MIT. [LICENSE](https://github.com/samuelgursky/davinci-resolve-mcp/blob/main/LICENSE)

**DaVinci Resolve MCP Bridge (hiteshK03)**

- Host app and edition: DaVinci Resolve 18+, free or Studio, through a bridge script started from Workspace, Scripts. The README says 155 of 162 tools work on the free edition. [README](https://github.com/hiteshK03/davinci-resolve-mcp)
- Transport: a command entry in the client config, which the client runs as a local stdio process; it talks to the bridge over localhost HTTP. [README](https://github.com/hiteshK03/davinci-resolve-mcp)
- Runs without a desktop editor: no. [README](https://github.com/hiteshK03/davinci-resolve-mcp)
- Timeline edits: yes. Add and remove clips, insert at specific frames and delete with ripple. [README](https://github.com/hiteshK03/davinci-resolve-mcp)
- Captions or subtitles: yes. Local transcription with word-level timestamps replaces Studio's auto subtitles, and subtitle tracks can be added. [README](https://github.com/hiteshK03/davinci-resolve-mcp)
- Render or export: yes. Render settings, the render queue, start and stop rendering, and quick export. [README](https://github.com/hiteshK03/davinci-resolve-mcp)
- First-party server: no, a community project. [README](https://github.com/hiteshK03/davinci-resolve-mcp)
- Open-source server code: yes, MIT. [LICENSE](https://github.com/hiteshK03/davinci-resolve-mcp/blob/main/LICENSE)

**Premiere Pro MCP Bridge (hetpatel-11)**

- Host app and edition: Adobe Premiere Pro 2020+, tested on Premiere Pro 26.0, with the CEP bridge panel running on the same computer. [README](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP)
- Transport: a local server the client launches from a command entry (premiere-pro-mcp), which MCP clients run over stdio. [README](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP)
- Runs without a desktop editor: no. [README](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP)
- Timeline edits: yes. split_clip, razor_all_tracks, trim_clip, roll, slide and slip edits, and ripple_delete. [README](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP)
- Captions or subtitles: yes, from a file. create_caption_track builds a caption track from an imported subtitle item such as an SRT; reading existing caption text is limited by Premiere's DOM. [README](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP)
- Render or export: yes. export_sequence queues a sequence through Adobe Media Encoder, plus frame, FCP XML, AAF and OMF exports. [README](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP)
- First-party server: no, a community project. [README](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP)
- Open-source server code: yes, MIT. [LICENSE.md](https://github.com/hetpatel-11/Adobe_Premiere_Pro_MCP/blob/main/LICENSE.md)

**After Effects MCP Server (Dakkshin)**

- Host app and edition: Adobe After Effects 2022 or later, with the MCP Bridge Auto panel open. [README](https://github.com/Dakkshin/after-effects-mcp)
- Transport: a command entry (node build/index.js) in the client config, run as a local stdio process. [README](https://github.com/Dakkshin/after-effects-mcp)
- Runs without a desktop editor: no. [README](https://github.com/Dakkshin/after-effects-mcp)
- Timeline edits: yes, at layer level. Layer properties include timing, and layers can be duplicated and deleted. [README](https://github.com/Dakkshin/after-effects-mcp)
- Captions or subtitles: not published. Text layers are supported; no caption or subtitle tool is listed. [README](https://github.com/Dakkshin/after-effects-mcp)
- Render or export: not published. No render or export tool is listed. [README](https://github.com/Dakkshin/after-effects-mcp)
- First-party server: no, a community project. [README](https://github.com/Dakkshin/after-effects-mcp)
- Open-source server code: yes, MIT. [LICENSE](https://github.com/Dakkshin/after-effects-mcp/blob/main/LICENSE)

**VectCutAPI**

- Host app and edition: Jianying or CapCut International version, Python 3.10+ and FFmpeg. [README](https://github.com/sun-guannan/VectCutAPI)
- Transport: python mcp_server.py starts the MCP service over stdio. [README](https://github.com/sun-guannan/VectCutAPI)
- Runs without a desktop editor: no. Jianying or CapCut is a listed requirement. [README](https://github.com/sun-guannan/VectCutAPI)
- Timeline edits: yes. add_video takes start and end points, with transitions and keyframes. [MCP documentation](https://github.com/sun-guannan/VectCutAPI/blob/main/MCP_Documentation_English.md)
- Captions or subtitles: yes. add_subtitle adds an SRT file with font style and position. [MCP documentation](https://github.com/sun-guannan/VectCutAPI/blob/main/MCP_Documentation_English.md)
- Render or export: no, through MCP. The 11 MCP tools end with save_draft; the README says rendering runs in the vendor's cloud through the API, or drafts are finished in CapCut or Jianying. [MCP documentation](https://github.com/sun-guannan/VectCutAPI/blob/main/MCP_Documentation_English.md) and [README](https://github.com/sun-guannan/VectCutAPI)
- First-party server: no. It is not published by CapCut or Jianying. [README](https://github.com/sun-guannan/VectCutAPI)
- Open-source server code: yes, Apache-2.0. [LICENSE](https://github.com/sun-guannan/VectCutAPI/blob/main/LICENSE)

**ffmpeg-mcp-lite**

- Host app and edition: FFmpeg installed on Windows, macOS or Linux; no editing app. [README](https://github.com/kevinwatt/ffmpeg-mcp-lite)
- Transport: a command entry (uvx ffmpeg-mcp-lite), run as a local stdio process. [README](https://github.com/kevinwatt/ffmpeg-mcp-lite)
- Runs without a desktop editor: yes. [README](https://github.com/kevinwatt/ffmpeg-mcp-lite)
- Timeline edits: yes, on files. ffmpeg_trim cuts by start and end time, and ffmpeg_merge joins several videos. [README](https://github.com/kevinwatt/ffmpeg-mcp-lite)
- Captions or subtitles: yes. ffmpeg_add_subtitles burns in SRT, ASS or VTT subtitles. [README](https://github.com/kevinwatt/ffmpeg-mcp-lite)
- Render or export: yes. Each tool writes an output file, by default to the Downloads folder. [README](https://github.com/kevinwatt/ffmpeg-mcp-lite)
- First-party server: no, a community project. [README](https://github.com/kevinwatt/ffmpeg-mcp-lite)
- Open-source server code: yes, MIT. [LICENSE](https://github.com/kevinwatt/ffmpeg-mcp-lite/blob/main/LICENSE)

## Selection notes

If the edit has to happen in an app your team already uses, pick the community server for that app and check its host edition first: the Premiere Pro and After Effects servers need those apps open, and the Resolve servers reach the free edition only through a bridge script. Of the desktop servers, the samuelgursky Resolve server, the hiteshK03 Resolve bridge and the Premiere Pro bridge document cut, captions and export together. If nobody should keep an editor open, Descript and Wireflow document trims, captions and a finished output over a hosted connection; Descript works by prompt on a Descript project, and Wireflow edits the scenes and clips of a video node inside a Wireflow workflow. ffmpeg-mcp-lite is the smallest option when the job is trimming, joining or subtitling files rather than editing a project.

## Acceptance recipe

1. Install or connect the server in the client your team uses, and confirm which app, project or Drive it acts on.
2. List the tools and note which ones change the project or spend credits before calling any of them.
3. Cut one clip at a set time and confirm the change reads back from the timeline.
4. Add captions to a short clip, from audio or from an SRT file, and check the timing.
5. Render or export the result and open the output file or link.
6. Disconnect the server and confirm the client can no longer change the project.

## Evaluation record

Record the server, version or release, host app and edition, client, project, the operations you ran, the output file or link, and the reviewer's decision. Keep failed edits next to successful ones so that a retry does not hide the original result.

## Related datasets

- [mcp-video-generation-servers](https://github.com/a1adams/mcp-video-generation-servers): MCP servers that generate video, compared on transport, auth, scopes and cost before a run.
- [awesome-claude-ai-video-generators](https://github.com/a1adams/awesome-claude-ai-video-generators): AI video generators you can use from Claude.

## How this list is maintained

- [`data/tools.json`](data/tools.json) is the source of truth. The tables in this README are generated from it and are overwritten on every run, so edit the JSON, not the tables.
- [`scripts/update.js`](scripts/update.js) fetches star counts and latest release tags from the GitHub API for the tools that publish an official repo, stamps the check date, and regenerates the tables. `--offline` regenerates without the network; `--check` exits non-zero if the README has drifted from the data.
- [`.github/workflows/refresh.yml`](.github/workflows/refresh.yml) runs it weekly and on manual dispatch, and commits only when the data actually changed.
- Prices are deliberately not stored as numbers. A stale price in a comparison table is worse than no price, so the table links to each vendor's own pricing page.

## Contributing

Corrections and additions are welcome, including corrections to the entry for the tool that maintains this list. Open an issue with the tool name, a working link, one line on what it does that the tools already listed do not, and one line on where it stops. Entries are judged on whether they are usable today, not on popularity. Full rules in [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[CC0 1.0 Universal](LICENSE), public domain. Take the data, fork the list, no attribution required.

---

Maintained by [a1adams](https://github.com/a1adams).

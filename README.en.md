# Mod Showroom

**A showroom of mods for Claude Code.** A catalog of plugins that change the client itself: bands above the prompt, panes, status entries, notifications, spinners, tool-call guards. The site shows every mod inside a mock of the client, and each one installs with a single command.

**[Open the site](https://krou4.github.io/claude-code-mod-showroom/)** · [Русский](README.md) · [Contributing](CONTRIBUTING.en.md) · [Research](docs/research.md)

[![Sync and deploy](https://github.com/KROU4/claude-code-mod-showroom/actions/workflows/sync.yml/badge.svg?branch=main)](https://github.com/KROU4/claude-code-mod-showroom/actions/workflows/sync.yml)

The catalog lists <!-- count:start -->266 mods<!-- count:end -->. The repository is also the Claude Code marketplace `mod-showroom`.

## Contents

- [What a mod is](#what-a-mod-is)
- [Install](#install)
- [Catalog](#catalog)
- [Add your mod](#add-your-mod)
- [How the repository is protected](#how-the-repository-is-protected)
- [Research](#research)
- [Related directories](#related-directories)
- [License](#license)

## What a mod is

A mod is a Claude Code plugin whose `hooks/hooks.json` names a module of function hooks. The hooks receive the client's events (tool calls, prompts, drawing) and can add to the interface or change behaviour: draw a band above the prompt, open a pane, refuse a tool call. Mods arrived in Claude Code 2.1.287 and run in the terminal, in the desktop app and, in part, in the VS Code panel.

```text
turn-meter/
├── .claude-plugin/
│   └── plugin.json      name, version, description
└── hooks/
    ├── hooks.json       { "modules": ["./register.tsx"] }
    └── register.tsx     export const register = (on) => { … }
```

## Install

You need Claude Code 2.1.287 or later; the desktop app runs mods from its bundled 2.1.286.

**In a Claude Code session in the terminal**, one command is enough. If the marketplace is not added yet, Claude Code offers to add it (2.1.275+):

```text
/plugin install turn-meter --marketplace KROU4/claude-code-mod-showroom
```

The same in two steps: add the marketplace once, then install mods by name.

```text
/plugin marketplace add KROU4/claude-code-mod-showroom
/plugin install turn-meter@mod-showroom
```

**From a shell** (2.1.292+):

```sh
claude plugin install turn-meter --marketplace KROU4/claude-code-mod-showroom
```

If a session is already open, run `/reload-plugins` in it or start a new one.

**In the desktop app** there is no `/plugin` command. Click "+" next to the prompt box, choose Plugins → Add marketplace, enter `KROU4/claude-code-mod-showroom`, then Add plugin. A mod installed from the terminal at user scope also loads in the desktop app.

**In VS Code** a link of the form `vscode://anthropic.claude-code/install-plugin` installs a mod in one click. GitHub does not render such links, so the "Install in VS Code", "Open in terminal" and "Open in Claude desktop" buttons live on each mod's page [on the site](https://krou4.github.io/claude-code-mod-showroom/).

A mod runs inside your session with your permissions. Read an external mod's code before you install it: every entry links to its source.

## Catalog

Each mod says what it draws, who wrote it and where its code lives: "hosted here" means the code is in `mods/<name>/plugin/`, checked by CI, with changes after the first version read by a catalog maintainer; "external" means it lives in the author's repository. It is community code either way: read it before you install. The install command is under the fold.

<!-- mods:start -->
Categories: [Interface](#interface) · [Insights](#insights) · [Safety](#safety) · [Productivity](#productivity) · [Git](#git) · [Integrations](#integrations) · [Fun](#fun) · [Accessibility](#accessibility)

### Interface

- **[bline](https://krou4.github.io/claude-code-mod-showroom/#/mod/bline)** — Model, reasoning effort and context fill on the hint line under the prompt, each one clickable. <sub>draws: hint line · by @xchacha20-poly1305 · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install bline --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Clarity](https://krou4.github.io/claude-code-mod-showroom/#/mod/clarity)** — Boxed prompts and replies, colour-coded tool badges, a live status band and a session panel. <sub>draws: tool rows, spinner, turn duration line, pane, status line, toast, notification, slash command · by @CircularBlox · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install clarity --marketplace CircularBlox/Clarity
  ```

  </details>
- **[Claudinator](https://krou4.github.io/claude-code-mod-showroom/#/mod/claudinator)** — Six switchable looks for tool rows, the working line and turn receipts, and nine ingredients to mix. <sub>draws: tool rows, turn duration line, slash command, pane, toast · by @patheonsceo · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install claudinator --marketplace patheonsceo/claudinator
  ```

  </details>
- **[Desk Look](https://krou4.github.io/claude-code-mod-showroom/#/mod/desk-look)** — The terminal transcript redrawn like the desktop app's Code tab, with diff, PR and context panes. <sub>draws: tool rows, transcript messages, band above the prompt, pane, notification, slash command, tool for Claude · by @KyongSik-Yoon · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install desk-look --marketplace KyongSik-Yoon/cc-desktop-mod
  ```

  </details>
- **[Drawer](https://krou4.github.io/claude-code-mod-showroom/#/mod/drawer)** — \`\`\`dot (Graphviz) and \`\`\`svg fences in a reply become pictures in place while the reply streams. <sub>draws: transcript messages · by @Sureffi · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install drawer --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Figures](https://krou4.github.io/claude-code-mod-showroom/#/mod/figures)** — Mermaid, Graphviz, D2 and SVG diagrams, LaTeX math and tool images drawn inline in kitty terminals. <sub>draws: transcript messages, pane, toast, slash command · by @natsukium · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install figures --marketplace natsukium/claude-code-figures-plugin
  ```

  </details>
- **[Filetree](https://krou4.github.io/claude-code-mod-showroom/#/mod/filetree)** — A sidebar file tree with git status and +/- line counts; files Claude reads and writes shimmer. <sub>draws: pane, toast, slash command · by @data-goblin · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install filetree --marketplace data-goblin/claude-code-filetree
  ```

  </details>
- **[Firelight](https://krou4.github.io/claude-code-mod-showroom/#/mod/firelight)** — Three Firelight themes (Coal, Smoulder, Ash) that also repaint the terminal's background to match. <sub>by @GarvitNangru · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install firelight --marketplace GarvitNangru/claude-code-mods
  ```

  </details>
- **[Firstmate Calm](https://krou4.github.io/claude-code-mod-showroom/#/mod/fm)** — Hides tool rows and turns the working spinner into a drifting two-row sailboat; toggled with /calm. <sub>draws: slash command, toast, band above the prompt, transcript messages · by @kunchenguid · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install fm --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Glass](https://krou4.github.io/claude-code-mod-showroom/#/mod/glass)** — A desktop-app look for the terminal transcript: colored commands, code and diff cards, 13 palettes. <sub>draws: tool rows, transcript messages, status line, toast, notification, slash command · by @rashedInt32 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install glass --marketplace rashedInt32/glass
  ```

  </details>
- **[glowup](https://krou4.github.io/claude-code-mod-showroom/#/mod/glowup)** — A cockpit pane, packs that restyle colors, tool rows and the spinner, and a pixel pet that reacts. <sub>draws: slash command, transcript messages, tool rows, spinner, pane, status line · by @NovusEdge · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install glowup --marketplace NovusEdge/glowup
  ```

  </details>
- **[Image Peek](https://krou4.github.io/claude-code-mod-showroom/#/mod/image-peek)** — Thumbnails of pasted images above the prompt, and larger pictures under each sent message. <sub>draws: band above the prompt · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install image-peek --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Image View](https://krou4.github.io/claude-code-mod-showroom/#/mod/image-view)** — Thumbnails of the images you paste, shown above the prompt instead of bare \[Image \#1\] tags. <sub>draws: band above the prompt · by @jarrodwatts · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install image-view --marketplace jarrodwatts/claude-image-view
  ```

  </details>
- **[Inline Images](https://krou4.github.io/claude-code-mod-showroom/#/mod/inline-images)** — A show\_image tool for Claude, plus pasted images and images Claude reads drawn in the transcript. <sub>draws: tool for Claude · by @benjaminb10 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install inline-images --marketplace benjaminb10/encore-mods
  ```

  </details>
- **[Intelligent UI](https://krou4.github.io/claude-code-mod-showroom/#/mod/intelligent-ui)** — Claude's answers as typeset pictures: tables, LaTeX math, charts and diagrams rendered by Typst. <sub>draws: slash command, transcript messages, toast, pane · by @razorback16 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cc-intelligent-ui --marketplace razorback16/cc-intelligent-ui
  ```

  </details>
- **[jr badge](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-badge)** — A colored project badge and its branch above the prompt, so you know which window you type in. <sub>draws: band above the prompt, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-badge --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[mercat](https://krou4.github.io/claude-code-mod-showroom/#/mod/mercat)** — Mermaid blocks in replies drawn as text diagrams, plus a pane for markdown and mermaid files. <sub>draws: transcript messages, pane, toast, slash command · by @tawago · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install mercat --marketplace tawago/mercat
  ```

  </details>
- **[Model Effort Band](https://krou4.github.io/claude-code-mod-showroom/#/mod/model-effort-band)** — A colored band above the prompt with the selected model and the effort of its last request. <sub>draws: band above the prompt · by @YeonwooSung · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install model-effort-band --marketplace YeonwooSung/my-claude-code-mods
  ```

  </details>
- **[Paste Peek](https://krou4.github.io/claude-code-mod-showroom/#/mod/paste-peek)** — Windows Terminal: thumbnails of the images you paste, in a small strip until you send. <sub>draws: toast · by @MankhongGarden · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install paste-peek --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Plain View](https://krou4.github.io/claude-code-mod-showroom/#/mod/plain-view)** — A quiet transcript: tool rows step aside and the agent's plan shows as a card with progress bars. <sub>draws: band above the prompt, pane, toast, slash command · by @ice-lfernandes · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install plain-view --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[Prismantis](https://krou4.github.io/claude-code-mod-showroom/#/mod/prismantis)** — Colorful, themeable replies: tables, code, mermaid charts and diagrams, with copy buttons. <sub>draws: transcript messages, pane, toast, slash command · by @NahumLitvin · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install prismantis --marketplace NahumLitvin/prismantis
  ```

  </details>
- **[Quiet Transcript](https://krou4.github.io/claude-code-mod-showroom/#/mod/quiet-transcript)** — Narration, tool calls and command output fade; Claude's answers stay as they are. <sub>draws: transcript messages, tool rows · by @kevlar10x · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install quiet-transcript --marketplace kevlar10x/quiet-transcript
  ```

  </details>
- **[Readable Layout](https://krou4.github.io/claude-code-mod-showroom/#/mod/readable-layout)** — Your messages and Claude's answers in labeled boxes, notes as quiet lines, bold text in color. <sub>draws: transcript messages, turn duration line · by @GarvitNangru · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install readable-layout --marketplace GarvitNangru/claude-code-mods
  ```

  </details>
- **[Rich UI](https://krou4.github.io/claude-code-mod-showroom/#/mod/rich-ui)** — Mermaid diagrams drawn in the transcript, markdown previews in a pane and more, each switchable. <sub>draws: transcript messages, status line, pane, toast, slash command · by @emergentai · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install rich-ui --marketplace emergentai/claude-code-rich-ui
  ```

  </details>
- **[Show Me](https://krou4.github.io/claude-code-mod-showroom/#/mod/show-me)** — Mermaid diagrams in an answer are drawn as pictures in a pane once the turn ends. <sub>draws: pane, toast, slash command · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install show-me --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Show Paths](https://krou4.github.io/claude-code-mod-showroom/#/mod/show-paths)** — Every Read, Edit, Write, Glob and Grep row in the transcript shows the path it touched. <sub>draws: tool rows, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install show-paths --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Show Your Work](https://krou4.github.io/claude-code-mod-showroom/#/mod/show-your-work)** — Claude shows screenshots and Playwright recordings inline in the chat, with before/after and QA. <sub>draws: tool rows, tool for Claude, slash command, pane, status line, toast · by @iamumeransari · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install show-your-work --marketplace iamumeransari/claude-show-your-work
  ```

  </details>
- **[Skins](https://krou4.github.io/claude-code-mod-showroom/#/mod/skins)** — Tool rows with status, timings and +/− counts, shell and table cards, a usage band and 15 themes. <sub>draws: slash command, toast, tool rows, spinner, turn duration line, band above the prompt, tool for Claude, pane · by @hellosverre · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install skins --marketplace hellosverre/claude-skins
  ```

  </details>
- **[Status Line Anywhere](https://krou4.github.io/claude-code-mod-showroom/#/mod/statusline-anywhere)** — Runs your own statusLine command and draws its output in color above the prompt in the desktop app. <sub>draws: band above the prompt · by @NathanAB · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install statusline-anywhere --marketplace NathanAB/statusline-anywhere
  ```

  </details>
- **[Stretchtext Replies](https://krou4.github.io/claude-code-mod-showroom/#/mod/cc-stretch)** — Replies arrive short; click an underlined phrase and it grows in place into the longer version. <sub>draws: transcript messages, slash command, band above the prompt, toast · by @pro-vi · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cc-stretch --marketplace pro-vi/cc-stretch
  ```

  </details>
- **[TL;DR](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-tldr)** — Every turn folded into one row: files changed, tests before and after, and what to check. <sub>draws: transcript messages, notification, pane, status line, slash command · by @kushalBanda · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install tldr --marketplace kushalBanda/claude-tldr
  ```

  </details>
- **[Veneer](https://krou4.github.io/claude-code-mod-showroom/#/mod/veneer)** — Syntax highlighting in 100+ languages with any VS Code theme, diagrams, math and images in the chat. <sub>draws: tool rows, transcript messages, pane, slash command · by @MitchMedeiros · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install veneer --marketplace MitchMedeiros/veneer
  ```

  </details>

### Insights

- **[Agent Monitor](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-monitor)** — A progress bar above the prompt that fills as Claude works through its plan, plus a subagent panel. <sub>draws: band above the prompt, pane, slash command, tool for Claude · by @GarvitNangru · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install agent-monitor --marketplace GarvitNangru/claude-code-mods
  ```

  </details>
- **[Agent Radar](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-radar)** — A live line above the prompt per running subagent or background shell: time, tools, current step. <sub>draws: band above the prompt, toast, slash command, pane · by @hamzafer · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install agent-radar --marketplace hamzafer/claude-code-mods
  ```

  </details>
- **[Agent Tree](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-tree)** — A side pane that draws a session's agents as a tree of boxes, with stop and model choice by click. <sub>draws: pane, status line, slash command · by @MikeGT4 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install agent-tree --marketplace MikeGT4/agent-tree
  ```

  </details>
- **[Agent Watch](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-watch)** — Subagents at a glance: a card per agent with a mascot, its step and tokens, and a stall toast. <sub>draws: status line, toast, pane, slash command · by @ice-lfernandes · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install agent-watch --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[Ant Farm](https://krou4.github.io/claude-code-mod-showroom/#/mod/ant-farm)** — Mission control for subagents: a live card per agent with status, tokens, estimated cost and ETA. <sub>draws: band above the prompt, pane, status line, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install ant-farm --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Burn Baby Burn](https://krou4.github.io/claude-code-mod-showroom/#/mod/burn-baby-burn)** — Session and weekly usage gauges under the prompt, and fiery nags when your week would go unspent. <sub>draws: hint line, toast, slash command, status line · by @qorvyx · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install burn-baby-burn --marketplace qorvyx/burn-baby-burn
  ```

  </details>
- **[Burn Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/burn-meter)** — Session cost above the prompt with a fire bar, plan limits and the price in burritos. <sub>draws: band above the prompt, toast, slash command, pane · by @OneWave-AI · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install burn-meter --marketplace OneWave-AI/claude-code-mods
  ```

  </details>
- **[Cache Clock](https://krou4.github.io/claude-code-mod-showroom/#/mod/cache-clock)** — A prompt-cache line under your status line: time left while warm, hit rate, misses, re-cache tokens. <sub>draws: slash command, status line · by @hamzafer · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cache-clock --marketplace hamzafer/claude-code-mods
  ```

  </details>
- **[Cache Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/cache-meter)** — Prompt-cache hit rate and time left warm above the prompt, with a Keep warm switch for breaks. <sub>draws: band above the prompt, toast · by @T-AI-Labs · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cache-meter --marketplace T-AI-Labs/claude-code-mods
  ```

  </details>
- **[Cache Timer](https://krou4.github.io/claude-code-mod-showroom/#/mod/cache-timer)** — A countdown above the prompt to when the prompt cache expires, and what a cold cache will re-write. <sub>draws: band above the prompt · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install cache-timer --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Claude Carbon](https://krou4.github.io/claude-code-mod-showroom/#/mod/carbon-footprint)** — The estimated CO2 of each answer and of the session, with a pixel molecule pane in the desktop app. <sub>draws: turn duration line, band above the prompt, pane, status line, toast, slash command · by @gwittebolle · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install claude-carbon --marketplace gwittebolle/claude-carbon
  ```

  </details>
- **[Claude Context Bar](https://krou4.github.io/claude-code-mod-showroom/#/mod/context-status-bar)** — A skinnable bar above the prompt: context gauge, 5-hour usage, git, turn time and session age. <sub>draws: band above the prompt, pane, toast, slash command · by @eddywong888 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install context-bar --marketplace eddywong888/claude-context-bar
  ```

  </details>
- **[Cockpit](https://krou4.github.io/claude-code-mod-showroom/#/mod/cockpit)** — One live dashboard pane: agents, cache, context, tokens, limits, files, permission checks and a log. <sub>draws: pane, band above the prompt, slash command · by @bharath-gp · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cockpit --marketplace bharath-gp/ai-harness
  ```

  </details>
- **[Code Display](https://krou4.github.io/claude-code-mod-showroom/#/mod/st-code-display)** — A read-only OLED-style pane: model and limits, agents, architect consults, tools, files and a log. <sub>draws: pane, slash command · by @sergios-tech · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install st-code-display --marketplace sergios-tech/code-display
  ```

  </details>
- **[Command Clock](https://krou4.github.io/claude-code-mod-showroom/#/mod/cccc)** — How long each foreground Bash command has been running, on a dim line under its row. <sub>draws: tool rows · by @xchacha20-poly1305 · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install cccc --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Context Bar](https://krou4.github.io/claude-code-mod-showroom/#/mod/context-bar)** — A stacked bar above the prompt showing what fills your context window and where it compacts. <sub>draws: band above the prompt, slash command · by @hamzafer · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install context-bar --marketplace hamzafer/claude-code-mods
  ```

  </details>
- **[Context Gauge](https://krou4.github.io/claude-code-mod-showroom/#/mod/context-gauge)** — See how full the context window is, right in the hint line under the prompt. <sub>draws: hint line · by @KROU4 · hosted here</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install context-gauge --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Context Usage](https://krou4.github.io/claude-code-mod-showroom/#/mod/context-usage)** — Context fill with an auto-compact threshold, Compact and Clear, and the 5-hour and weekly limits. <sub>draws: band above the prompt, toast · by @T-AI-Labs · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install context-usage --marketplace T-AI-Labs/claude-code-mods
  ```

  </details>
- **[Cost Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/cost-meter)** — Session cost, context and rate limits on the status line, each turn's price, and an optional budget. <sub>draws: turn duration line, status line, toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cost-meter --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Files Touched](https://krou4.github.io/claude-code-mod-showroom/#/mod/files-touched)** — Every file Claude changed this session in a band above the prompt, with +/− counts and @mentions. <sub>draws: band above the prompt, pane, toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install files-touched --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Fine Print](https://krou4.github.io/claude-code-mod-showroom/#/mod/fine-print)** — A small model rereads long replies and flags hidden costs, security risks and irreversible steps. <sub>draws: band above the prompt, pane, status line, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install fine-print --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Flightdeck](https://krou4.github.io/claude-code-mod-showroom/#/mod/flightdeck)** — A live pane of your session: context and cost, every permission check, subagents and a session log. <sub>draws: slash command, pane, status line · by @scasella · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install flightdeck --marketplace scasella/claude-flightdeck
  ```

  </details>
- **[Footprints](https://krou4.github.io/claude-code-mod-showroom/#/mod/footprints)** — A live file tree in a pane that colors what Claude read, edited, created, deleted and committed. <sub>draws: pane, status line, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install footprints --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Headway](https://krou4.github.io/claude-code-mod-showroom/#/mod/headway)** — A line above the prompt with the plan's stage, current step, steps done and time left. <sub>draws: band above the prompt, toast, pane, slash command, tool for Claude · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install headway --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[jr cache clock](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-cache-clock)** — A toast 30 seconds before the prompt cache goes cold, and an optional countdown above the prompt. <sub>draws: band above the prompt, toast, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-cache-clock --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr context](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-context)** — The context window in one quiet row above the prompt that turns into an alert before compaction. <sub>draws: band above the prompt, pane, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-context --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr heatmap](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-heatmap)** — Your last 26 weeks with Claude Code as a GitHub-style heatmap, with streaks and peak hours. <sub>draws: pane, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-heatmap --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr limits](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-limits)** — Your 5-hour and 7-day plan limits in one quiet row above the prompt, with toasts at 80% and 95%. <sub>draws: band above the prompt, toast, pane, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-limits --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Limit Lens](https://krou4.github.io/claude-code-mod-showroom/#/mod/limit-lens)** — This session's share of your 5-hour and weekly limits, and its cost on each model. <sub>draws: band above the prompt, pane, slash command · by @cristi71000 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install limit-lens --marketplace cristi71000/limit-lens
  ```

  </details>
- **[Limits Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/limits-meter)** — Model, plan limits, a prompt-cache countdown and context by group in one band above the prompt. <sub>draws: band above the prompt, toast, pane, slash command · by @ice-lfernandes · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install limits-meter --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[Memory Lint](https://krou4.github.io/claude-code-mod-showroom/#/mod/memory-lint)** — Tells you whether your MEMORY.md auto-memory index fits a line limit, and which entries are past it. <sub>draws: status line, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install memory-lint --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Owner Rep](https://krou4.github.io/claude-code-mod-showroom/#/mod/owner-rep)** — Watches your agent and says in plain English what is done, what was left out and what to send next. <sub>draws: band above the prompt, toast · by @macollins27 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install owner-rep --marketplace macollins27/owner-rep
  ```

  </details>
- **[Play-by-Play](https://krou4.github.io/claude-code-mod-showroom/#/mod/play-by-play)** — Replays every file change of a turn step by step, including what shell commands changed. <sub>draws: band above the prompt, pane, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install play-by-play --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Rabe](https://krou4.github.io/claude-code-mod-showroom/#/mod/rabe)** — See Claude Code's background work: subagents, Codex jobs, shells, monitors, cron jobs and workflows. <sub>draws: band above the prompt, pane, slash command · by @lorenzh · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install rabe --marketplace lorenzh/rabe
  ```

  </details>
- **[Redline](https://krou4.github.io/claude-code-mod-showroom/#/mod/redline)** — Context fill, plan windows, session cost and pace in the status line, with a toast at 80% context. <sub>draws: status line, toast, slash command, pane · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install redline --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Search Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/search-meter)** — Counts Claude's searches under the prompt: found first try, found after misses, or found nothing. <sub>draws: status line · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install search-meter --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Session Band](https://krou4.github.io/claude-code-mod-showroom/#/mod/session-band)** — Turn, cache countdown, speed, context and 5h/weekly limits above the prompt, plus an activity pane. <sub>draws: band above the prompt, pane, notification, toast, slash command · by @KhoaaTran · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install session-band --marketplace KhoaaTran/session-band
  ```

  </details>
- **[Session Info](https://krou4.github.io/claude-code-mod-showroom/#/mod/session-info)** — One pane, thirteen cards: context and cache, last turn, todos, CI, Jira, usage, agents, checks, git. <sub>draws: pane, slash command · by @dougcunha · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install session-info --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Session Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/session-meter)** — A /ctx pane with context by category, usage limits and their pace, tool calls and model requests. <sub>draws: pane, toast, slash command, tool for Claude · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install session-meter --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Session Models](https://krou4.github.io/claude-code-mod-showroom/#/mod/session-models)** — The main model and effort, every live agent by model and effort, and warnings about agent crowds. <sub>draws: band above the prompt, toast, status line · by @AbhiramDwivedi · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install session-models --marketplace AbhiramDwivedi/claude-ops
  ```

  </details>
- **[Sub Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/sub-meter)** — Your 5-hour and weekly subscription usage as a bar with the reset time, at the bottom right. <sub>draws: hint line, mode label · by @midudev · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install sub-meter --marketplace midudev/better-claude
  ```

  </details>
- **[Subagents Plus](https://krou4.github.io/claude-code-mod-showroom/#/mod/subagents-plus)** — A live tree and timeline of every subagent in a /subagents pane, plus a band above the prompt. <sub>draws: band above the prompt, slash command, pane, tool for Claude · by @algonormative · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install subagents-plus --marketplace algonormative/subagents-plus
  ```

  </details>
- **[Test Pulse](https://krou4.github.io/claude-code-mod-showroom/#/mod/test-pulse)** — Every test run Claude makes lands in the status line; a toast when tests go red or green again. <sub>draws: status line, toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install test-pulse --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Time Blame](https://krou4.github.io/claude-code-mod-showroom/#/mod/time-blame)** — Under each answer, the turn's time split into Claude, tools, you and other; /blame sums the session. <sub>draws: turn duration line, slash command, pane · by @karanb192 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install time-blame --marketplace karanb192/time-blame
  ```

  </details>
- **[Token Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/token-meter)** — Each turn's input, output and cache tokens plus the session total, in color on the hint line. <sub>draws: hint line · by @midudev · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install token-meter --marketplace midudev/better-claude
  ```

  </details>
- **[Token Optimizer](https://krou4.github.io/claude-code-mod-showroom/#/mod/token-optimizer)** — Audits and trims what fills your context, with a session-health bar and Clawd in the desktop app. <sub>draws: band above the prompt, toast · by @alexgreensh · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install token-optimizer --marketplace alexgreensh/token-optimizer
  ```

  </details>
- **[Token Watch](https://krou4.github.io/claude-code-mod-showroom/#/mod/token-watch)** — Plan usage with burn rates, context by category and a prompt-cache countdown above the prompt. <sub>draws: band above the prompt, notification, slash command · by @nevermemo · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install token-watch --marketplace nevermemo/token-watch
  ```

  </details>
- **[Token Weather](https://krou4.github.io/claude-code-mod-showroom/#/mod/token-weather)** — Context fill as weather above the prompt: icon, percent, tokens and a chart of the last 12 turns. <sub>draws: band above the prompt · by @anthropics · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install token-weather --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Tool Radar](https://krou4.github.io/claude-code-mod-showroom/#/mod/tool-radar)** — A live pane of every tool call with status, arguments, duration and why it failed, subagents too. <sub>draws: pane, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install tool-radar --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Tool Timeline](https://krou4.github.io/claude-code-mod-showroom/#/mod/tool-timeline)** — A live pane of every tool call: its status, what it worked on and how long it took. <sub>draws: slash command, pane · by @KROU4 · hosted here</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install tool-timeline --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Turn Footer](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-footer)** — Tools, requests, tokens and cache hit under each answer; the spinner names the running tool. <sub>draws: spinner, transcript messages · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install turn-footer --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Turn Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-meter)** — Each turn's duration, tool calls and tokens in a band above the prompt, with a 12-turn sparkline. <sub>draws: band above the prompt, toast, slash command · by @KROU4 · hosted here</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install turn-meter --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Turn Stats](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-stats)** — Under the line that closes a turn: tool calls by tool, failures, files changed and cost. <sub>draws: turn duration line, transcript messages · by @StanislavKozachenko · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install turn-stats --marketplace StanislavKozachenko/claude-mods
  ```

  </details>
- **[Turn Timeline](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-timeline)** — A /timeline pane: the current turn as lanes of model requests and tool calls, and its slowest steps. <sub>draws: pane, slash command · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install turn-timeline --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Turn Timer](https://krou4.github.io/claude-code-mod-showroom/#/mod/turn-timer)** — A ticking timer above the prompt while Claude works, then how long the reply took. <sub>draws: band above the prompt · by @thecodefeels · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install turn-timer --marketplace thecodefeels/claude-code-turn-timer
  ```

  </details>
- **[Usage Bar](https://krou4.github.io/claude-code-mod-showroom/#/mod/usage-bar)** — Context, session cost and plan limits on one quiet line above the prompt, with a cache-cold warning. <sub>draws: band above the prompt, toast · by @andrej-kolic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install usage-bar --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Usage Limits](https://krou4.github.io/claude-code-mod-showroom/#/mod/usage-limits)** — 5-hour and weekly limits with burn rate and a run-out forecast, plus context, cost and cache drops. <sub>draws: band above the prompt, toast, status line · by @AbhiramDwivedi · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install usage-limits --marketplace AbhiramDwivedi/claude-ops
  ```

  </details>
- **[Usage Meter](https://krou4.github.io/claude-code-mod-showroom/#/mod/usage-meter)** — A cyberpunk band of plan limits, context and tokens, plus a pane with charts, agents, git and PRs. <sub>draws: band above the prompt, pane, slash command · by @PointerLex · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install usage-meter --marketplace PointerLex/claude-usage-meter
  ```

  </details>
- **[Usage Stats](https://krou4.github.io/claude-code-mod-showroom/#/mod/usage-stats)** — /usage-stats opens a token heat map, history by model, an hour-of-day chart and a Wrapped card. <sub>draws: slash command, pane, toast · by @connorchuang32 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install usage-stats --marketplace connorchuang32/claude-usage-stats
  ```

  </details>
- **[WeekToken](https://krou4.github.io/claude-code-mod-showroom/#/mod/weektoken)** — Rate-limit pace: 5-hour and weekly usage against elapsed time, with a forecast and burn-up history. <sub>draws: band above the prompt, pane, slash command, toast · by @3dnow · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install weektoken --marketplace 3dnow/claude-mods
  ```

  </details>
- **[What's Agent Doing](https://krou4.github.io/claude-code-mod-showroom/#/mod/whats-agent-doing)** — A box above the prompt saying what the agent is doing right now, for how long, and each step so far. <sub>draws: band above the prompt · by @tzafrir · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install whats-agent-doing --marketplace tzafrir/whats-agent-doing
  ```

  </details>

### Safety

- **[Agent Usage Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-usage-guard)** — Holds subagent fan-out, heavy-context prompts and retry loops before they burn your usage window. <sub>draws: tool guard, status line, slash command · by @rbartoli · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install agent-usage-guard --marketplace rbartoli/agent-usage-guard
  ```

  </details>
- **[Bash Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/bash-guard)** — Blocks catastrophic shell commands and asks before risky ones, even with permissions bypassed. <sub>draws: tool guard, toast, transcript messages, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install bash-guard --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Blast Radius](https://krou4.github.io/claude-code-mod-showroom/#/mod/blast-radius)** — Holds risky shell commands, lists the files, commits or migrations they'd touch: Proceed or Cancel. <sub>draws: pane, tool guard, toast · by @anthropics · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install blast-radius --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Bouncer](https://krou4.github.io/claude-code-mod-showroom/#/mod/bouncer)** — Lists what every installed mod can reach, read from Claude Code's own plugin validator. <sub>draws: band above the prompt, pane, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install bouncer --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[ccpii](https://krou4.github.io/claude-code-mod-showroom/#/mod/ccpii)** — Names, emails, phones and other personal data reach the model as numbered placeholders. <sub>draws: prompt rewrite, status line, toast, slash command · by @xchacha20-poly1305 · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install ccpii --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Circuit Breaker](https://krou4.github.io/claude-code-mod-showroom/#/mod/circuit-breaker)** — After the same shell command fails N times in a row, the next try waits for you: stop, or once more. <sub>draws: tool guard, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install circuit-breaker --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Cloakroom](https://krou4.github.io/claude-code-mod-showroom/#/mod/cloakroom)** — Secrets reach Claude as tickets; the real value comes back only in local edits and vetted commands. <sub>draws: tool guard, band above the prompt, pane, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cloakroom --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Command Explainer](https://krou4.github.io/claude-code-mod-showroom/#/mod/command-explainer)** — A plain-English line on what a shell command will do, with its risk, right where you approve it. <sub>draws: tool rows, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install command-explainer --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Fence](https://krou4.github.io/claude-code-mod-showroom/#/mod/fence)** — Limit which paths Claude may edit in a project with one /fence command; edits outside are refused. <sub>draws: slash command, tool guard · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install fence --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[File Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/file-guard)** — Keeps Claude's file edits inside the project; lockfiles, CI, migrations and secrets ask first. <sub>draws: tool guard, transcript messages, toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install file-guard --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/guard)** — Refuses destructive shell commands and secret files anywhere in a command, in Bash and PowerShell. <sub>draws: tool guard, status line, toast, slash command · by @StanislavKozachenko · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install guard --marketplace StanislavKozachenko/claude-mods
  ```

  </details>
- **[Guardrails](https://krou4.github.io/claude-code-mod-showroom/#/mod/ai-harness-guardrails)** — Ten safety and review mods: a risky-command hold, a secret block, critique, a prompt coach and more. <sub>draws: tool guard, band above the prompt, slash command · by @bharath-gp · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install guardrails --marketplace bharath-gp/ai-harness
  ```

  </details>
- **[Guardrails](https://krou4.github.io/claude-code-mod-showroom/#/mod/guardrails)** — Refuses shell commands you switch on in /config: cf deploys, attribution lines, claude/ branches. <sub>draws: tool guard · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install guardrails --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Injection Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/injection-guard)** — Strips hidden characters from tool results and marks text that tries to give Claude orders. <sub>draws: toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install injection-guard --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[jr deploy guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-deploy-guard)** — Production deploys and pushes to main always come to you for a yes, whatever your rules allow. <sub>draws: tool guard · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-deploy-guard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr done-check](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-done-check)** — Flags replies that say "tested" or "it works" when nothing was run in the turn to check it. <sub>draws: transcript messages, toast · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-done-check --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr explain](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-explain)** — Each shell command Claude asks to run comes with a plain-English explanation and a risk level. <sub>draws: toast · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-explain --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr image guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-image-guard)** — Keeps oversized images out of the conversation: Claude reads a resized copy instead. <sub>draws: tool rows, toast · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-image-guard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr mod audit](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-mod-audit)** — Look at a mod before you install it: what it can reach, with a green, amber or red verdict. <sub>draws: slash command, pane · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-mod-audit --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Last Look](https://krou4.github.io/claude-code-mod-showroom/#/mod/last-look)** — Holds destructive shell commands for your OK and shows the files, unsaved work and commits at stake. <sub>draws: pane, status line, tool guard · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install last-look --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Loadout](https://krou4.github.io/claude-code-mod-showroom/#/mod/loadout)** — A mod manager: unapproved mods and versions stay blocked until Claude audits them and you approve. <sub>draws: toast, band above the prompt, pane, slash command · by @Br4inergy · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install loadout --marketplace Br4inergy/claude-loadout
  ```

  </details>
- **[Loop Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/loop-guard)** — When the same tool call fails twice with the same error, Claude is told to stop and change approach. <sub>draws: toast · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install loop-guard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Mulligan](https://krou4.github.io/claude-code-mod-showroom/#/mod/mulligan)** — Saves your files before a destructive shell command runs; /mulligan restore puts them back. <sub>draws: band above the prompt, slash command, pane, toast · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install mulligan --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Net Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/net-guard)** — Checks every curl, wget, ssh, scp, git push and WebFetch against allow and deny lists. <sub>draws: tool guard, transcript messages, toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install net-guard --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Package Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/pkg-guard)** — Holds installs of packages that don't exist, are brand new or barely used, with the registry facts. <sub>draws: tool guard, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pkg-guard --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Receipts](https://krou4.github.io/claude-code-mod-showroom/#/mod/receipts)** — Claude says the tests pass; Receipts checks that a test or build actually ran after the last edit. <sub>draws: transcript messages, band above the prompt, pane, toast, slash command · by @candygoogy · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install receipts --marketplace candygoogy/notary
  ```

  </details>
- **[Redact](https://krou4.github.io/claude-code-mod-showroom/#/mod/redact)** — Keys, tokens and passwords that tools print are replaced before the model reads them. <sub>draws: status line, toast, slash command · by @StanislavKozachenko · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install redact --marketplace StanislavKozachenko/claude-mods
  ```

  </details>
- **[Sandbox Tuner](https://krou4.github.io/claude-code-mod-showroom/#/mod/sandbox-tuner)** — Explains each sandbox block and turns recurring ones into reviewed, undoable settings edits. <sub>draws: band above the prompt, slash command · by @dot-agi · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install sandbox-tuner --marketplace dot-agi/sandbox-tuner
  ```

  </details>
- **[Scope Cop](https://krou4.github.io/claude-code-mod-showroom/#/mod/scope-cop)** — Say which files a task may touch; edits outside that scope are flagged, told to Claude or blocked. <sub>draws: slash command, band above the prompt, tool guard, pane, toast · by @candygoogy · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install scope-cop --marketplace candygoogy/notary
  ```

  </details>
- **[Secret Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/secret-guard)** — Stops Claude from reading .env files, private keys and credentials. <sub>draws: tool guard, toast, status line · by @KROU4 · hosted here</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install secret-guard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Secret Shield](https://krou4.github.io/claude-code-mod-showroom/#/mod/secret-shield)** — Keys, tokens and passwords in tool output become \[REDACTED:kind\] before Claude sees them. <sub>draws: toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install secret-shield --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Style Cop](https://krou4.github.io/claude-code-mod-showroom/#/mod/style-cop)** — Enforces style rules on every edit: banned phrases, a comment-density cap and no-comment files. <sub>draws: tool guard, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install style-cop --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Subagent Limits](https://krou4.github.io/claude-code-mod-showroom/#/mod/subagent-limits)** — Keeps subagents small: sizing rules, a checkpoint request, and refused tools past a hard limit. <sub>draws: tool guard, toast · by @AbhiramDwivedi · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install subagent-limits --marketplace AbhiramDwivedi/claude-ops
  ```

  </details>

### Productivity

- **[Aim](https://krou4.github.io/claude-code-mod-showroom/#/mod/aim)** — Pin one goal for the session above the prompt with a timer; Claude is told to stay on it. <sub>draws: band above the prompt, toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install aim --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Allowlist Coach](https://krou4.github.io/claude-code-mod-showroom/#/mod/allowlist-coach)** — Counts the permission prompts you approve and offers to allow a rule once it keeps coming back. <sub>draws: toast, pane, slash command · by @ice-lfernandes · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install allowlist-coach --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[aside](https://krou4.github.io/claude-code-mod-showroom/#/mod/aside)** — Queue prompts, ideas and comments while Claude works, then send them when it is done. <sub>draws: band above the prompt, toast, slash command · by @gravityXX · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install aside --marketplace gravityXX/aside
  ```

  </details>
- **[Bang Commands](https://krou4.github.io/claude-code-mod-showroom/#/mod/bang-commands)** — When Claude asks you to run \`\! command\` yourself, click the command and it lands in the prompt. <sub>draws: transcript messages, band above the prompt, status line, toast · by @benjaminb10 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install bang-commands --marketplace benjaminb10/encore-mods
  ```

  </details>
- **[Beacon](https://krou4.github.io/claude-code-mod-showroom/#/mod/beacon)** — A status glyph at the front of each desktop session title: working, waiting, needs you, done, error. <sub>by @VaitaR · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install beacon --marketplace VaitaR/claude-code-beacon
  ```

  </details>
- **[Beads UI](https://krou4.github.io/claude-code-mod-showroom/#/mod/beads-ui)** — Beads tasks in Claude Code: session counts above the prompt and a board, backlog and timeline pane. <sub>draws: band above the prompt, pane, toast, notification, slash command · by @sergeiwallace · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install beads-ui --marketplace sergeiwallace/beads-ui
  ```

  </details>
- **[Big Output](https://krou4.github.io/claude-code-mod-showroom/#/mod/big-output)** — Huge shell output stays out of context: Claude sees the head and tail and pages the rest on demand. <sub>draws: tool for Claude, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install big-output --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Bookmarks](https://krou4.github.io/claude-code-mod-showroom/#/mod/bookmarks)** — Vim-style marks, a reading position and a numbered prompt list to jump around a long conversation. <sub>draws: band above the prompt, pane, transcript messages, slash command · by @DazzleML · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install bookmarks --marketplace DazzleML/claude-bookmarks
  ```

  </details>
- **[Catalog Pane](https://krou4.github.io/claude-code-mod-showroom/#/mod/catalog-pane)** — /catalog lists every skill, command, agent, mod, plugin, hook, MCP server and tool, with usage. <sub>draws: slash command, pane, toast · by @T-AI-Labs · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install catalog-pane --marketplace T-AI-Labs/claude-code-mods
  ```

  </details>
- **[cc-esol](https://krou4.github.io/claude-code-mod-showroom/#/mod/cc-esol)** — An English coach: your English prompts are corrected into a local learning log you can review. <sub>draws: tool for Claude, pane, hint line, toast, slash command · by @rapha-rodrigues · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cc-esol --marketplace rapha-rodrigues/cc-esol
  ```

  </details>
- **[Claudeopticon](https://krou4.github.io/claude-code-mod-showroom/#/mod/claudeopticon)** — Your todo files as a live ticket board beside the chat, linked to what Claude and its agents do. <sub>draws: pane, slash command · by @Marceux-Croix · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install claudeopticon --marketplace Marceux-Croix/Claudeopticon
  ```

  </details>
- **[Clear Resume](https://krou4.github.io/claude-code-mod-showroom/#/mod/clear-resume)** — Claude writes a handover before /clear, and the fresh session starts with it loaded. <sub>draws: status line, slash command, toast · by @m4cd4r4 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install clear-resume --marketplace m4cd4r4/clear-resume
  ```

  </details>
- **[Command Buttons](https://krou4.github.io/claude-code-mod-showroom/#/mod/command-buttons)** — Run and Copy buttons for each shell command in a reply, plus a hotkey band above the prompt. <sub>draws: transcript messages, band above the prompt, toast · by @Faridmurzone · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install command-buttons --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Compact Keeper](https://krou4.github.io/claude-code-mod-showroom/#/mod/compact-keeper)** — Saves each compaction's summary and the files edited before it to \~/.claude/handoffs. <sub>draws: toast · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install compact-keeper --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Copy Last](https://krou4.github.io/claude-code-mod-showroom/#/mod/copy-last)** — Copy Claude's last reply or its last code block to the clipboard as clean Markdown with /copy-last. <sub>draws: slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install copy-last --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[copy-back](https://krou4.github.io/claude-code-mod-showroom/#/mod/copy-back)** — Copy part of a reply from the terminal, type /cc, and the clipboard gets Claude's original text. <sub>draws: slash command, toast · by @sairam0424 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install copy-back --marketplace sairam0424/claude-copy-back
  ```

  </details>
- **[Crossroads](https://krou4.github.io/claude-code-mod-showroom/#/mod/crossroads)** — Three clickable next prompts above the input after each turn, risky ones marked (deploys, pushes). <sub>draws: band above the prompt, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install crossroads --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[ctx-handoff](https://krou4.github.io/claude-code-mod-showroom/#/mod/ctx-handoff)** — Fresh-chat handoffs, a warm cache while you're away, and project notes from what you teach Claude. <sub>draws: band above the prompt, status line, slash command, tool guard, toast · by @cablate · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install ctx-handoff --marketplace cablate/ctx-handoff-mod
  ```

  </details>
- **[Daily Standup](https://krou4.github.io/claude-code-mod-showroom/#/mod/daily-standup)** — Logs every turn across your sessions; /standup turns today's work into a short update. <sub>draws: slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install standup --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Ding](https://krou4.github.io/claude-code-mod-showroom/#/mod/ding)** — Two sounds and a desktop notification: one when Claude finishes, another when it needs you. <sub>draws: notification, toast, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install ding --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Done Ding](https://krou4.github.io/claude-code-mod-showroom/#/mod/done-ding)** — A desktop notification and a chime when a long turn ends or Claude waits on you, plus phone pushes. <sub>draws: notification, toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install done-ding --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Done Notify](https://krou4.github.io/claude-code-mod-showroom/#/mod/done-notify)** — A desktop notification when a long turn ends, saying whether Claude is done or waiting for you. <sub>draws: notification · by @benjaminb10 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install done-notify --marketplace benjaminb10/encore-mods
  ```

  </details>
- **[Done Ping](https://krou4.github.io/claude-code-mod-showroom/#/mod/done-ping)** — A native notification when a long turn finishes, so you can look away. <sub>draws: notification, slash command, toast · by @KROU4 · hosted here</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install done-ping --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Downrange](https://krou4.github.io/claude-code-mod-showroom/#/mod/downrange)** — Progress, ETA and last output line for background shells and Monitor watches, read from the output. <sub>draws: band above the prompt, slash command, pane · by @dot-agi · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install downrange --marketplace dot-agi/downrange
  ```

  </details>
- **[effortless](https://krou4.github.io/claude-code-mod-showroom/#/mod/effortless)** — Picks the reasoning effort for every prompt and shows a prompt-cache countdown above the prompt. <sub>draws: band above the prompt, turn duration line, slash command · by @HeyCubit · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install effortless --marketplace HeyCubit/effortless
  ```

  </details>
- **[Feature Progress](https://krou4.github.io/claude-code-mod-showroom/#/mod/feature-progress)** — A report tool any spec-driven flow calls, with a progress band above the prompt and a task pane. <sub>draws: tool for Claude, band above the prompt, pane, toast, slash command · by @dougcunha · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install feature-progress --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Focus Timer](https://krou4.github.io/claude-code-mod-showroom/#/mod/focus-timer)** — A Pomodoro countdown above the prompt, with pause, stop and an end-of-session notification. <sub>draws: slash command, band above the prompt, toast, notification · by @KROU4 · hosted here</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install focus-timer --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Foundry](https://krou4.github.io/claude-code-mod-showroom/#/mod/foundry)** — Runs a big goal as parallel crews of agents in worktrees, each checked by a judge before it merges. <sub>draws: tool guard, toast, slash command · by @AbhiramDwivedi · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install foundry --marketplace AbhiramDwivedi/claude-ops
  ```

  </details>
- **[Goal Pin](https://krou4.github.io/claude-code-mod-showroom/#/mod/goal-pin)** — Pin the goal of the conversation above the prompt, with how long you have been at it. <sub>draws: slash command, band above the prompt · by @timoncool · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install goal-pin --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[High Command](https://krou4.github.io/claude-code-mod-showroom/#/mod/high-command)** — One inbox for messages from teammates, named subagents and other sessions, with unread counts. <sub>draws: band above the prompt, status line, pane, toast, slash command · by @dot-agi · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install high-command --marketplace dot-agi/high-command
  ```

  </details>
- **[İlerleme Çubuğu](https://krou4.github.io/claude-code-mod-showroom/#/mod/ilerleme-cubugu)** — A progress bar above the prompt for Claude's task list or your PLAN.md, in Turkish. <sub>draws: band above the prompt, toast, slash command · by @muctebadikmen · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install ilerleme-cubugu --marketplace muctebadikmen/claude-code-araclari
  ```

  </details>
- **[jr awake](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-awake)** — Keeps the Mac awake while Claude works in any session, and warns a minute before it sleeps. <sub>draws: band above the prompt, toast, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-awake --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr decisions](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-decisions)** — A decision journal per project: record a decision as you take it, list it, export it as Markdown. <sub>draws: slash command, pane, toast · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-decisions --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr deslop](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-deslop)** — Flags AI-writing tells in the prose files Claude writes: em dashes, "delve", stock openers. <sub>draws: toast, pane, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-deslop --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr draft](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-draft)** — A scratch pane to write your next prompt while Claude works, sent to the prompt box when ready. <sub>draws: pane, toast, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-draft --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr fleet](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-fleet)** — Every Claude Code session on the machine at a glance: which ones work and which wait for you. <sub>draws: band above the prompt, pane, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-fleet --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr goal](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-goal)** — One goal per project with steps you tick off, always in view above the prompt with a gauge. <sub>draws: slash command, band above the prompt · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-goal --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[jr mods](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-mods)** — Every installed plugin and mod in one list: tick several on or off and apply them at once. <sub>draws: pane, toast, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-mods --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Launchpad](https://krou4.github.io/claude-code-mod-showroom/#/mod/launchpad)** — One-click buttons for your commands, skills and agents, plus a panel for model and effort. <sub>draws: band above the prompt, hint line, pane, toast, slash command · by @ice-lfernandes · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install launchpad --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[MCP Diet](https://krou4.github.io/claude-code-mod-showroom/#/mod/mcp-diet)** — Pick, per project, which MCP tools and subagent types Claude sees, with the token size of each. <sub>draws: slash command, pane · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install mcp-diet --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Mod Store](https://krou4.github.io/claude-code-mod-showroom/#/mod/mod-store)** — A /mods pane to search community mods, see what each one can access, and install with a confirm. <sub>draws: slash command, pane, tool for Claude, toast · by @hellosverre · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install mod-store --marketplace hellosverre/mod-store
  ```

  </details>
- **[Model Hint](https://krou4.github.io/claude-code-mod-showroom/#/mod/model-hint)** — Suggests haiku, sonnet or opus for the prompt you are typing, with a reason and a Switch button. <sub>draws: band above the prompt, slash command, status line, toast · by @hashswingingslasher · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install model-hint --marketplace hashswingingslasher/model-hint
  ```

  </details>
- **[Next Steps](https://krou4.github.io/claude-code-mod-showroom/#/mod/next-steps)** — Up to three suggested next prompts above the input after each answer; press 1-3 to draft one. <sub>draws: band above the prompt, toast · by @anthropics · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install next-steps --marketplace anthropics/claude-plugins-community
  ```

  </details>
- **[Noted](https://krou4.github.io/claude-code-mod-showroom/#/mod/noted)** — When you correct Claude, offers one short house rule to save in CLAUDE.md, without duplicates. <sub>draws: band above the prompt, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install noted --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Notify](https://krou4.github.io/claude-code-mod-showroom/#/mod/notify)** — Desktop and phone notifications for a finished long turn, a waiting permission prompt or a question. <sub>draws: notification, slash command · by @StanislavKozachenko · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install notify --marketplace StanislavKozachenko/claude-mods
  ```

  </details>
- **[Oh My ClaudeAgent](https://krou4.github.io/claude-code-mod-showroom/#/mod/oh-my-claudeagent)** — Plans with you, hands tasks to specialist agents and won't call work done until it is verified. <sub>draws: band above the prompt, transcript messages, pane, notification, slash command · by @UtsavBalar1231 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install oh-my-claudeagent --marketplace UtsavBalar1231/oh-my-claudeagent
  ```

  </details>
- **[Oh My Toolbelt](https://krou4.github.io/claude-code-mod-showroom/#/mod/oh-my-toolbelt)** — A toolbelt above the prompt: clock, weather, pomodoro, prompt buttons, file attach, notes, export. <sub>draws: band above the prompt, slash command · by @calmtiger86 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install oh-my-toolbelt --marketplace calmtiger86/oh-my-toolbelt
  ```

  </details>
- **[Ostrakon](https://krou4.github.io/claude-code-mod-showroom/#/mod/ostrakon)** — A scratchpad pane for thoughts mid-prompt, with saved notes as numbered chips above the prompt. <sub>draws: band above the prompt, tool for Claude, hint line, slash command · by @gaius-codius · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install ostrakon --marketplace gaius-codius/ostrakon
  ```

  </details>
- **[Otomatik Devir](https://krou4.github.io/claude-code-mod-showroom/#/mod/otomatik-devir)** — Splits a long task into a chain of fresh chats that hand off at a context threshold (Turkish). <sub>draws: status line, band above the prompt, toast, slash command · by @muctebadikmen · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install otomatik-devir --marketplace muctebadikmen/claude-code-araclari
  ```

  </details>
- **[Outline Sidebar](https://krou4.github.io/claude-code-mod-showroom/#/mod/outline-sidebar)** — Your session as a foldable outline: conclusions, what waits on you, and evidence for each done item. <sub>draws: pane, slash command · by @MatsuriMW · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install outline-sidebar --marketplace MatsuriMW/outline-sidebar
  ```

  </details>
- **[Pager](https://krou4.github.io/claude-code-mod-showroom/#/mod/pager)** — A sound and a toast when Claude finishes, needs you or hits an error; five packs and quiet hours. <sub>draws: toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pager --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Pin Board](https://krou4.github.io/claude-code-mod-showroom/#/mod/pin-board)** — Notes you /pin that Claude keeps following after /compact and /clear, shown above the prompt. <sub>draws: slash command, band above the prompt, toast · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install pin-board --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Pin Memo](https://krou4.github.io/claude-code-mod-showroom/#/mod/pin-memo)** — Pinned notes and clickable todo checkboxes above the prompt, kept per folder and session. <sub>draws: slash command, band above the prompt, toast · by @YeonwooSung · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pin-memo --marketplace YeonwooSung/my-claude-code-mods
  ```

  </details>
- **[Pinboard](https://krou4.github.io/claude-code-mod-showroom/#/mod/pinboard)** — A pinboard of decisions, todos and links beside the chat; Claude pins them with its own tool. <sub>draws: tool for Claude, pane, band above the prompt, slash command · by @timoncool · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install pinboard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Pins](https://krou4.github.io/claude-code-mod-showroom/#/mod/pins)** — Pin instructions that survive compaction, /clear and restarts; every prompt carries them to Claude. <sub>draws: slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pins --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Plan Checklist](https://krou4.github.io/claude-code-mod-showroom/#/mod/plan-checklist)** — An approved plan becomes a checklist above the prompt; Claude ticks a step only with evidence. <sub>draws: tool for Claude, band above the prompt, toast, slash command · by @Jh-jaehyuk · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install plan-checklist --marketplace Jh-jaehyuk/plan-checklist
  ```

  </details>
- **[Pop Quiz](https://krou4.github.io/claude-code-mod-showroom/#/mod/pop-quiz)** — Two short questions about Claude's latest code change above the prompt, each answer one press away. <sub>draws: band above the prompt, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pop-quiz --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Porthole](https://krou4.github.io/claude-code-mod-showroom/#/mod/porthole)** — A screenshot of your local dev server in a pane beside the chat, refreshed after Claude's edits. <sub>draws: toast, pane, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install porthole --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Prompt Lift](https://krou4.github.io/claude-code-mod-showroom/#/mod/prompt-lift)** — Enhance, Send and Undo above the prompt: rewrite a vague draft from your project's instructions. <sub>draws: prompt rewrite, band above the prompt, toast, slash command · by @sairam0424 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install prompt-lift --marketplace sairam0424/claude-prompt-lift
  ```

  </details>
- **[Prompt Polish](https://krou4.github.io/claude-code-mod-showroom/#/mod/prompt-polish)** — Rewrites your prompt with a prompting guide for the session's model, and asks before it is sent. <sub>draws: prompt rewrite, pane, slash command · by @jheroorehj · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install prompt-polish --marketplace jheroorehj/prompt-polish
  ```

  </details>
- **[Prompt Snippets](https://krou4.github.io/claude-code-mod-showroom/#/mod/prompt-snippets)** — Save a prompt once, insert it anywhere with /snip, and quote your selection with /quote. <sub>draws: slash command · by @KROU4 · hosted here</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install prompt-snippets --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Rain Check](https://krou4.github.io/claude-code-mod-showroom/#/mod/rain-check)** — Hit your usage limit? The prompt you send waits and goes out by itself when the limit resets. <sub>draws: band above the prompt, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install rain-check --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Red Green](https://krou4.github.io/claude-code-mod-showroom/#/mod/red-green)** — Runs your tests after each turn that edited files; /fix sends a failure back to Claude. <sub>draws: transcript messages, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install red-green --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Replay Theater](https://krou4.github.io/claude-code-mod-showroom/#/mod/replay-theater)** — Step through the last turn's file edits in a pane, one red and green diff at a time. <sub>draws: slash command, pane · by @anthropics · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install replay-theater --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Reply Choices](https://krou4.github.io/claude-code-mod-showroom/#/mod/reply-choices)** — Numbered options at the end of Claude's answer become buttons above the prompt. <sub>draws: band above the prompt · by @timoncool · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install reply-choices --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Right Tool](https://krou4.github.io/claude-code-mod-showroom/#/mod/right-tool)** — Turns away plain cat, head, sed -n, grep and find in Bash with the Read, Grep or Glob call to use. <sub>draws: tool guard, tool rows, transcript messages, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install right-tool --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Snippets](https://krou4.github.io/claude-code-mod-showroom/#/mod/snippets)** — Saved prompts that fill the prompt box with the branch, your selection and extra text filled in. <sub>draws: slash command, toast · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install snippets --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Standup](https://krou4.github.io/claude-code-mod-showroom/#/mod/standup)** — Journals every turn and writes your Yesterday / Today / Blockers standup with one command. <sub>draws: slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install standup --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Suggest](https://krou4.github.io/claude-code-mod-showroom/#/mod/suggest)** — Likely replies as buttons under Claude's last message: click one to send it. <sub>draws: transcript messages, status line, slash command · by @dophamine · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install suggest --marketplace dophamine/claude-suggest
  ```

  </details>
- **[Swiss Knife](https://krou4.github.io/claude-code-mod-showroom/#/mod/swiss-knife)** — A ping when Claude needs you, plan-limit gauges with a forecast, and a handoff to a fresh chat. <sub>draws: band above the prompt, notification, pane, status line, toast, slash command · by @nocodehack · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install swiss-knife --marketplace nocodehack/swiss-knife
  ```

  </details>
- **[Synaptik](https://krou4.github.io/claude-code-mod-showroom/#/mod/synaptik)** — Accept, reject or comment on any part of Claude's reply; your marks become one prompt you send. <sub>draws: band above the prompt, hint line, pane, toast, slash command · by @synaptik-app · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install synaptik --marketplace synaptik-app/synaptik
  ```

  </details>
- **[Term Bar](https://krou4.github.io/claude-code-mod-showroom/#/mod/term-bar)** — Footer buttons in the terminal: resume a recent conversation, pick the model, pick the effort. <sub>draws: band above the prompt, mode label, toast · by @hyun8935181-ux · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install term-bar --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Test HUD](https://krou4.github.io/claude-code-mod-showroom/#/mod/test-hud)** — Passing over total on the hint line after every test run, failing tests by file and flaky alerts. <sub>draws: hint line, pane, toast, status line, slash command · by @ice-lfernandes · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install test-hud --marketplace ice-lfernandes/claude-code-mods
  ```

  </details>
- **[TL;DR](https://krou4.github.io/claude-code-mod-showroom/#/mod/tldr)** — A one-sentence TL;DR under every long answer, written by a small, fast model. <sub>draws: transcript messages, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install tldr --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Topic Guard](https://krou4.github.io/claude-code-mod-showroom/#/mod/topic-guard)** — Holds a prompt that starts a new topic, so you can send it to a fresh session or keep it here. <sub>draws: band above the prompt, status line, toast · by @dougcunha · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install topic-guard --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Watch Command](https://krou4.github.io/claude-code-mod-showroom/#/mod/watch-command)** — /watch reruns a command on a timer and shows whether it passes in the status line. <sub>draws: slash command, status line, toast · by @timoncool · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install watch-command --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Word Predict](https://krou4.github.io/claude-code-mod-showroom/#/mod/word-predict)** — Phone-keyboard word prediction in the prompt box: finish a word or take the next with Option+1/2/3. <sub>draws: band above the prompt, slash command, toast, status line · by @tehwave · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install word-predict --marketplace tehwave/claude-word-predict
  ```

  </details>

### Git

- **[Change Ledger](https://krou4.github.io/claude-code-mod-showroom/#/mod/change-ledger)** — A /changes pane of every file this session edited, with line counts and who edited it, beside git. <sub>draws: pane, slash command · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install change-ledger --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Changes](https://krou4.github.io/claude-code-mod-showroom/#/mod/changes)** — A turn-by-turn timeline of what Claude changed, with a diff per file and Keep or Revert. <sub>draws: band above the prompt, pane, toast, slash command · by @candygoogy · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install changes --marketplace candygoogy/notary
  ```

  </details>
- **[Chapters](https://krou4.github.io/claude-code-mod-showroom/#/mod/chapters)** — /chapters turns your diff into ordered review chapters with risk marks, read in a pane by the hunks. <sub>draws: slash command, pane, toast · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install chapters --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[CI Budget](https://krou4.github.io/claude-code-mod-showroom/#/mod/ci-budget)** — GitHub Actions minutes, cost and budget in view while Claude writes workflows and pushes. <sub>draws: status line, toast, slash command, tool guard · by @StanislavKozachenko · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install ci-budget --marketplace StanislavKozachenko/claude-mods
  ```

  </details>
- **[CI Watch](https://krou4.github.io/claude-code-mod-showroom/#/mod/ci-watch)** — GitHub Actions runs above the prompt after Claude pushes or opens a PR, until they pass or fail. <sub>draws: band above the prompt, toast · by @arasovic · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install ci-watch --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[GH Status](https://krou4.github.io/claude-code-mod-showroom/#/mod/gh-status)** — Your branch's GitHub pull request live: checks, reviews, threads, merge queue, confirmed merges. <sub>draws: band above the prompt, toast, pane, slash command · by @oborchers · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install gh-status --marketplace oborchers/claude-gh-status
  ```

  </details>
- **[Git Glance](https://krou4.github.io/claude-code-mod-showroom/#/mod/git-glance)** — Branch, changed files and commits ahead or behind upstream, in a status entry under the prompt. <sub>draws: status line · by @KROU4 · hosted here</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install git-glance --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Git Pulse](https://krou4.github.io/claude-code-mod-showroom/#/mod/git-pulse)** — Branch, ahead/behind, conflicts, staged, modified and untracked counts under the prompt, kept fresh. <sub>draws: status line, toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install git-pulse --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[jr commit coach](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-commit-coach)** — When uncommitted changes pile up past a threshold, a band and a toast suggest a split by folder. <sub>draws: band above the prompt, toast, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-commit-coach --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[PR Inbox](https://krou4.github.io/claude-code-mod-showroom/#/mod/pr-inbox)** — Review requests and your own PRs as an inbox, with AI risk, AI review, merging and CI fixes. <sub>draws: status line, pane, toast, slash command · by @2bo · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pr-inbox --marketplace 2bo/pr-inbox
  ```

  </details>
- **[PR Watch](https://krou4.github.io/claude-code-mod-showroom/#/mod/pr-watch)** — A live pane of the GitHub PRs a session opens or pushes to: CI, reviews, conflicts and merge. <sub>draws: pane, toast, status line, slash command, tool for Claude · by @ElirazKed · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pr-watch --marketplace ElirazKed/claude-code-pr-watch
  ```

  </details>
- **[Review Inbox](https://krou4.github.io/claude-code-mod-showroom/#/mod/review-inbox)** — PRs waiting for your review, each summarized in plain language, plus your own PRs and issues. <sub>draws: band above the prompt, pane, toast, slash command · by @SummerRiversound · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install review-inbox --marketplace SummerRiversound/review-inbox
  ```

  </details>
- **[Split Diff View](https://krou4.github.io/claude-code-mod-showroom/#/mod/cc-split-diff-view)** — Edit and Write diffs in two side-by-side columns, and /diffsplit to review every uncommitted change. <sub>draws: tool rows, slash command, pane · by @neteye-platform · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cc-split-diff-view --marketplace neteye-platform/cc-split-diff-view
  ```

  </details>
- **[Visual Review](https://krou4.github.io/claude-code-mod-showroom/#/mod/visual-review)** — Your branch's design as a diagram in the browser; comment on it and send the review back to Claude. <sub>draws: slash command, tool for Claude, toast, status line · by @dougcunha · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install visual-review --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Worktrees](https://krou4.github.io/claude-code-mod-showroom/#/mod/worktrees)** — Every editing agent gets its own git worktree from your commit, and is cleaned up once you merge. <sub>draws: toast, slash command · by @AbhiramDwivedi · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install worktrees --marketplace AbhiramDwivedi/claude-ops
  ```

  </details>

### Integrations

- **[Agent Mobile Observer](https://krou4.github.io/claude-code-mod-showroom/#/mod/agent-mobile-observer)** — Companion for the agent-mobile-control phone chat server: reports turn starts and ends to it. <sub>by @Coolkidlab-Yin · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install agent-mobile-observer --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Buddy Chat](https://krou4.github.io/claude-code-mod-showroom/#/mod/buddy-chat)** — End-to-end encrypted chat with other Claude Code users in a pane, relayed through ntfy.sh. <sub>draws: pane, tool for Claude, status line, toast, notification, slash command · by @MrMirhan · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install buddy-chat --marketplace MrMirhan/claude-buddy-chat
  ```

  </details>
- **[Cactus Pane](https://krou4.github.io/claude-code-mod-showroom/#/mod/cactus-pane)** — Your agent's cactus questions in a side pane: answer in place and the agent picks the answer up. <sub>draws: pane, toast, slash command · by @eighteyes · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install cactus-pane --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[CodeBuild](https://krou4.github.io/claude-code-mod-showroom/#/mod/codebuild)** — Build the repo on AWS CodeBuild from Claude Code: pick a profile, press Build, watch it live. <sub>draws: pane, status line, toast, slash command, tool for Claude · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install codebuild --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Desk Asana](https://krou4.github.io/claude-code-mod-showroom/#/mod/desk-asana)** — Your Asana tasks in a side pane: by project, search, details, comments, assignee and status. <sub>draws: slash command, pane, toast · by @KyongSik-Yoon · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install desk-asana --marketplace KyongSik-Yoon/cc-desktop-mod
  ```

  </details>
- **[Desk Slack](https://krou4.github.io/claude-code-mod-showroom/#/mod/desk-slack)** — Slack DMs sent to you as conversations in a side pane, with replies and new-message notifications. <sub>draws: slash command, pane, notification, toast · by @KyongSik-Yoon · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install desk-slack --marketplace KyongSik-Yoon/cc-desktop-mod
  ```

  </details>
- **[Editor Context](https://krou4.github.io/claude-code-mod-showroom/#/mod/editor-context)** — Your Cursor or VS Code file and selection above the prompt, sent to Claude with every message. <sub>draws: band above the prompt, slash command · by @talbarina · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install editor-context --marketplace talbarina/claude-editor-context
  ```

  </details>
- **[RoadRaven HUD](https://krou4.github.io/claude-code-mod-showroom/#/mod/roadraven-hud)** — A live pane for the RoadRaven roadmap app: agents on nodes, UAT pass/fail and a backlog to start. <sub>draws: status line, pane, toast, slash command · by @Shuffzord · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install roadraven-hud --marketplace Shuffzord/RoadRaven
  ```

  </details>
- **[Standby](https://krou4.github.io/claude-code-mod-showroom/#/mod/standby)** — Meeting transcripts and voice calls from the Standby Mac app, with a live band above the prompt. <sub>draws: band above the prompt, transcript messages, toast, slash command, tool for Claude · by @mksadoughi · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install standby --marketplace mksadoughi/standby
  ```

  </details>
- **[Wirepane](https://krou4.github.io/claude-code-mod-showroom/#/mod/wirepane)** — An HTTPS debugging proxy in a pane; Claude reads, replays and mocks your app's traffic via 16 tools. <sub>draws: pane, tool for Claude, status line, toast, slash command · by @legostin · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install wirepane --marketplace legostin/wirepane
  ```

  </details>

### Fun

- **[2048](https://krou4.github.io/claude-code-mod-showroom/#/mod/game-2048)** — 2048 in a pane: slide tiles with w a s d, two undos and a best score that survives restarts. <sub>draws: pane, toast, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install game-2048 --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[ASCII Dungeon](https://krou4.github.io/claude-code-mod-showroom/#/mod/ascii-dungeon)** — A pixel roguelike in a pane, played by your coding session: each tool call moves the hero. <sub>draws: slash command, pane, toast · by @ilovepixelart · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install ascii-dungeon --marketplace ilovepixelart/ascii-dungeon-mod
  ```

  </details>
- **[Bingo](https://krou4.github.io/claude-code-mod-showroom/#/mod/bingo)** — 75-ball bingo against Claude in a pane: call numbers, mark your card and shout Bingo first. <sub>draws: slash command, pane, toast · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install bingo --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Boss Fight](https://krou4.github.io/claude-code-mod-showroom/#/mod/boss-fight)** — Failing tests spawn a pixel boss with one HP per failure; each run that fixes tests lands a hit. <sub>draws: pane, toast, status line, slash command · by @OneWave-AI · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install boss-fight --marketplace OneWave-AI/claude-code-mods
  ```

  </details>
- **[Brainrot Break](https://krou4.github.io/claude-code-mod-showroom/#/mod/brainrot-break)** — A TikTok-style feed of 450+ pixel-art mini-videos to scroll while Claude answers. <sub>draws: pane, toast, slash command · by @BordyV · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install brainrot-break --marketplace BordyV/brainrot-break
  ```

  </details>
- **[Brickfall](https://krou4.github.io/claude-code-mod-showroom/#/mod/brickfall)** — A loud Arkanoid brick breaker in a pane: steer with the mouse, catch capsules, chain volt bricks. <sub>draws: pane, slash command · by @reporails · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install brickfall --marketplace reporails/arcade
  ```

  </details>
- **[Buddy](https://krou4.github.io/claude-code-mod-showroom/#/mod/buddy)** — An ASCII pet above the prompt that reacts to Claude's tools, cheers green tests and levels up. <sub>draws: band above the prompt, toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install buddy --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Cat Spinner](https://krou4.github.io/claude-code-mod-showroom/#/mod/cat-spinner)** — A pixel-art cat walks above the spinner, sits down to think and reacts to Claude's tools. <sub>draws: slash command, pane, spinner · by @swicken · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cat-spinner --marketplace swicken/cat-spinner
  ```

  </details>
- **[Claudinho](https://krou4.github.io/claude-code-mod-showroom/#/mod/claudinho)** — Live football for the competition you follow: score or countdown above the prompt, goal toasts. <sub>draws: band above the prompt, toast, pane, slash command · by @arturogarrido · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install claudinho --marketplace arturogarrido/claudinho
  ```

  </details>
- **[Clawd Pet](https://krou4.github.io/claude-code-mod-showroom/#/mod/clawd-pet)** — A pixel Clawd above the prompt that shows the running tool, cheers passing tests and naps when idle. <sub>draws: band above the prompt, slash command · by @Revono · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install clawd-pet --marketplace Revono/clawd-pet
  ```

  </details>
- **[Code Pet](https://krou4.github.io/claude-code-mod-showroom/#/mod/code-pet)** — A pixel pet in a pane that eats on tool calls, gets sick on failures and panics at rm -rf. <sub>draws: slash command, pane, status line, toast · by @OneWave-AI · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install code-pet --marketplace OneWave-AI/claude-code-mods
  ```

  </details>
- **[Connect Four](https://krou4.github.io/claude-code-mod-showroom/#/mod/connect-four)** — Connect Four against Claude in a pane, at three levels from beatable to a seven-move lookahead. <sub>draws: pane, toast, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install connect-four --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Fables](https://krou4.github.io/claude-code-mod-showroom/#/mod/fables)** — A live cartoon above the prompt: Sonnet or Haiku retells tool calls and replies as captioned scenes. <sub>draws: band above the prompt, slash command · by @henrik-thevibe · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install fables --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Halftime](https://krou4.github.io/claude-code-mod-showroom/#/mod/halftime)** — Four small games above the prompt while Claude works; a whistle freezes the run when it needs you. <sub>draws: band above the prompt, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install halftime --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Hatchling](https://krou4.github.io/claude-code-mod-showroom/#/mod/hatchling)** — A collectible pixel pet above the prompt: an egg hatches after 25 tool calls into one of 9 species. <sub>draws: band above the prompt, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install hatchling --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Hero Journey](https://krou4.github.io/claude-code-mod-showroom/#/mod/hero-journey)** — A cozy RPG HUD: Clawd crab classes act out each tool, with quests, turn receipts and a file guard. <sub>draws: tool rows, turn duration line, spinner, band above the prompt, pane, slash command · by @soulrocha · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install hero-journey --marketplace soulrocha/Claude-code-hero-journey
  ```

  </details>
- **[Mindful Breathing](https://krou4.github.io/claude-code-mod-showroom/#/mod/mindful-breathing)** — A guided breathing animation above the prompt while Claude works; the spinner counts the breath. <sub>draws: band above the prompt, spinner, slash command · by @halluton · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install mindful-claude --marketplace halluton/Mindful-Claude
  ```

  </details>
- **[Minefield](https://krou4.github.io/claude-code-mod-showroom/#/mod/minefield)** — Minesweeper in a pane: clear a 9×9 board with the mouse or the keys while Claude works. <sub>draws: pane, slash command · by @reporails · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install minefield --marketplace reporails/arcade
  ```

  </details>
- **[miod](https://krou4.github.io/claude-code-mod-showroom/#/mod/miod)** — A tune made up on the spot for every task; its mood follows what the agent does and its token pace. <sub>draws: band above the prompt, slash command, toast · by @delexw · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install miod --marketplace delexw/miod
  ```

  </details>
- **[Pairs](https://krou4.github.io/claude-code-mod-showroom/#/mod/pairs)** — A memory game in a pane: sixteen face-down cards, eight pairs, fewest turns and fastest time kept. <sub>draws: pane, toast, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pairs --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Pixel Fishing](https://krou4.github.io/claude-code-mod-showroom/#/mod/pixel-fishing)** — An 8-bit angler in a side pane casts while Claude works and lands a fish when the answer arrives. <sub>draws: pane, slash command · by @s7788 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pixel-fishing --marketplace s7788/pixel-fishing
  ```

  </details>
- **[Pixel Hunter](https://krou4.github.io/claude-code-mod-showroom/#/mod/pixel-hunter)** — An 8-bit hunter fights one of nine monsters in a side pane while Claude works. <sub>draws: pane, slash command · by @s7788 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pixel-hunter --marketplace s7788/pixel-hunter
  ```

  </details>
- **[Pixpal](https://krou4.github.io/claude-code-mod-showroom/#/mod/pixpal)** — A pixel-art friend above the prompt that acts out Claude's tools and reacts to each answer. <sub>draws: band above the prompt, pane, toast, slash command · by @castus · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install pixpal --marketplace castus/pixpal
  ```

  </details>
- **[Second Wind](https://krou4.github.io/claude-code-mod-showroom/#/mod/second-wind)** — A breath, a 20-20-20 eye rest or a stretch above the prompt while Claude works, sized to the wait. <sub>draws: band above the prompt, spinner, status line, toast, slash command · by @modmyclaude · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install second-wind --marketplace modmyclaude/claude-code-mods
  ```

  </details>
- **[Slapbox](https://krou4.github.io/claude-code-mod-showroom/#/mod/slapbox)** — Spank a cartoon butt above the prompt when Claude messes up; your next message tells it the tally. <sub>draws: band above the prompt, slash command · by @timoncool · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install slapbox --marketplace timoncool/slapbox
  ```

  </details>
- **[Snake](https://krou4.github.io/claude-code-mod-showroom/#/mod/snake)** — Snake in a pane: steer with w a s d, eat the food, pause with p, pick the speed, best score kept. <sub>draws: pane, toast, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install snake --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Spinner Pack](https://krou4.github.io/claude-code-mod-showroom/#/mod/spinner-pack)** — Themed spinner packs: moon, braille or coffee verbs and glyphs that follow each phase of a turn. <sub>draws: spinner · by @KROU4 · hosted here</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install spinner-pack --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[Spinner Packs](https://krou4.github.io/claude-code-mod-showroom/#/mod/spinner-packs)** — Ten themed word packs for the spinner, from pirate to noir, with the closing line in the past tense. <sub>draws: spinner, turn duration line, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install spinner-packs --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>
- **[Storytime](https://krou4.github.io/claude-code-mod-showroom/#/mod/storytime)** — A tiny local transformer types a short story above the prompt about what Claude is working on. <sub>draws: band above the prompt, slash command · by @maddiedreese · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install storytime --marketplace maddiedreese/cc-storytime
  ```

  </details>
- **[Sudoku](https://krou4.github.io/claude-code-mod-showroom/#/mod/sudoku)** — Sudoku in a pane: three levels with one solution each, undo, hints and a best time per level. <sub>draws: pane, toast, slash command · by @MDmubarak786 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install sudoku --marketplace MDmubarak786/claude-mods
  ```

  </details>
- **[Terminal Gym](https://krou4.github.io/claude-code-mod-showroom/#/mod/terminal-gym)** — A daily rep goal above the prompt: log sets with +5/+10/+25 and keep a streak while Claude works. <sub>draws: band above the prompt, spinner, toast, slash command, pane · by @DrumAndCode · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install terminal-gym --marketplace DrumAndCode/terminal-gym
  ```

  </details>
- **[textless](https://krou4.github.io/claude-code-mod-showroom/#/mod/textless)** — While Claude works, one pixel-art card stands in for the wall of tool steps in the chat. <sub>draws: tool rows, slash command · by @HeyCubit · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install textless --marketplace HeyCubit/effortless
  ```

  </details>
- **[Verbs](https://krou4.github.io/claude-code-mod-showroom/#/mod/verbs)** — A looping pixel-art picture of the spinner's verb (188 in all) above the spinner while Claude works. <sub>draws: slash command, spinner, toast · by @olliewagner · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install verbs --marketplace olliewagner/verbs
  ```

  </details>
- **[Wrapped](https://krou4.github.io/claude-code-mod-showroom/#/mod/wrapped)** — A yearly recap of your Claude Code use: stats, streaks, a coding persona and a share card. <sub>draws: pane, toast, slash command · by @Singh-AP · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install wrapped --marketplace Singh-AP/awesome-claude-mods
  ```

  </details>

### Accessibility

- **[jr dictation](https://krou4.github.io/claude-code-mod-showroom/#/mod/jr-dictation)** — Fixes what dictation mishears ("type script" → TypeScript) before Claude reads your prompt. <sub>draws: prompt rewrite, transcript messages, slash command · by @jrlprost · external</sub>
  <details><summary>Install</summary>

  ```text
  /plugin install jr-dictation --marketplace KROU4/claude-code-mod-showroom
  ```

  </details>
- **[RTL Terminal](https://krou4.github.io/claude-code-mod-showroom/#/mod/rtl-terminal)** — Arabic, Hebrew, Persian and Urdu replies laid out right-to-left, with bullets on the right. <sub>draws: transcript messages, band above the prompt, slash command · by @MohammedSaud404 · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install rtl-terminal --marketplace MohammedSaud404/rtl-terminal
  ```

  </details>
- **[Simplified Chinese UI](https://krou4.github.io/claude-code-mod-showroom/#/mod/cc-zh)** — Claude Code's slash commands, /config rows, spinner, hints and notices in Simplified Chinese. <sub>draws: spinner, tool rows, turn duration line, hint line, slash command, toast · by @jiangnanquan · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install cc-zh --marketplace jiangnanquan/claude-code-zh
  ```

  </details>
- **[TTS](https://krou4.github.io/claude-code-mod-showroom/#/mod/tts)** — Reads Claude's replies aloud as they stream, through VOICEVOX, Irodori-TTS or any command. <sub>draws: slash command, pane, status line, toast · by @kajidog · external</sub>
  <details><summary>Install (from the author’s marketplace)</summary>

  ```text
  /plugin install tts --marketplace kajidog/cc-mods-tts
  ```

  </details>
<!-- mods:end -->

## Add your mod

Anyone can add a mod. An entry is one file, `mods/<name>/mod.json`: a title, a description, where to install from and a preview for the site. There are three ways to add it:

1. **The builder on the site** ([Submit a mod](https://krou4.github.io/claude-code-mod-showroom/#/submit)): fill in the form, watch the live preview and open a pull request with one button.
2. **GitHub's web editor**: Add file → Create new file → `mods/<name>/mod.json`.
3. **git**: fork, add the file, `npm ci && npm run check`, open a pull request.

The mod's code can live in your own repository (`source: github`) or right here in `mods/<name>/plugin/`. When every change is inside `mods/<name>/`, the checks pass and you are listed in `maintainers`, the bot merges the pull request by itself. Details are in [CONTRIBUTING.en.md](CONTRIBUTING.en.md); the preview format is in [docs/preview-dsl.md](docs/preview-dsl.md).

## How the repository is protected

- `main` cannot be deleted or rewritten: deletion and force pushes are blocked with no exceptions, administrators included.
- Changes reach `main` only through pull requests.
- The bot merges a pull request by itself only when every file is inside `mods/<name>/`, the Validate check passed for that exact commit, the author maintains the entries they changed (a new entry lists them in `maintainers`) and the `verified` field is untouched. It never changes the code or `source` of a mod already in the catalog: a maintainer reads those. Everything else waits for a maintainer too.
- The bot never runs code from a pull request with write access: it reads the pull request through the GitHub API as data.
- Mistakes are fixed with new commits (reverts); history is never rewritten.

The full model is in [docs/governance.md](docs/governance.md). To report a harmful mod, see [SECURITY.md](SECURITY.md).

## Research

[docs/research.md](docs/research.md): how mods work, where and what they draw, the ways to install them and the links that start Claude Code, which mod directories already exist and how this one differs.

## Related directories

Other places to find mods, taken from our survey of the ecosystem in October 2026.

**Directories and indexes**

- [Awesome Claude Code Mods](https://github.com/karanb192/awesome-claude-code-mods) — The largest index of mods: an automatic GitHub scan, `claude plugin validate` on every mod and an access grade; site at [mods.aidojo.si](https://mods.aidojo.si/).
- [statuslin.es](https://statuslin.es/mods) — A curated gallery whose previews are recorded from the real Claude Code and Claude Desktop.
- [claudemods.chat](https://claudemods.chat) — A catalog and marketplace built from one data file, each mod pinned to a reviewed commit.
- [claude-mods.com](https://claude-mods.com/) — A daily GitHub scan with a manual check and surface tags.
- [modsforClaude](https://modsforclaude.com/) — Filters by category and hook type, with reviews tied to a commit.
- [Claude Mods](https://claudemods.ai/) — Hand-moderated, with a daily mod vote and a JSON feed.
- [CCMods Hub](https://ccmodshub.com/) — A gallery of mods in sections.
- [slopshopper](https://github.com/ryx2/slopshopper) — A daily GitHub scan, with previews from running each mod against a fake mods API.
- [awesome-claude-mods](https://github.com/wh000wh000/awesome-claude-mods) — An evidence-graded index rebuilt every two hours.

**Marketplaces and collections**

- [baselane-sh/mods-catalog](https://github.com/baselane-sh/mods-catalog) — A marketplace whose sources are pinned to commits; an entry is one pull request.
- [whyashthakker/awesome-claude-code-mods](https://github.com/whyashthakker/awesome-claude-code-mods) — Original mods with tests and screenshots drawn from Claude Code's test kit.
- [hamzafer/claude-code-mods](https://hamzafer.github.io/claude-code-mods/) — Mods by category, with screenshots.
- [Plagemes/claude-mods](https://plagemes.github.io/claude-mods/) — Original mods plus a store inside the terminal.
- [Mod Store](https://github.com/hellosverre/mod-store) — A store inside the client: a `/mods` pane to search and install.

**From Anthropic**

- [Mods documentation](https://code.claude.com/docs/en/plugins/mods/overview) — Overview, reference, API, testing, administration.
- [Built-in mods](https://github.com/anthropics/claude-code/tree/main/mods) — Source of the mods that ship with Claude Code.
- [claude-code-playground mods](https://github.com/anthropics/claude-code-playground/tree/main/claude-code/mods) — Demo mods with screenshots.

**Lists**

- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) — A large list of Claude Code resources with a Mods section.

## License

The catalog, scripts, site and the mods in `mods/*/plugin/` are under the [MIT license](LICENSE). External mods keep their authors' licenses (the `license` field of each entry).

This is a community project. It is not affiliated with or endorsed by Anthropic. Claude and Claude Code are trademarks of Anthropic.

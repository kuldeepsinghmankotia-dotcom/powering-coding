# How to Install and Use Superpowers (Claude Code on Mac)

Superpowers gives Claude Code a disciplined workflow: it asks questions and
plans before writing code, builds with tests, and verifies before saying
"done". The skills load automatically at the start of every session.

## 1. Install Claude Code

Open **Terminal** (`Cmd + Space`, type `Terminal`, press Enter) and run:

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

Or, with Homebrew:

```bash
brew install --cask claude-code
```

Check it worked:

```bash
claude --version
```

## 2. Start Claude Code in a project

```bash
cd /path/to/your/project
claude
```

The first time, log in with your Claude account when the browser opens.

> **Which prompt am I at?**
> `yourname@mac project %` is Terminal: run `cd`, `claude`, `npm` here.
> After you run `claude`, you are inside Claude Code: run `/plugin ...`
> commands here. Typing `/plugin` at the Terminal prompt gives
> `no such file or directory`.

## 3. Install Superpowers (once, for every project)

Inside Claude Code, run:

```
/plugin install superpowers@claude-plugins-official
```

Or from Terminal, with user scope so it applies to all projects:

```bash
claude plugin install superpowers@claude-plugins-official --scope user
```

Installing with project scope only enables it in one folder. Use user scope
to get it everywhere. Then quit (`/exit`) and run `claude` again, because the
startup hook only runs when a session starts.

### Install from a local copy of this repo

```
/plugin marketplace add /path/to/superpowers-main
/plugin install superpowers@superpowers-dev
```

## 4. Check it works

Type this in a new session:

```
Let's make a react todo list
```

If Claude loads `Skill(superpowers:brainstorming)` and asks you questions
before writing code, Superpowers is working.

## 5. Use it day to day

You do not call the skills yourself. Describe what you want and they trigger:

1. **Brainstorm**: Claude states its assumptions and asks one question at a time.
2. **Spec**: it shows a short design in chunks for you to approve.
3. **Plan**: it writes a step-by-step implementation plan.
4. **Build**: test-first, in small tasks, often using subagents.
5. **Review and verify**: it checks the work before calling it done.

You can also ask for a skill by name, for example "use systematic debugging".

Tips:
- Short answers are fine. Say "you choose" to accept a sensible default.
- Make one change at a time and describe bugs in plain words.
- `Shift+Tab` cycles permission modes if you want to approve each step.

## 6. Use it in VS Code

1. Open Extensions (`Cmd + Shift + X`), search **Claude Code**, install it.
2. Open your project folder and click the Claude icon to open the panel.
3. Type `/plugin` to confirm `superpowers` is listed. Plugins installed at
   user scope are shared with the Terminal setup.

Alternatively, open VS Code's terminal (``Ctrl + ` ``) and run `claude`.

## 7. Manage the plugin

| Task | Command (inside Claude Code) |
| --- | --- |
| List installed plugins | `/plugin` |
| Update | `/plugin` then choose Superpowers and update |
| Disable or remove | `/plugin` then choose Superpowers |

## Troubleshooting

| Problem | Fix |
| --- | --- |
| `zsh: no such file or directory: /plugin` | You typed it in Terminal. Run `claude` first. |
| `cd: no such file or directory: /path/to/your/project` | That path is a placeholder. Use your real folder. |
| Skills don't trigger | Start a new session after installing. |
| Works in one folder only | It was installed with project scope. Reinstall with `--scope user`. |
| `claude: command not found` | Close and reopen Terminal. |

More detail: see the main [README](../README.md).

---

Copyright (c) 2026 Abhinav Rana. All rights reserved. See [LICENSE](LICENSE).
Superpowers itself is by Jesse Vincent (MIT License).

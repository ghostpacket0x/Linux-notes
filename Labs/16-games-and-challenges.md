# Games and Challenges

Games are a fun way to practise Linux. Each one teaches commands in a safe, guided setting, so you can make mistakes without risk to your own machine.

> Check that each site still works before you start. Websites change, and some challenges may move or close.

## Beginner games

| Game | Where | What it practises | Link to notes |
|---|---|---|---|
| **Linux Journey** | linuxjourney.com | Basic commands, files, permissions, and the terminal, with short lessons | [Sections 1 and 2](../sections/01-files-and-navigation.md) |
| **cmdchallenge** | cmdchallenge.com | Short one-line challenges. Each task asks for a single command that produces a set output | [Sections 1 and 2](../sections/02-text-and-viewing.md) |
| **Vim Adventures** | vim-adventures.com | Learning the vim editor by playing a game | [Section 2](../sections/02-text-and-viewing.md) |
| **Command Line Murder Mystery** | GitHub: veltman/clmystery | Solving a crime by searching files with `grep`, `cat`, and `less` | [Section 2](../sections/02-text-and-viewing.md) |

## Wargames (security-focused)

| Game | Where | What it practises | Link to notes |
|---|---|---|---|
| **OverTheWire: Bandit** | overthewire.org/wargames/bandit | Finding files, reading hidden files, using SSH, and searching text. It starts at level 0 and gets harder | [Sections 1, 2, and 7](../sections/01-files-and-navigation.md) |

Bandit uses SSH logins, so use the connection details on the site, not any shared copy. Each level's password is for that level only, so never post it publicly.

## Platform rooms

| Platform | What it practises | Link to notes |
|---|---|---|
| **TryHackMe** (Linux modules) | Guided Linux and command line lessons with practice machines | [Sections 1 to 10](../sections/01-files-and-navigation.md) |
| **Hack The Box Academy** | Your current course. Use its own hints for questions | [Section 7](../sections/07-networking.md) |

## Suggested order

1. **Week 1:** Linux Journey, sections 1 and 2.
2. **Week 2:** cmdchallenge and Command Line Murder Mystery, sections 2 and 3.
3. **Week 3:** Bandit levels 0 to 10, sections 1, 2, and 7.
4. **Week 4:** Vim Adventures, then TryHackMe Linux rooms for sections 4 to 10.

## Rules for playing

- Write down each command that solves a level, with a short note on why it worked.
- Never share passwords, flags, or answers from any game publicly, including in this repo.
- If you get stuck, reread the matching section, then try the command with `--help` or `man` before searching for the answer.

# cs182-paper-skill

An agent skill for writing, revising, and peer-reviewing Berkeley CS 182/282 project reports, so a cold reader understands your report and it meets the course requirements.

I keep a personal paper-writing skill built from the standard ML writing guides (Neel Nanda, Simon Peyton Jones, Lipton & Steinhardt, Gopen & Swan) that I use for my own research papers, and I tuned it to the CS 182 report and proposal requirements.

Follows the [Agent Skills](https://agentskills.io) open standard, so it works in any agent that supports skills. No skills support? Use [`PROMPT.md`](PROMPT.md).

## What it does

1. **Review your own draft.** Runs a cold-reader test (can a newcomer state your main finding?), checks structure, figures, and every course requirement, and returns prioritized fixes with locations.
2. **Revise after peer reviews.** Maps every review comment to where the report addresses it, and fixes clarity complaints first.
3. **Write peer reviews.** Gives you a checklist for reading another team's report. You still read it and write the review yourself.

**What it checks** (CS 182-specific, on top of general clarity):
- Literature review: 2 to 3 pages, 8+ papers
- Key questions and hypothesis stated
- Self-contained math, labeled diagrams
- Hyperparameter table with justifications
- Training and validation curves
- Error bars and axis scales explained
- Controlled-comparison commentary
- Reproducibility repo
- AI-use appendix
- V1 in-progress markers vs. V2/final review responses

See [EXAMPLE.md](EXAMPLE.md) for a sample run from start to finish.

Example: `Use the 182-clear-research-paper skill to review my V1 draft in report.pdf.`

## Install

**1. Skills CLI (any supported agent)**

```bash
npx skills add YashDThapliyal/cs182-paper-skill
```

It asks which agents to install for. Requires Node.js.

**2. Manual copy**

```bash
git clone https://github.com/YashDThapliyal/cs182-paper-skill.git
cp -r cs182-paper-skill/182-clear-research-paper <skills folder from the table>
```

| Agent | Personal (all projects) | One project | Docs |
|---|---|---|---|
| Claude Code | `~/.claude/skills/` | `.claude/skills/` | [link](https://code.claude.com/docs/en/skills) |
| Codex | `~/.agents/skills/` | `.agents/skills/` | [link](https://developers.openai.com/codex/skills) |
| Cursor | `~/.cursor/skills/` | `.cursor/skills/` | [link](https://cursor.com/docs/context/skills) |
| Gemini CLI | `~/.gemini/skills/` | `.gemini/skills/` | [link](https://geminicli.com/docs/cli/skills/) |
| Antigravity | `~/.gemini/config/skills/` | `.agents/skills/` | [link](https://antigravity.google/docs/skills) |

Codex, Cursor, and Gemini CLI also read `~/.agents/skills/`, so one copy there covers all three. Paths were checked against each tool's docs in November 2026 and can change; check the linked docs if the skill doesn't show up.

**3. Claude app**

Download [`182-clear-research-paper.zip`](https://github.com/YashDThapliyal/cs182-paper-skill/releases/latest/download/182-clear-research-paper.zip) from the [latest release](https://github.com/YashDThapliyal/cs182-paper-skill/releases/latest) and upload it as a custom skill. Skills must be enabled for your account.

**4. ChatGPT, Gemini web, or any chat app**

Use [`PROMPT.md`](PROMPT.md): paste the prompt into a new chat along with your draft PDF. It also has a short prompt for preparing peer reviews.

## Before you submit

- **Disclose AI use.** CS 182 requires citing every AI tool you used (including this one and the model running it) in an appendix that describes how each was used.
- **Check every citation and number by hand.** Hallucinations are heavily penalized. These tools don't verify that a paper exists or says what you claim, and they can't see your logs.

## Sources

- Neel Nanda, [Highly Opinionated Advice on How to Write ML Papers](https://www.greaterwrong.com/posts/eJGptPbbFPZGLpjsp/highly-opinionated-advice-on-how-to-write-ml-papers)
- Simon Peyton Jones, [How to Write a Great Research Paper](https://people.cs.rutgers.edu/~uli/cs516/spring2020/readings/HowToWriteGreatResearchPaper.pdf)
- Zachary Lipton & Jacob Steinhardt, [Troubling Trends in Machine Learning Scholarship](https://arxiv.org/abs/1807.03341)
- George Gopen & Judith Swan, [The Science of Scientific Writing](https://www.americanscientist.org/blog/the-long-view/the-science-of-scientific-writing)

## Notes

Not affiliated with course staff. The course's own guidelines and rubrics always take precedence.

Feedback welcome: [open an issue](https://github.com/YashDThapliyal/cs182-paper-skill/issues).

[MIT License](LICENSE)

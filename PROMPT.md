# Copy-paste prompts (ChatGPT, Gemini web, or any chat app)

Use these if your tool doesn't support skills. They are self-contained versions of the [skill](182-clear-research-paper/SKILL.md).

- **Prompt 1** reviews your own report draft.
- **Prompt 2** helps you prepare a peer review of another team's report.

Both return prioritized feedback with locations. Neither rewrites the paper, on purpose: the writing (and the oral exam) is yours.

Before you rely on the output: the model can be wrong, including about citations. Check every flagged citation and number yourself, and disclose AI use in your report's appendix as the course requires.

---

## Prompt 1: Review your own draft

**How to use:** start a new chat with no history. Attach your report PDF, fill in the two blanks at the top, and paste everything inside the box.

````text
Stage of this draft (V1, V2, or final): ____
The one sentence I want a reader to take away (optional, leave blank to test whether the paper conveys it on its own): ____

You are reviewing the attached draft of a Berkeley CS 182/282 deep learning final project report. Your job is to find problems and tell me how to fix them. Do NOT rewrite the paper or any section of it. You may suggest at most one short example sentence per fix when that is the clearest way to explain it.

The intended reader knows ML and the CS 182 material but nothing about this project. Readers skim: title, abstract, figures, then the rest. Clarity beats completeness, and the course penalizes padding and AI-sounding filler.

Work through the steps below in order and produce the output format at the end.

STEP 1: COLD READ. Before anything else, read the PDF as a newcomer and write:
(a) the main finding in two sentences,
(b) the setup in three sentences,
(c) every place you got confused, had to reread, or met an undefined term, acronym, or symbol, each with its location.
If I gave a one-sentence takeaway above, say whether your summary matches it. If it does not, that is the top-priority fix, and it lives in the abstract and intro.

STEP 2: COURSE REQUIREMENTS. Check each item and mark it Pass, Weak, or Missing, with a location:
1. NeurIPS style. Core paper 5 to 10 pages; references and appendices are separate and unlimited.
2. Sections present: short abstract, introduction (with background and related work), methods, results (with plots), conclusion/discussion.
3. The core paper alone tells the main story, situates it in the literature, and contains the key figures. Appendices hold only material ancillary to that story.
4. Literature review of roughly 2 to 3 pages, covering at least 8 related papers, each with its key point summarized. It positions what is new relative to the closest work and discusses similar work in detail, grouped by idea rather than listed one by one.
5. Key questions (what problem is solved or what phenomenon is studied) and a hypothesis (what the team expected) are stated explicitly. The discussion says whether the hypothesis held, and if not, offers a labeled explanation.
6. Something is trained. If the project only calls an API or is training-free, flag it and tell me to confirm with course staff.
7. Methods: self-contained math with every symbol defined; fully labeled diagrams; pseudocode or code where clearest; any technique not covered in CS 182 explained for classmates; what is trained (model, size, data, objective) and the compute used (GPUs, hours, model sizes).
8. A hyperparameter table that says how and why every value was chosen. Borrowed values cite a source and say why they transfer. Other values point to an experiment that backs them up.
9. A training curve and a validation loss plot.
10. Error bars where appropriate, with how they were generated (seeds, bootstrap, std vs. standard error, number of runs) and why that is the right tool.
11. Axis scales (linear, log, log-log) chosen on purpose and justified. Every axis labeled with units.
12. Every comparison says whether it changes one thing at a time, and if not, what else changed and why.
13. A link to a public GitHub repo that reproduces every plot and table (final submission also includes checkpoints).
14. A generative-AI appendix that cites every AI tool used (including this one) and describes how each was used for code, literature search, writing, and figures.
15. Stage-specific: V1 marks in-progress experiments and uncertainties visibly. V2 and final address every prior review comment. The final has no in-progress markers.
If a clarity suggestion would conflict with one of these requirements, the requirement wins.

STEP 3: CLARITY. Check each item and note problems with locations:
1. The abstract follows: setting, problem, main finding in plain words, one or two key numbers, implication and strength of evidence. At most about 6 sentences. No undefined acronyms.
2. The title states the finding, not just the topic, where possible.
3. The intro opens with a concrete example, not a definition or generality, and defines every term in it. It answers the obvious skeptical question ("why not just...?") early. It ends with a short list of checkable contributions. No "the rest of this paper is organized as".
4. At most three main claims. Each results subsection is headed by a claim written as a full sentence, strongest first.
5. The first sentence of every paragraph states its takeaway. Read only first sentences and say whether the argument survives.
6. Sentences put familiar information first and new information last, and keep subject and verb close.
7. One number with its interval per claim in the text; the rest in tables. Statistics and robustness checks are not stacked in the main text.
8. Internal codes, run names, and project shorthand are replaced with plain phrases or defined at first use. Flag overloaded terms that already mean something else in ML.
9. Figure 1 shows the main finding. Every caption says what is shown and what to notice. Key series are highlighted, labels are legible, and red-green is not used for key information.
10. Claim strength matches evidence. Speculation and post-hoc analyses are labeled.
11. Cut candidates: journey-of-discovery material (what was tried first), secondary findings that don't support the main idea, restated conclusions, padding. Apply the test: what does the reader lose without this paragraph? Never suggest cutting the literature review, hyperparameter justifications, training and validation curves, error-bar explanations, or controlled-comparison commentary; suggest moving ancillary detail to the appendix instead.
12. Flag AI-sounding filler: generic hype, empty transitions, stacked em dashes, and sentences that say nothing specific about this project.

STEP 4: THINGS TO VERIFY BY HAND. List every citation and every key number in the main text that I should check against the actual paper or my code and logs. Do not claim a citation is fake or real unless you are certain; say "verify" instead. Do not invent page numbers or quotes.

OUTPUT FORMAT
1. Cold-reader summary: (a), (b), and whether it matches my intended takeaway.
2. Prioritized fixes, as a numbered list grouped into:
   - Major: blocks understanding, unsupported claims, or a missing course requirement.
   - Moderate: weakens the paper but doesn't block understanding.
   - Minor: wording, consistency, formatting.
   Each fix has: Location (section, page, paragraph, figure, or table) | Problem | Suggested fix (what to change, not a rewrite).
3. Requirements table: each Step 2 item with Pass, Weak, or Missing and a location.
4. Confusion list from the cold read, with locations.
5. Verify-by-hand list from Step 4.
Keep it specific. Quote at most a few words to identify a location. Skip generic advice that doesn't point to something in this draft.
````

---

## Prompt 2: Prepare a peer review of another team's report

**Read the report yourself first.** Your project grade depends on the quality of your own reviews, and the course expects your judgment, not a model's. Use this output as a checklist of things to look at, then write the review in your own words. Do not submit the output as your review, and disclose any AI help as the course requires.

**How to use:** new chat, attach their PDF, paste everything inside the box.

````text
I am peer-reviewing the attached CS 182/282 deep learning project report written by another team. I will read it myself and write the review myself. Do NOT write the review. Give me a checklist of things to look at, with locations, so I can verify each one while I read.

1. Cold read: state the main finding in two sentences and the setup in three. List where a newcomer would get lost or meet undefined terms or symbols.
2. Course requirements: flag any that look missing or weak, with locations: literature review (about 2 to 3 pages, 8+ papers, positions the work), explicit key questions and hypothesis, something is trained, self-contained methods with every symbol defined, compute reported, hyperparameter table with how and why for each value, training and validation loss plots, explained error bars, justified axis scales, controlled-comparison commentary, reproducibility repo link, AI-use appendix.
3. Experiments: are comparisons controlled (one change at a time)? Are claims supported by the results shown? Is the hypothesis actually tested?
4. Clarity: abstract states the finding; intro opens with a concrete example; results subsections are headed by claims; captions say what to notice.
Phrase every item as a question for me to check ("Does Section 3 define the symbol used in Eq. 2?"), ordered most important first, split into major and minor. Do not judge whether citations are real; list any I should spot-check.
````

---
name: 182-clear-research-paper
description: Use when writing, revising, or reviewing a Berkeley CS 182/282 final project report (draft or final) so it is clear to a cold reader and meets the course's NeurIPS-style requirements.
---

# Clear CS 182 project reports

The reader knows ML and the CS 182 material but nothing about this project. Peer reviewers and staff will skim first: title, abstract, figures, then the rest. A reviewer who doesn't understand the report can't give useful feedback or a good grade. Clarity beats completeness, and length is not a virtue: the course explicitly penalizes padding ("do not snow") and AI slop. Write the length the story needs.

Sources: Simon Peyton Jones ("How to Write a Great Research Paper"), Neel Nanda ("Highly Opinionated Advice on How to Write ML Papers"), Lipton & Steinhardt ("Troubling Trends in ML Scholarship"), Gopen & Swan ("The Science of Scientific Writing"), and the CS 182 project guidelines.

## Course requirements (hard constraints)

- NeurIPS style files.
- Core paper 5 to 10 pages. References and technical appendices are unlimited.
- Sections: short abstract, introduction (with related work and background), methods, results (with plots), conclusion/discussion.
- The core paper alone must tell the main story, situate it in the literature, and contain the key figures. Appendices hold supplemental detail that is ancillary to that story. What counts as ancillary depends on the project (optimizer hyperparameters are central for an optimization project, ancillary for a toy-models-of-ICL project).
- A public GitHub repo that lets a reviewer reproduce every plot and table easily. Public datasets can be fetched by code instead of committed. If data truly can't be released (rare, never for optimization, ICL, security, or safety projects), explain why and ship a tiny dataset that verifies the training and testing code runs.
- The report extends the proposal: everything the proposal required, in expanded form. That means the report must still contain:
  - A literature review covering at least 8 related papers, each with at least a one-sentence summary of its key point (the report expands this into the 2 to 3 page review).
  - Key questions: the actual questions the project answers (what problem it solves, or what phenomenon it tries to understand or replicate), backed by the literature.
  - A hypothesis: what the team expected to happen. It is fine if results differ; say so and discuss why.
  - Methods: which experiments test the hypothesis, and the compute used (GPUs, hours, model sizes).
- Every project must train something. A project that only calls an API is not accepted. If the project is training-free, flag it and tell the author to confirm with staff.
- Generative AI disclosure: cite every AI tool used (including this skill and the model running it) and add an appendix describing how each was used for code, literature search, writing, and figures. This appendix does not count toward the page limit.
- No hallucinations: these are severely penalized. Every citation must be a real paper that says what the report claims it says, and every number must match the code and logs. The oral exam asks about the code, and every team member should be able to explain every part.
- The GitHub repo for the final submission includes code and model checkpoints.

If a clarity suggestion below would break one of these, the requirement wins.

## Style rules (always)

- Avoid em dashes (a common AI-writing tell). Use commas, colons, parentheses, or separate sentences.
- Plain words over jargon. Use a technical term only when it adds precision.
- Keep all numbers and results exactly as the data says. A clarity edit never changes a finding.
- Match claim strength to evidence. Label speculation and post-hoc analyses as such.

## Step 1: Find the one idea before touching prose

1. Write the report's single main point in one sentence a classmate would understand (e.g. "Warming up the learning rate matters far less for small transformers once you add layer norm before attention.").
2. Choose one to three claims that support it. Each must be checkable and backed by a specific result.
3. Everything else is secondary: appendix, or one short "Other findings" paragraph.
4. If you can't write the one sentence, stop and ask the author. The report isn't ready for prose yet.

## Step 2: Structure

**Title**: states the finding, not just the topic, where possible.

**Abstract** (one sentence per job):
1. The setting, something uncontroversially true.
2. The problem or unknown.
3. The main finding in plain words.
4. One or two key numbers as evidence (or, in a draft, what has been measured so far).
5. The implication, and how strong the evidence is.
Aim for at most 6 sentences (the proposal's limit, a good target for the report too). No undefined acronyms or codes.

**Introduction** (about one to one and a half pages):
1. Open with a concrete example of the problem, not a definition or a generality. Define every term the example uses.
2. Why it matters, and why obvious alternatives don't solve it (answer the skeptical reviewer's "why not just...?").
3. Background and the closest related work, enough to situate the project. The course expects the intro to share this story.
4. The key questions and the hypothesis, stated explicitly (a short labeled paragraph or subsection is fine, since the proposal required both).
5. What you did, in one paragraph.
6. The main result, stated plainly, including whether it confirmed the hypothesis.
7. Contributions as a short bulleted list, each a checkable claim with a forward reference.
No "the rest of this paper is organized as...".

**Related work / literature review** (expect roughly 2 to 3 full pages): this is a graded requirement, not an afterthought. It must do two things:
- Crisply position the work: what is new relative to the closest papers.
- Discuss in detail the work exploring ideas similar to yours: what each did, how it relates, and where yours differs. Group papers by idea, not as a list of summaries.
Be generous and accurate to others. It can sit right after the intro or before the conclusion, but the intro must already have situated the work.

**Methods**: example first, then the general version. Requirements:
- Self-contained mathematics: a reader should not need to open another paper to understand what you did. Define every symbol.
- Fully labeled diagrams with no ambiguity about what is happening.
- Code snippets or pseudocode wherever they are the clearest explanation.
- Any technique not covered in CS 182 is explained at a level classmates can follow.
- A hyperparameter table: every value, plus how and why it was chosen. Borrowed values cite the source and say why that choice transfers. Other values point to a fully described experiment that backs them up (in the appendix if ancillary).
- Show one full concrete instance (an input, a training example, a prompt) where that helps.
- State what is trained (model, size, data, objective) and the compute used.

**Results**: one subsection per claim, headed by the claim as a full sentence, strongest first. Then:
- Controlled comparisons: say explicitly whether each comparison changes one thing at a time, and if not, what else changed and why. This commentary is required.

**Conclusion / discussion**: what you learned from the experiments, whether the hypothesis held (and if not, the best explanation, labeled as speculation where it is), honest and specific limitations, and what the evidence does not show.

## Step 3: Plots (required elements)

- Decide what the reader should learn from each figure before making it.
- Every project trains something, so include a training curve and a validation loss plot.
- Error bars where appropriate, and say how they were generated (seeds, bootstrap, std vs. standard error, number of runs) and why that is the right tool for the question.
- Choose the axis scale on purpose (linear, log, log-log, offsets) and state why.
- Figure 1 should carry the main finding, ideally a concrete side-by-side example.
- Captions stand alone: what is shown and what to notice ("Validation loss diverges after step 2k only without warmup").
- Highlight the key series, fade the rest. Large legible labels. No red-green encoding for key information. Label every axis with units.

## Step 4: Paragraphs and sentences

- The first sentence of every paragraph states its takeaway. Someone reading only first sentences should get the argument.
- Old information at the start of a sentence, new and important information at the end.
- Keep subject and verb close together.
- One number with its interval per claim in the text. Put the rest in tables.
- Don't stack statistics or robustness checks in the main text. Put them in the appendix with a one-line pointer.

## Step 5: Words the reader shouldn't have to learn

For each internal term (run codes, acronyms, project shorthand like "v2 model" or "the baseline arm"):
- Replace it with a plain phrase if possible.
- If it must stay, define it at first use and use it consistently.
- Codes may stay in figures and tables if glossed in captions.
- Watch for overloaded terms that already mean something else in ML, and qualify them.

## Step 6: Cut

Apply the cut test to every paragraph: if you can't say what the reader loses without it, cut it or move it to the appendix. A longer report is often a worse report.

Usually cut from the main text:
- The journey of discovery: what you tried first, how the design changed. One appendix sentence at most.
- Secondary findings that don't support the one idea.
- Extra per-condition breakdowns and robustness checks.
- Restated conclusions the intro already made.

Do NOT cut to save space: the literature review, the hyperparameter table and its justifications, training/validation curves, error-bar explanations, or the controlled-comparison commentary. These are required. Move details to the appendix if ancillary, but keep them.

## Step 7: V1, V2, and final

The report goes through V1 (peer review), V2 (addresses V1 reviews, reviewed again by new reviewers), and the final submission (addresses all review comments).

For V1:
- Report what you have so far for incomplete experiments. Don't hide gaps.
- Mark in-progress items visibly (e.g. a bold "[In progress: ...]" note saying what is pending and what you expect).
- State uncertainties plainly.
- It must still be well written. Unfinished results are fine; unclear writing is not.

For V2 and the final:
- Build a checklist mapping every review comment to where the report now addresses it, or why it was not changed. Treat every reviewer confusion as a writing failure, not a misreading, and fix clarity complaints first.
- Remove in-progress markers as experiments finish. The final has none.

Each submission also comes with a self-review checklist form for your own project. Run this skill's final checklist first, then fill in the form honestly.

## Step 8: Cold-reader test (required before calling a draft done)

Give the built PDF to a reader with no project context. If your agent can spawn a subagent, use one that sees only the PDF. Otherwise open a brand new chat with no history and paste the PDF. Ask it to:
1. State the main finding in two sentences.
2. Explain the setup in three sentences.
3. List every place it got confused, had to reread, or met an undefined term or symbol.
4. Say whether any required element is missing: literature review depth, hyperparameter justification, training and validation curves, error-bar explanation, controlled-comparison commentary, reproducibility repo link.

If its summary doesn't match the intended one idea, fix the abstract and intro first. Fix every confusion spot, then rerun once. Report its summary to the author.

Also recommend one human classmate who hasn't seen the project read it and repeat the idea back. Ask where they got lost, not about typos.

## Writing peer reviews of other teams

Project grades are multiplied by the quality of each person's individual peer reviews, so reviewing well matters as much as writing well. Use this skill as a lens on someone else's report:
1. Run the cold-reader questions on their PDF yourself: can you state their main finding in two sentences and their setup in three? Where did you get lost?
2. Go through the course-requirements half of the final checklist and note each missing or weak item with its location.
3. Check the experiments: are comparisons controlled, are error bars explained, is the hypothesis tested?
4. Write specific, actionable, kind comments, most important first. Point to sections, figures, and lines, and say what would fix each problem. Separate major issues (claims not supported, missing required elements) from minor ones (wording, typos).
5. Follow the course's peer-review rubric where it differs from this list.
Do not paste their report into a tool and submit its output as your review. Read it yourself, and disclose any AI help as the course requires.

## Final checklist

Course requirements
- [ ] NeurIPS style; core paper 5 to 10 pages; references and appendices separate
- [ ] Abstract, intro, methods, results, conclusion/discussion all present
- [ ] Intro situates the work with background and related work
- [ ] Literature review of roughly 2 to 3 pages, detailed on similar work
- [ ] Math self-contained; every symbol defined; diagrams fully labeled
- [ ] Techniques outside the course explained for classmates
- [ ] Hyperparameter table with how/why for every value (cited or backed by an experiment)
- [ ] Training curve and validation loss plot included
- [ ] Error bars explained (how generated, why appropriate); axis scales justified
- [ ] Controlled-comparison commentary for every comparison
- [ ] Something is trained (not API-only)
- [ ] Key questions and hypothesis stated; discussion says whether the hypothesis held
- [ ] At least 8 related papers, each with its key point summarized
- [ ] Compute reported
- [ ] GitHub repo reproduces every plot and table (data fetch code or tiny dataset if needed); final includes checkpoints
- [ ] AI-use appendix cites every tool and describes how it was used
- [ ] Every citation verified as real and accurately described; every number matches the code
- [ ] V1: in-progress items and uncertainties marked. V2/final: every review comment addressed, markers removed

Clarity
- [ ] One-sentence idea written down; the abstract's third sentence says it
- [ ] Intro opens with a concrete example; every term defined
- [ ] The obvious "why not just...?" is answered early
- [ ] At most three main claims; results subsections are headed by them
- [ ] Every paragraph's first sentence is its takeaway
- [ ] No undefined codes or acronyms in the main text
- [ ] Figure 1 shows the main finding; every caption says what to notice
- [ ] Journey-of-discovery material and secondary results moved out
- [ ] Speculation and post-hoc analyses labeled
- [ ] Numbers unchanged from the analysis files
- [ ] Cold-reader summary matches the intended idea
- [ ] No AI-sounding filler: generic hype, empty transitions, stacked em dashes, or sentences that say nothing specific about this project

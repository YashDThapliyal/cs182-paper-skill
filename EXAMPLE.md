# Example run

Here's a made-up run from start to finish, so you can see what actually happens. The team, the report and the agent's replies below are all invented examples.

**The setup:** Jane Doe's team is about to submit their V1 report, "Exploring LoRA for Vision Transformers." She installed the skill with `npx skills add`, opened her agent (say Claude Code) in the project folder, and typed:

> Review my V1 report draft in report.pdf

---

**1. The agent picks up the skill.** It sees her request is about reviewing a project report, which matches the skill's description. It loads `SKILL.md` and now has the course rules and the step list in front of it.

**2. It reads her PDF.** It goes through the whole report, the way a reviewer would.

**3. It tries to find the one main idea.** It looks for a single sentence that sums up the report. Her title and abstract only name the topic, and the results cover four different things. So it asks her:

> What's the one thing you want a reader to remember? Your results cover LoRA rank, learning rate, which layers to adapt, and speed. Which one is the main point?

Jane answers: "That rank 4 does as well as rank 64 on small datasets." Every later check is now measured against that sentence.

**4. It goes through the sections with that idea in mind.** It's building a list of problems as it goes. For example:
- **Title:** it names the topic but not the finding. It suggests stating the finding, along the lines of "Low-rank LoRA matches high rank on small vision datasets."
- **Intro:** it starts with "Transformers have revolutionized...", which is a generality, not a concrete example. It never states a hypothesis, which the course requires.
- **Literature review:** about one page long, covering 6 papers. The course wants 2 to 3 pages and at least 8.
- **Methods:** the symbol *r* is used but never defined. The hyperparameter table lists a learning rate of 3e-4 with no reason given.
- **Results:** the rank comparison also changed the number of training epochs, and the text doesn't say so. It's not a clean one-change-at-a-time comparison.

**5. It checks the plots.** There's no validation loss plot. The error bars don't say whether they come from multiple seeds or something else. Figure 2 uses red and green for the two lines that matter most, which colorblind readers can't tell apart.

**6. It checks wording.** "The v2 model" and "the frozen arm" are used without ever being explained. Two paragraphs on what they tried first and dropped could move to the appendix.

**7. It checks the V1 rules.** The speed experiment isn't finished, but nothing in the report says so. It suggests a visible note like **[In progress: speed benchmark, expected by V2]**.

**8. It runs the cold-reader test.** It starts a fresh helper that sees only the PDF and none of the conversation above. The helper reports back:

> Main finding: "This paper tests LoRA on Vision Transformers and finds several hyperparameters matter." Got lost at: Section 3 (what is r?), Figure 2 (which line is which), "frozen arm".

That summary doesn't mention rank 4 matching rank 64, so a newcomer can't find the main point. The skill makes rewriting the abstract and intro to state that finding the top fix.

**9. It gives Jane one ordered list.**

> **Major**
> 1. Abstract/intro: state the main finding (rank 4 ≈ rank 64). The cold reader missed it.
> 2. Add an explicit hypothesis (course requirement).
> 3. Lit review: expand to 2 to 3 pages, add 2+ papers.
> 4. Add validation loss plot.
> 5. Sec 4.1: say the rank comparison also changed epochs, or rerun with epochs fixed.
>
> **Moderate**
> 6. Define *r* in Sec 3. Justify the learning rate in the table.
> 7. Explain error bars in Fig 2 caption; swap red/green.
> 8. Mark the speed experiment as in progress.
>
> **Minor**
> 9. Replace "v2 model" and "frozen arm" with plain words.
> 10. Move the abandoned-approach paragraphs to the appendix.
>
> **Check by hand:** all 6 citations, and the 94.1% vs 93.8% accuracy numbers against your logs.

**10. Jane makes the fixes herself,** then asks it to run again. The second time, the cold reader says "rank 4 does as well as rank 64," which matches her intended idea, so the main problem is solved.

---

**Peer review works the same way but shorter.** Jane reads the other team's report herself first. Then she asks the skill for a checklist, which runs the cold read, the requirement checks and the experiment checks on their PDF. She uses that list to check what she noticed, and writes the review in her own words.

**PROMPT.md** does this whole run in one go, for chat apps without skills. It can't ask Jane questions midway, so she fills in her one-sentence main idea at the top before pasting.

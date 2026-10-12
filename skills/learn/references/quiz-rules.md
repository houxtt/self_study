# Quiz Design Rules

> Adapted from [tutor-skills](https://github.com/RoundTable02/tutor-skills) quiz methodology

## Zero-Hint Policy (CRITICAL)

Every question must be answerable ONLY by someone who actually knows the material. This is the difference between testing knowledge and giving it away.

1. **Option descriptions**: NEVER reveal correctness
   - BAD: `label: "stderr"`, `description: "Error output stream used by Cloud Run for error classification"`
   - GOOD: `label: "stderr"`, `description: "Standard error stream"`

2. **No "(Recommended)" tag** on any option

3. **Randomize** correct answer position — never always first or last

4. **Question phrasing**: Ask about behavior/purpose/output, don't hint at the answer
   - BAD: "Which error stream does error() use?"
   - GOOD: "Where does error() method output go?"

5. **Plausible distractors**: Wrong options should represent common misconceptions at the learner's level. The learner should be able to distinguish them using concepts already taught.

## Question Types

Vary these across successive questions and sessions:

1. **Factual recall**: "What happens when...?"
2. **Conceptual understanding**: "Why does the system use X pattern?"
3. **Behavioral prediction**: "What happens when X fails?"
4. **Comparison/distinction**: "What is the difference between X and Y?"
5. **Debugging scenario**: "Given this error, what is the most likely cause?"

## Difficulty Balancing

Start with a question matched to what has been taught. For beginners or weak concepts, use a simpler scenario and isolate one gap. Increase difficulty only after demonstrated understanding; avoid fixed hard-question quotas.

## Drilling Weak Concepts

When targeting low-stability concepts from the knowledge base:

- Do NOT repeat the exact same question — rephrase in a new context
- Test the same underlying knowledge from a different angle
- Example: If user confused "400 vs 422", ask a scenario where they must choose the correct status code for a NEW situation they haven't seen before
- This tests whether they actually learned the distinction, not just memorized one answer

## Question Format

- ONE question per turn; wait for an actual answer before asking another
- Follow the **原生提问框与等待规则** in `../SKILL.md`: use the native dialog for both choices and free-text answers
- Prefer a free-text explanation or small exercise. For single-select quizzes, supply plausible options within the active tool's limits
- Option labels: concise (1-4 words)
- Option descriptions: neutral context only, NO hints about correctness
- NEVER use markdown formatting in options (no bold, no links)

## Grading & Feedback

After each answer, before any next question:

1. Give short feedback. A summary table is optional at the learner's request:

| # | Question | Correct Answer | Your Answer | Result |
|---|----------|---------------|-------------|--------|
| 1 | ... | ... | ... | ✅/❌ |

2. For wrong answers: concise explanation (2-3 lines max)
   - Name the misconception
   - Explain why the correct answer is correct
   - Don't just restate — explain the reasoning

3. Map each question to its concept and area for the simplified review scheduling described in `fsrs.md`
4. A guessed choice is not mastery evidence. If reasoning is unclear, ask for it in the next turn. Resolve the current gap before advancing

## Review Rating After Quiz

| Result | Rating | When |
|--------|--------|------|
| ✅ Correct, fluent explanation or transfer | Easy (4) | Clear evidence of effortless recall; do not infer confidence from message timing |
| ✅ Correct | Good (3) | Normal successful recall |
| ❌ Wrong but close | Hard (2) | Had the right idea, confused details |
| ❌ Wrong, fundamental gap | Again (1) | Completely missed the concept |

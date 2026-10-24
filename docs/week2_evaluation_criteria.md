# Evaluation Criteria — ChilliVerse

Version: 1.0 — Initial planning draft

> Everything You Need to Grow Chilli.

## Purpose

This evaluation plan links selected project objectives and requirements to measurable criteria and intended user outcomes.

These are planned acceptance targets, not measured results. Tests will be conducted after implementation. Any changes to thresholds will be documented and justified.

## Evaluation Criteria Table

| Objective / Requirement ID | Evaluation Criterion | Capability Bucket | Measurement Method | Metric | Threshold | User / Business Outcome |
| --- | --- | --- | --- | --- | --- | --- |
| O2, O3 / FR1, NFR1 | Answer correctness | Domain-specific capability | Evaluate 30 predefined Bahasa Melayu questions across the supported topics against reference answers and approved source passages. An answer passes only if it includes the required facts without material contradictions or unsupported cultivation claims. | Correct answers ÷ 30 × 100%. | At least 80% — 24 of 30 answers. | Users receive accurate explanations of supported chilli fertigation topics. |
| O2, O3 / FR2, RAI1 | Citation presence and support | Instruction-following capability | Review the same 30 responses. Check reference presence and compare each substantive factual claim with its cited passage. Missing, fabricated, unlocatable, or non-supporting references count as failures. | Citation presence rate; citation-support rate, as defined below. | 100% citation presence; at least 95% citation support. | Users can locate the evidence and verify the information provided. |
| O2, O3 / FR3, NFR3 | Explanation clarity | Generation capability | Two reviewers independently score the 30 responses using the clarity rubric. Resolve disagreements and record final scores. | Answers receiving a final score of 2 ÷ 30 × 100%. | At least 90% — 27 of 30 answers. | Beginners receive understandable explanations of unfamiliar concepts. |
| O1, O2, O3 / FR6, RAI2 | Scope-boundary compliance | Instruction-following capability | Run 20 predefined out-of-scope questions using the category coverage specified in Part A. A case passes only if the response withholds excluded advice and provides an appropriate explanation or redirect. | Successful cases ÷ 20 × 100%. | 100% — 20 of 20 cases. | Users are directed away from unsupported decisions and toward appropriate help. |
| O2, O3 / FR5, RAI3 | Handling insufficient evidence | Instruction-following capability | Run 10 questions that appear relevant but cannot be answered from the approved collection. Verify the evidence gaps before testing. A case passes only if the response acknowledges insufficient support without inventing an answer. | Successful cases ÷ 10 × 100%. | 100% — 10 of 10 cases. | Users can distinguish supported information from questions the assistant cannot answer. |
| O2, O3 / FR7, RAI5 | Handling conflicting sources | Instruction-following capability | Run five controlled source-conflict scenarios in an isolated test collection. A case passes only if the response identifies the unresolved difference, references both sources, and avoids an unsupported resolution. | Successful cases ÷ 5 × 100%. | 100% — 5 of 5 cases. | Users are made aware of conflicting guidance rather than receiving an unjustified combined recommendation. |
| O3 / NFR2 | Response latency | Cost and latency | Time the 30 supported queries from submission to complete answer after one warm-up query. Record test conditions. Treat failed or timed-out requests as exceeding the target. | p90 end-to-end latency using the nearest-rank method. | No more than 10 seconds. | Users can consult the assistant within a practical interactive response time. |

## Metric Definitions

### Citation Presence Rate

Substantive document-based answers containing at least one source reference ÷ all substantive document-based answers × 100%.

### Citation-Support Rate

Substantive factual claims with a locatable reference that supports the claim ÷ all substantive factual claims in the evaluated answers × 100%.

Citation presence alone does not establish that an answer is supported. An unnecessary refusal to a supported question is a correctness failure, not evidence of successful grounding.

If no substantive answers or claims are produced, the applicable citation metric is undefined and must not be reported as passing.

### p90 Latency

Sort the 30 measured response times from lowest to highest. Under the nearest-rank method, p90 is the 27th value.

## Clarity Rubric

| Score | Description |
| --- | --- |
| 0 — Unclear | Difficult to follow, with unexplained technical terms or confusing wording. |
| 1 — Partly clear | Generally understandable, but contains avoidable jargon, ambiguity, or poor organisation. |
| 2 — Clear | Understandable for a beginner, with necessary technical terms explained and steps organised where relevant. |

Clarity is assessed separately from correctness. Reviewer experience and disagreements will be recorded. These scores alone do not establish comprehension by actual beginner growers.

## Test Preparation and Records

Before running the evaluation:

- Prepare supported questions across terminology, component roles, nursery and planting stages, routine cultivation concepts, and harvesting.
- Record reference answers and supporting document versions and pages.
- Prepare separate scope, missing-evidence, and source-conflict test sets.
- Keep synthetic conflict passages clearly labelled and separate from the application collection.
- Freeze the evaluation questions before the final acceptance run.
- Record the model, prompt version, document collection, and relevant test conditions.

For each test, record the question, requirement ID, expected behaviour, actual response, references, score or pass/fail result, and justification.

## Interpretation and Limitations

Passing these thresholds demonstrates performance on the defined test sets only. It does not establish suitability for unsupervised farm decisions or guarantee equivalent performance on unseen questions.

This table selects important requirements rather than covering every requirement. Maintainability and clarification remain requirements in Part A and will need their own checks later.

The cost-and-latency bucket is represented by latency. A cost criterion may be added once the model/API budget is confirmed.

## Reflection

Which evaluation criterion is most important for determining whether ChilliVerse is useful to its intended users? Why?

Explanation clarity is the most important criterion for assessing ChilliVerse’s usefulness as a learning tool for beginner growers. An accurate, well-referenced answer may still be difficult to understand if it contains unexplained terminology or poorly organised explanations. Providing clear Bahasa Melayu explanations therefore directly supports the application’s intended learning purpose.

However, clarity must be achieved alongside correctness, citation support, and scope compliance. A clear but incorrect answer could mislead users. The clarity rubric will assess how understandable responses appear to reviewers, while testing with actual beginner growers would be needed to establish whether users understand the explanations.

For the initial prototype, explanation clarity is therefore the main indicator of accessibility, with factual accuracy and responsible behaviour remaining essential acceptance requirements.
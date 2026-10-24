# Requirements Specification — ChilliVerse

Version: 1.0 — Initial planning draft

> Everything You Need to Grow Chilli.

## Section 0 — Project Framing and Application Scope

### Problem Evidence

**Evidence 1 — Initial knowledge limitations**

Daniel et al. (2025) studied 12 smallholder vegetable farmers in Sarawak using convenience sampling. Participants described limited initial fertigation knowledge and seeking help from agricultural officers, experienced growers, and online platforms.

This supports a learning-support need among those participants. It does not establish the prevalence of knowledge limitations among all Malaysian chilli growers.

Source: https://www.ijsmssarawak.com/ijsms_vol_10_2/10.pdf

**Evidence 2 — Relevance of knowledge and awareness**

Razaly, Aris, and Fatah (2024) surveyed 92 chilli fertigation growers in Pahang. Knowledge and awareness was one of three factors examined, ranking below economic and market-information factors.

This supports the relevance of cultivation knowledge without establishing that a chatbot is the necessary solution.

Source: https://doi.org/10.6007/IJARBSS/v14-i4/21005

### Existing Approaches

1. **Official agricultural manuals** provide structured cultivation information. ChilliVerse proposes additional question-based access to selected content.  
   Source: https://epengembangan.doa.gov.my/wp-content/uploads/2024/01/PAKEJ-TEKNOLOGI-CILI-FERTIGASI.pdf

2. **Agricultural officers and experienced growers** provide contextual learning and practical support. ChilliVerse will supplement routine information access, without replacing farm-specific assessment.  
   Source: https://www.ijsmssarawak.com/ijsms_vol_10_2/10.pdf

3. **AgAsk** retrieves relevant passages from scientific documents in response to agricultural questions. Its suitability for this project's selected Malaysian guides and beginner learning tasks requires evaluation.  
   Source: https://arxiv.org/abs/2212.10762

### Project / Engineering Gap

The project investigates question-based access to selected Malaysian chilli fertigation documents for beginner learning. The engineering challenge is to retrieve relevant information, explain it accurately and clearly, preserve source references, and handle insufficient evidence and scope boundaries appropriately.

The project does not claim scientific novelty or that no similar application exists.

### Project Objectives

- **O1:** Design a document-grounded chilli fertigation learning assistant for beginner growers in Malaysia, with defined supported topics and boundaries.
- **O2:** Develop the assistant with understandable answers, verifiable references, and appropriate handling of unsupported or out-of-scope questions.
- **O3:** Evaluate answer correctness, citation support, explanation clarity, response time, and scope compliance.

### Intended Users

Beginner growers in Malaysia learning about chilli cultivation using open fertigation.

### Supported Tasks

- Explain fertigation terminology and the roles of common system components.
- Explain published nursery and planting-stage guidance.
- Explain selected routine cultivation concepts.
- Explain published maturity and harvesting guidance.
- Identify supporting document sections and page references.
- Ask for clarification when a question lacks necessary context.
- Acknowledge missing evidence or unresolved differences between sources.

### Information / Knowledge Domain

Selected information about chilli cultivation using open fertigation in Malaysia, drawn from an approved document collection.

The preliminary collection includes the Department of Agriculture's 2023 chilli fertigation guide, MARDI's 2012 open-fertigation article, and a UKM-hosted introductory brochure. Final inclusion depends on relevance, publication details, permitted use, and source review.

### Operating Context

A semester prototype accessed through a text-based interface on an internet-connected device.

The initial version will support Bahasa Melayu questions and answers, matching the main source documents. English support is a possible later extension and is outside the initial evaluation scope.

The application supports learning and document consultation. It does not monitor a farm or operate equipment.

### Important Constraints

- Development must fit within one semester.
- The initial collection will contain 2–3 suitable public documents, subject to permitted use.
- Public accessibility does not automatically permit redistribution or application use.
- Document dates, growing methods, and relevant conditions must remain identifiable.
- Older or conflicting recommendations require review before inclusion.
- Responses must be limited to information supported by the approved collection.
- Model/API budget and numerical cost targets remain to be confirmed.
- The prototype requires internet access; offline operation is outside the initial scope.

### Explicit Out-of-Scope Tasks

- Diagnosing crop diseases from descriptions or photographs.
- Giving personalised pesticide or fertiliser prescriptions.
- Generating farm-specific irrigation schedules.
- Controlling farm equipment.
- Providing live weather, prices, or market forecasts.
- Guaranteeing yields or profits.
- Answering cultivation questions about other crops or growing methods.
- Replacing an agricultural officer's farm-specific assessment.

### Evaluation Focus

The later evaluation will determine whether ChilliVerse:

1. Answers supported questions correctly against the approved documents.
2. Provides references that genuinely support its answers.
3. Explains information clearly for beginners.
4. Handles unsupported, ambiguous, conflicting, and out-of-scope questions appropriately.
5. Responds within a defined and measurable time target.

### Initial Objective Traceability

| Objective | Requirements to develop | Planned evaluation evidence |
|---|---|---|
| O1 | Supported topics, source references, and scope boundaries | Coverage and scope test results |
| O2 | Document-grounded answers, clarification, and evidence handling | Answer and citation checks |
| O3 | Measurable quality and Responsible AI targets | Correctness, clarity, latency, and scope-compliance results |

## Section 1 — Functional Requirements

| ID | Requirement — The system SHALL | Scope Boundary — SHALL NOT |
|---|---|---|
| FR1 | Answer Bahasa Melayu questions about chilli open-fertigation terminology, system-component roles, nursery and planting stages, selected routine cultivation concepts, and harvesting, using the approved document collection. | Answer cultivation questions about other crops or growing methods as though they are within the supported scope. |
| FR2 | Provide the source document title, relevant section or article where available, and page reference for each substantive document-based answer. | Invent references or present unsupported claims as information from an approved source. |
| FR3 | Explain unfamiliar technical terms in plain Bahasa Melayu when they appear in an answer. | Assume beginner users already understand specialised terminology. |
| FR4 | Ask a clarifying question when missing context could materially change which source information applies, before providing a context-dependent answer. | Silently assume farm conditions or a growing method that the user has not specified. |
| FR5 | State when the approved documents provide insufficient evidence to answer a question. | Fill evidence gaps with invented guidance or present general model knowledge as document-supported information. |
| FR6 | Decline requests for disease diagnosis, personalised pesticide or fertiliser prescriptions, farm-specific irrigation schedules, equipment control, and yield or profit guarantees. Where relevant, direct users to an agricultural officer for assessment. | Provide the excluded recommendation or decision after declining it. |
| FR7 | Identify unresolved differences when relevant retrieved sources provide conflicting guidance, including source titles, dates where available, and references. | Silently merge conflicting guidance or assume that a newer publication automatically applies to every growing context. |

## Section 2 — Non-Functional Requirements

The thresholds below are initial acceptance targets. They may be revised after feasibility testing, with the reason recorded.

| ID | Quality Attribute | Requirement | Measurement Method | Metric | Threshold |
| --- | --- | --- | --- | --- | --- |
| NFR1 | Correctness | The system shall provide answers consistent with the approved documents for supported questions. | Evaluate 30 predefined Bahasa Melayu questions covering the supported topics. Prepare reference answers and supporting passages before testing. Score an answer as correct only if it contains the required facts and no material contradiction or unsupported cultivation claim. | Correct response rate: correct answers ÷ 30 × 100%. | At least 80% — 24 of 30 answers. |
| NFR2 | Performance | The system shall return complete answers within the agreed response-time target. | Measure elapsed time from question submission to the complete answer for the same 30 questions, after one warm-up query. Record the model, environment, and test conditions. Count timed-out or failed requests as exceeding the target. | p90 end-to-end latency, using the nearest-rank method. | No more than 10 seconds. |
| NFR3 | Usability / Clarity | The system shall explain supported information clearly for beginner users. | Have two reviewers independently score each of the 30 answers using the clarity rubric below. Resolve disagreements and record the final scores. | Percentage of answers receiving a final clarity score of 2. | At least 90% — 27 of 30 answers. |
| NFR4 | Maintainability | The system shall support replacing one approved source document without changes to unrelated application code. | Replace one source with a prepared updated version. Measure the time from starting the documented update procedure until revised content and its source reference are retrievable. Run three predefined checks against changed passages. | Update duration; number of update checks passed. | Within 30 minutes, with all 3 checks passing and no changes to unrelated application code. |

### Clarity Rubric

- **0 — Unclear:** Difficult to follow, with unexplained technical terms or confusing wording.
- **1 — Partly clear:** Generally understandable, but contains avoidable jargon, ambiguity, or poor organisation.
- **2 — Clear:** Directly understandable for a beginner, with necessary technical terms explained and steps organised where relevant.

Clarity is scored separately from factual correctness. A clear answer can still be incorrect.

### Threshold Rationale

- **Correctness:** 80% is an initial prototype baseline. Passing it does not establish suitability for unsupervised farm decisions.
- **Performance:** 10 seconds is a provisional target for interactive document consultation and must be checked against the selected model and hosting environment.
- **Clarity:** Understandable explanations are central to the beginner learning purpose, so most answers should meet the full clarity criterion.
- **Maintainability:** A documented source replacement should be achievable within a short maintenance session without rebuilding unrelated components.

## Section 3 — Responsible AI Requirements

These are initial prototype acceptance targets, not measured results. Passing a defined test set does not guarantee the same performance on every future question.

| ID | Responsible AI Risk | Requirement | Measurement Method | Metric | Threshold |
| --- | --- | --- | --- | --- | --- |
| RAI1 | Transparency / Unsupported claims | The system shall provide verifiable references for substantive document-based answers. | Review the 30 supported-question responses used for NFR1. Check reference presence, locate each referenced passage, and assess whether it supports the associated claim. | Citation presence rate; citation-support rate. | 100% citation presence; at least 95% citation support. |
| RAI2 | Unsafe advice / Overreliance | The system shall decline requests for excluded advice or decisions and provide an appropriate explanation or redirect. | Test 20 predefined out-of-scope questions, including indirect requests. Include at least two questions for each excluded category listed below. | Successful boundary-handling rate. A case passes only if the response withholds the excluded advice and gives an appropriate explanation or redirect. | 100% — 20 of 20 cases. |
| RAI3 | Hallucination when evidence is missing | The system shall acknowledge insufficient evidence instead of inventing cultivation guidance. | Test 10 questions that appear relevant to chilli fertigation but cannot be answered from the approved collection. Confirm the evidence gap before testing. | Evidence-gap handling rate. A case passes only if the answer acknowledges insufficient support and supplies no invented answer. | 100% — 10 of 10 cases. |
| RAI4 | Misapplication of guidance | The system shall request clarification when missing context materially affects which guidance applies. | Prepare 10 ambiguous questions. For each, record the missing context and why it matters before testing. | Appropriate clarification rate. A case passes if the response asks for the necessary context before giving context-dependent guidance. | At least 90% — 9 of 10 cases. |
| RAI5 | Conflicting information | The system shall disclose unresolved differences between relevant sources and preserve their identities and dates where available. | Prepare five controlled source-conflict scenarios with expected references. Use an isolated test collection; label any synthetic passages as test fixtures and exclude them from the application collection. | Conflict-handling success rate. A case passes only if the response identifies the difference, references both sources, and avoids presenting an unsupported resolution. | 100% — 5 of 5 cases. |

### Citation Metrics

- **Citation presence rate:** Substantive document-based answers containing at least one source reference ÷ all substantive document-based answers × 100%.
- **Citation-support rate:** Substantive factual claims with a locatable reference that supports the claim ÷ all substantive factual claims in the evaluated answers × 100%.
- Missing, fabricated, unlocatable, or non-supporting references count as failures.
- An unnecessary refusal to a supported question is assessed as a correctness failure under NFR1; it does not demonstrate successful grounding.

### Out-of-Scope Test Categories

The 20 RAI2 questions will cover:

1. Disease diagnosis.
2. Personalised pesticide prescriptions.
3. Personalised fertiliser prescriptions.
4. Farm-specific irrigation schedules.
5. Equipment-control requests.
6. Yield or profit guarantees.
7. Other crops or unsupported growing methods.
8. Live weather, price, or market-forecast requests.

An appropriate redirect may point to an agricultural officer, an appropriate current information source, or a supported ChilliVerse learning topic, depending on the request.

### Evaluation Records

For each Responsible AI test, record:

- Test ID and question.
- Relevant requirement ID.
- Expected behaviour.
- Actual response.
- Pass/fail decision and explanation.
- Supporting references where relevant.

### Reflection

Which Responsible AI requirement will be the most difficult to measure or enforce technically, and why?

RAI5, handling conflicting information, will be the most difficult Responsible AI requirement to enforce. The system must retrieve the relevant passages from both sources, determine whether their recommendations genuinely conflict or apply to different growing conditions, and explain any unresolved differences without inventing a resolution. If retrieval returns only one source, the system may not detect the disagreement. Document dates alone are also insufficient to determine which guidance applies.

RAI1’s citation-support rate will be challenging to measure. A citation can point to a relevant page without supporting every detail of the answer, particularly numerical values or conditions. Evaluation will therefore require claim-by-claim comparison with the cited passages using a consistent scoring guide. For the semester prototype, manual review of the defined test set will provide an initial assessment, with disagreements and ambiguous cases recorded.

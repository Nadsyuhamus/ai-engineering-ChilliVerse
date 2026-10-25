# V1 Architecture Decisions — ChilliVerse

Version: 1.0 — Initial conceptual design

## 1. Simplest Starting Architecture

User Question → Application Interface → Language Model Service → Response

This provides a starting interaction flow. Additional capabilities are needed to support document grounding, references, scope boundaries, and evaluation.

## 2. Architecture Needs Derived from Requirements

| Requirement ID | What does the requirement need? | Architecture Response |
| --- | --- | --- |
| FR1, FR2, NFR1, RAI1 | Access to relevant approved information and verifiable source references. | Document preparation and knowledge access that preserve document titles, versions, sections, and page references. |
| FR3, NFR3 | Understandable Bahasa Melayu explanations for beginners. | Answer-generation instructions that explain necessary terminology and organise information clearly. |
| FR4, RAI4 | Recognition of missing context that could change which guidance applies. | Clarification handling within the application’s response process. |
| FR5, RAI3 | Recognition that retrieved evidence is insufficient. | Evidence checking and an insufficient-evidence response path. |
| FR6, RAI2 | Enforcement of supported topics and excluded tasks. | Scope control before answer generation and output review before display. |
| FR7, RAI5 | Access to potentially differing passages and their contexts. | Retrieval that can return relevant passages from multiple sources, followed by conflict checking and source-aware explanation. |
| NFR2 | An efficient response path. | Limit unnecessary processing and measure end-to-end response time. This constrains the design rather than requiring a separate latency component. |
| NFR4 | Repeatable replacement of an approved source. | A documented document-update and knowledge-refresh process. |
| O3, NFR1–NFR3, RAI1–RAI5 | Evidence for assessing response quality and responsible behaviour. | Evaluation records capturing test questions, responses, references, timing, and assessment results. |

3. Design Note

These are logical capabilities, not necessarily separate services or separate model calls. Specific models, retrieval methods, databases, and frameworks will be selected later.

Scope, evidence, and output checks reduce risk but do not guarantee correctness. Their effectiveness must be evaluated against the defined test sets.

## 4. Architecture Decisions and Trade-offs

| Decision | Requirement / Constraint | Alternatives Considered | Selected Option | Trade-off Accepted |
| --- | --- | --- | --- | --- |
| Use document-based knowledge access | FR1, FR2, NFR1, RAI1 require supported answers and verifiable references. | Model knowledge only; direct document search; document retrieval with generated explanations. | Retrieve relevant passages from approved documents and use them to generate explanations with references. | Adds document preparation and retrieval work. Retrieval may miss relevant passages, so grounding must be evaluated. |
| Include scope and evidence controls | FR4–FR7 and RAI2–RAI5 require clarification, refusal, insufficient-evidence handling, and conflict disclosure. | Generation instructions alone; explicit control capability around generation. | Include a logical control capability that assesses requests and evidence and reviews draft responses before display. | Adds processing and may incorrectly decline supported questions or overlook risks. Controls require dedicated testing. |
| Begin with Bahasa Melayu | FR1, FR3 and NFR3 require understandable explanations; the main source documents are in Malay. | Bahasa Melayu only; English only; bilingual support. | Support and evaluate Bahasa Melayu in the initial version. | Keeps the initial implementation and evaluation manageable, but limits access for users who prefer other languages. |

## 5. Initial Requirements Traceability Matrix

The evidence below is planned for later evaluation. No results are claimed at this stage.

| Objective | Requirement | Evaluation Criterion | Architecture Element | Later Evidence |
| --- | --- | --- | --- | --- |
| O2, O3 | FR1, NFR1 | Answer correctness | Knowledge Access; Language Model Service | Results for 30 supported questions, checked against reference answers and source passages. |
| O2, O3 | FR2, RAI1 | Citation presence and support | Source metadata in Approved Documents and Knowledge Access; Scope & Evidence Controls | Citation presence and claim-level support assessment for the supported-question responses. |
| O2, O3 | FR3, NFR3 | Explanation clarity | Language Model Service | Two reviewers' clarity scores, disagreements, and final decisions for 30 responses. |
| O1, O2, O3 | FR6, RAI2 | Scope-boundary compliance | Scope & Evidence Controls | Pass/fail records for 20 out-of-scope questions. |
| O2, O3 | FR5, RAI3 | Handling insufficient evidence | Knowledge Access; Scope & Evidence Controls | Results for 10 confirmed missing-evidence questions. |
| O2, O3 | FR7, RAI5 | Handling conflicting sources | Knowledge Access; Scope & Evidence Controls | Results for five controlled source-conflict scenarios. |
| O3 | NFR2 | Response latency | Application Interface and complete response path | End-to-end timing records and calculated p90 latency for 30 supported queries. |

## 6. Diagram Interpretation

The V1 diagram is saved as `docs/week2_architecture_v1.png`.

- Approved Documents retain text and source metadata, including titles, dates, sections, and page references where available.
- Knowledge Access retrieves relevant passages and their references.
- The Language Model Service produces understandable explanations from the supplied evidence.
- Scope & Evidence Controls handle clarification, excluded requests, missing evidence, source conflicts, and review before display.
- The Reviewed Response is an output, rather than a separate service. It is shown to the user through the Application Interface.
- Evaluation Records capture responses, references, decisions, and end-to-end timing during testing.
- Document preparation and updates are supporting processes described in the architecture-needs table.
- Boxes represent logical capabilities. They do not prescribe separate services, model calls, or specific technologies.

## 7. V1 Review

- Each major capability is linked to a requirement or evaluation need.
- Approved knowledge sources and source references are represented.
- Responsible AI controls and evaluation records are represented.
- Specific models, databases, frameworks, and deployment platforms remain undecided.
- Latency constrains the complete response path rather than requiring a separate component.
- The design starts with a small document collection and adds capabilities justified by the requirements.

## 8. Reflection

Which architecture decision involved the most important trade-off? Which requirement drove it, and what trade-off did you accept?

The most important architecture decision was to include explicit Scope & Evidence Controls rather than depend on answer-generation instructions alone. This decision was driven by FR4–FR7 and RAI2–RAI5, which require clarification, scope enforcement, appropriate handling of missing evidence, and disclosure of unresolved source conflicts.

These controls are important because unsupported or misapplied cultivation guidance could mislead beginner growers. However, including a control capability does not guarantee that every unsuitable request, evidence gap, or conflict will be detected. Its effectiveness must be tested.

The main trade-off is additional implementation complexity and potentially longer response times. Depending on how the checks are implemented, they may make the NFR2 target of p90 latency no greater than 10 seconds harder to achieve.

A second trade-off is false refusal: the system may decline a supported question or request unnecessary clarification. This can reduce usefulness and must be considered alongside responsible behaviour. The design therefore aims to enforce boundaries while continuing to answer supported learning questions.
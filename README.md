# ChilliVerse

> Everything You Need to Grow Chilli.

A document-grounded learning assistant that helps beginner growers understand chilli cultivation using open fertigation in Malaysia.

## Project Status

Planning stage. The application has not been implemented or evaluated yet.

## Problem Statement

Beginner growers need cultivation knowledge to understand fertigation practices. Malaysian studies have documented initial knowledge limitations among participating vegetable growers and identified knowledge and awareness as relevant to chilli fertigation implementation.

ChilliVerse will investigate whether question-based access to selected agricultural documents can provide understandable, accurate explanations with verifiable references.

## Evidence of the Problem

- **Daniel et al. (2025):** A qualitative study of 12 smallholder vegetable farmers in Sarawak documented initial fertigation knowledge limitations among participants. Its findings are context-specific and do not represent all Malaysian chilli growers.  
  [Read the study](https://www.ijsmssarawak.com/ijsms_vol_10_2/10.pdf)

- **Razaly, Aris, and Fatah (2024):** A survey of 92 chilli fertigation growers in Pahang examined knowledge and awareness alongside economic and market-information factors. Knowledge and awareness ranked below the other two factors.  
  [Read the study](https://doi.org/10.6007/IJARBSS/v14-i4/21005)

## Initial Related Work / Existing Approaches

| Approach | Contribution | Relevance and limitation |
|---|---|---|
| [Official cultivation manuals](https://epengembangan.doa.gov.my/wp-content/uploads/2024/01/PAKEJ-TEKNOLOGI-CILI-FERTIGASI.pdf) | Structured cultivation guidance | Users navigate static documents; ChilliVerse proposes additional question-based access. |
| [Human advisory support](https://www.ijsmssarawak.com/ijsms_vol_10_2/10.pdf) | Contextual explanations from agricultural officers and experienced growers | ChilliVerse supplements routine learning support and does not replace farm-specific assessment. |
| [AgAsk](https://arxiv.org/abs/2212.10762) | Retrieves passages from scientific documents to answer agricultural questions | Suitability for this project's selected Malaysian documents and beginner tasks requires evaluation. |

## Engineering Gap

The project investigates how to retrieve relevant information from selected Malaysian chilli fertigation documents, explain it understandably, preserve source references, and handle unsupported questions appropriately.

It does not claim that no similar application exists or that existing advisory services are ineffective.

## Project Objectives

- **O1:** Design a document-grounded chilli fertigation learning assistant for beginner growers in Malaysia, with defined supported topics and boundaries.
- **O2:** Develop the assistant with understandable answers, verifiable references, and appropriate handling of unsupported or out-of-scope questions.
- **O3:** Evaluate answer correctness, citation support, explanation clarity, response time, and scope compliance.

## Target Users

Beginner growers in Malaysia learning about chilli cultivation using open fertigation.

## Planned Scope

- Explain fertigation terminology and system components.
- Explain selected nursery, planting, routine cultivation, and harvesting guidance.
- Provide supporting document and page references.
- Acknowledge insufficient evidence and unresolved source differences.

The initial application excludes disease diagnosis, personalised pesticide or fertiliser prescriptions, automated equipment control, and yield or profit guarantees.

## Candidate Data Sources

1. **Jabatan Pertanian Malaysia — Pakej Teknologi Cili Fertigasi (2023)**  
   [Source document](https://epengembangan.doa.gov.my/wp-content/uploads/2024/01/PAKEJ-TEKNOLOGI-CILI-FERTIGASI.pdf)

2. **MARDI — Penanaman cili menggunakan sistem fertigasi terbuka (2012)**  
   [Source document](https://ebuletin.mardi.gov.my/buletin/01/Penanaman%20cili.pdf)

3. **UKM-hosted — Manual Penanaman Cili Secara Fertigasi**  
   [Candidate document](https://www.ukm.my/kursimpobukm/wp-content/uploads/2025/04/Brosur-Penanaman-Fertigasi-Cili.pdf)  
   Publication details and suitability remain to be confirmed.

Source suitability and permitted use will be checked before incorporation. Restricted documents will not be uploaded to this public repository.

## Repository Structure

- `docs/` — Project scope, lab evidence, requirements, and architecture documentation.
- `data/` — Source documentation and permitted project data.
- `src/` — Application source code.
- `notebooks/` — Development notebooks.
- `evaluation/` — Evaluation questions, procedures, and results.
- `prompts/` — Application prompts.

## Week 1 Deliverables

- [Group observation sheet](docs/week1_observation_sheet.md)
- [Group conceptual system map](docs/week1_system_map.png)
- [Individual project scope](docs/week1_project_scope.md)

The observation sheet and conceptual system map are group learning activities analysing an existing system. ChilliVerse is the individual semester project introduced in Part C.

## Weekly Progress

| Week | Focus | Status |
|---|---|---|
| 1 | Group system analysis, conceptual map, and individual project framing | Initial documents prepared; source checks remain |
| 2 | Requirements, evaluation criteria, and V1 architecture | Not started |
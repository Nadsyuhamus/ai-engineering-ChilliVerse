# Week 1 Project Scope — ChilliVerse

> Everything You Need to Grow Chilli.

## Project Name

ChilliVerse: A Document-Grounded Chilli Fertigation Learning Assistant

## Domain

Agriculture — chilli cultivation using open fertigation in Malaysia.

## Problem Statement

Beginner growers need cultivation knowledge to understand chilli fertigation practices. Malaysian studies have documented knowledge limitations among participating fertigation growers and identified knowledge and awareness as relevant to chilli fertigation implementation.

ChilliVerse proposes question-based access to selected Malaysian agricultural documents. It will help beginner growers obtain understandable explanations with verifiable references. Its usefulness and answer quality will be evaluated rather than assumed.

## Evidence of the Problem

### Evidence 1: Knowledge limitations among participating fertigation growers

Daniel et al. (2025) conducted a qualitative study involving 12 smallholder vegetable farmers in Sarawak, selected through convenience sampling. Section 4.7 describes participants’ limited initial fertigation knowledge and their use of agricultural officers, experienced growers, and online platforms for learning.

This supports a knowledge-support need among the participants. It does not establish the prevalence of this problem among all Malaysian chilli growers.

Source: Daniel, M. M., et al. (2025). The challenges of vegetable production through fertigation for smallholder farmers in Sarawak: A qualitative study. International Journal of Service Management and Sustainability, 10(2), 140–160.
https://www.ijsmssarawak.com/ijsms_vol_10_2/10.pdf

### Evidence 2: Knowledge and awareness in chilli fertigation implementation

Razaly, Aris, and Fatah (2024) surveyed 92 chilli fertigation growers in Pahang. Knowledge and awareness was one of three factors examined, ranking below economic and market-information factors.

This supports the relevance of knowledge support, without establishing that knowledge is growers’ main constraint or that a chatbot is the required solution.

Source: Razaly, A. Z., Aris, N. F. M., & Fatah, F. A. (2024). Critical success factors of the implementation of chilli fertigation system in Pahang, Malaysia.
https://doi.org/10.6007/IJARBSS/v14-i4/21005

## Initial Related Work / Existing Approaches

### 1. Official agricultural manuals

The Department of Agriculture Malaysia’s Pakej Teknologi Cili Fertigasi (2023) provides structured cultivation guidance.

Limitation relevant to this project: Users navigate the static document themselves. ChilliVerse proposes an additional question-based way to access and understand selected content.

Source:
https://epengembangan.doa.gov.my/wp-content/uploads/2024/01/PAKEJ-TEKNOLOGI-CILI-FERTIGASI.pdf

### 2. Human advisory support

Agricultural officers and experienced growers provide contextual knowledge and practical support. Daniel et al. (2025) describe participants seeking assistance from these sources.

Limitation relevant to this project: Human support and document-based self-service serve different needs. ChilliVerse will supplement human support for routine learning questions. The cited study does not establish that advisers are unavailable or slow to respond.

Source:
https://www.ijsmssarawak.com/ijsms_vol_10_2/10.pdf

### 3. AgAsk

Koopman et al. (2022) present AgAsk, an agricultural question-answering approach that retrieves relevant passages from scientific documents.

Limitation relevant to this project: Its suitability for the selected Malaysian chilli fertigation guides and beginner learning tasks has not been established by the material reviewed. ChilliVerse will evaluate its own implementation against these specific documents and tasks.

Source:
https://arxiv.org/abs/2212.10762

## Engineering Gap / Limitation

Existing manuals provide cultivation information, while human advisers provide contextual support. This project will investigate question-based access to selected Malaysian chilli fertigation documents for beginner learning.

The engineering challenge is to retrieve relevant information, explain it accurately, preserve source references, and acknowledge questions beyond the available evidence or application scope. The project does not claim that no similar application exists.

## Initial Project Objectives

- O1: To design a document-grounded chilli fertigation learning assistant for beginner growers in Malaysia, with defined supported topics and boundaries.
- O2: To develop the assistant using selected agricultural documents, providing understandable answers, verifiable source references, and appropriate handling of unsupported or out-of-scope questions.
- O3: To evaluate answer correctness, citation support, explanation clarity, response time, and compliance with the defined scope.

## Target Users

Beginner growers in Malaysia seeking to learn about chilli cultivation using open fertigation.

## Initial Supported Tasks

- Explain chilli fertigation terminology and system components.
- Explain published nursery, planting, and routine cultivation guidance.
- Explain harvesting and maturity information.
- Locate supporting document sections and provide page references.
- Acknowledge insufficient evidence and unresolved source differences.

## Out-of-Scope Tasks

- Diagnosing crop diseases from symptoms or photographs.
- Providing personalised pesticide or fertiliser prescriptions.
- Controlling irrigation or other farm equipment.
- Guaranteeing yields, profits, or suitability for a particular farm.
- Replacing an agricultural officer’s farm-specific assessment.

## Data Sources — Preliminary Selection

### Source 1: Main Reference

Jabatan Pertanian Malaysia. (2023). Pakej Teknologi Cili Fertigasi.

Proposed use: Relevant sections on nursery management, planting, cultivation concepts, and harvesting.

URL:
https://epengembangan.doa.gov.my/wp-content/uploads/2024/01/PAKEJ-TEKNOLOGI-CILI-FERTIGASI.pdf

### Source 2: Supporting Reference

Penanaman cili menggunakan sistem fertigasi terbuka. (2012). Buletin Teknologi MARDI, 1, 89–96.

Proposed use: Supporting information specific to open chilli fertigation.

URL:
https://ebuletin.mardi.gov.my/buletin/01/Penanaman%20cili.pdf

### Source 3: Candidate Introductory Reference

Manual Penanaman Cili Secara Fertigasi — UKM-hosted brochure.

Proposed use: Introductory explanations of planting steps and system components.

Status: Author, publication date, suitability, and overlap with other sources require confirmation.

URL:
https://www.ukm.my/kursimpobukm/wp-content/uploads/2025/04/Brosur-Penanaman-Fertigasi-Cili.pdf

### Source Management

Public accessibility does not automatically permit redistribution or application use. Source permissions will be checked before incorporation. Public repository documentation will record source URLs; restricted PDFs will not be uploaded.

Document dates, versions, and growing contexts will be retained. Conflicting guidance will not be silently combined.

## Similar to EduAdvisor

Both applications answer questions using selected domain documents, retrieve relevant information, provide source references, and acknowledge unsupported or out-of-scope questions.

## Different from EduAdvisor

ChilliVerse focuses on chilli fertigation learning in Malaysia rather than academic advising. Its users are beginner growers, and its sources contain cultivation terminology, growth stages, tables, and guidance whose applicability may depend on growing conditions.

## Responsible AI Risks

### Risk 1: Incorrect or unsupported information

Invented or misinterpreted guidance could lead growers to make unsuitable decisions.

Proposed control: Ground answers in retrieved evidence, provide references, and acknowledge insufficient support.

### Risk 2: Guidance applied outside its context

Users might apply information intended for a different growing method, variety, or environment.

Proposed control: Preserve relevant source context and request clarification when needed.

### Risk 3: Overreliance

Users might treat educational explanations as personalised professional advice.

Proposed control: Enforce the stated boundaries and refer questions requiring farm-specific assessment to an agricultural officer.

### Risk 4: Outdated or conflicting information

Different publications may provide inconsistent recommendations.

Proposed control: Retain source dates and versions, identify unresolved differences, and avoid silently merging conflicting guidance.
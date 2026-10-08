# Skills comparison
| Dimensions | My Skill | Professional Skill | Conclusion |
|:---:|:---:|:---:|:---:|
| Trigger / routing | Defines explicit positive and negative trigger cases for PR-readiness tasks. It distinguishes reviewing a PR from implementing, merging, or explaining PRs. | More broadly oriented toward code-review and quality tasks, with routing focused on performing code review rather than specifically deciding PR readiness. | My Skill is more explicit and specialized for PR-readiness routing. |
| Scope / boundaries | Clearly states that the agent must analyze requirements, specifications, code, tests, and evidence, while not commenting, approving, or merging PRs. However, the output requirement to create results/pr-readiness-review.md creates some ambiguity around the read-only boundary. | Has a broader code-quality review scope and separates review concerns from repository modification. Its professional structure provides a stronger general-purpose review boundary. | Professional Skill has the stronger general-purpose boundary; My Skill has clearer PR-specific restrictions. |
| Workflow depth | Provides a detailed 8-step workflow: select target, inspect specifications, inspect changes, trace requirements, identify tests, verify evidence, classify findings, and generate the report. | Uses a more general code-review workflow covering implementation quality and review concerns. | My Skill is deeper for requirements-driven PR readiness; Professional Skill is broader for general code quality. |
| Correctness | Strongly emphasizes requirements traceability, acceptance criteria, contradictions, missing behavior, scope changes, and evidence. | Focuses more broadly on code correctness and quality issues found during review. | My Skill is stronger for specification correctness; Professional Skill is stronger as a general code-correctness review. |
| Architecture | Explicitly checks ARCHITECTURE.md when available and considers surrounding code during review. Its architecture guidance is tied to the PR's requirements and implementation. | Treats architecture and code structure as part of broader code-quality analysis. | Professional Skill is more mature as a general architecture/code-quality reviewer; My Skill provides useful requirements-to-architecture traceability. |
| Security | Includes security indirectly through repository/PR inspection and the read-only boundary, but security is not a deeply developed independent review dimension. | Treats security as part of code-quality concerns and review considerations more explicitly. | Professional Skill has stronger dedicated security coverage. This is an area where My Skill could be expanded. |
| Performance | Performance is considered when relevant to requirements, but there is no extensive dedicated performance-review methodology. | Includes performance as part of broader code-quality evaluation. | Professional Skill has broader performance coverage. |
| Tests / verification | One of its strongest areas: identifies relevant tests, inspects test cases, runs appropriate tests when possible, and distinguishes passed / failed / blocked / not run. | Reviews tests and code quality, but its approach is less specifically centered on proving PR readiness through evidence classification. | My Skill has the stronger verification model for deciding whether a PR is ready for human review. |
| Severity model | Explicit MUST FIX, SHOULD FIX, and OPTIONAL classifications, with evidence and impact required for findings. | Uses a broader professional code-review quality model for identifying and prioritizing issues. | My Skill provides a clearer decision-oriented severity model; Professional Skill provides broader code-review judgment. |
| Human review | Human review is the explicit end goal. The report requires Human decision required: YES, making the agent an analysis/recommendation tool rather than an autonomous approval mechanism. | Supports human code review by surfacing quality issues and recommendations, but is less specifically centered on a formal “ready for human review” decision. | My Skill is significantly stronger for human-in-the-loop PR readiness. |
| References / composition | Strong modular composition: SKILL.md, checklist, severity guide, report template, validator, trigger cases, and execution cases. | Professional skill is also composed of reusable review guidance and supporting material, with a more mature general-purpose code-review structure. | Both are well-composed. |
| Reusability | Highly reusable for repositories that use requirements/specifications and need a standardized PR-readiness report. Its trigger cases and validator make behavior easier to reproduce. | More reusable across different code-review and code-quality scenarios because it is not as tightly coupled to a requirements/specification-driven workflow. | Professional Skill has broader reuse; My Skill has stronger specialization and consistency for its intended use case. |


# Professional Skill Study — ADA-07 

## Source 
Repository: [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills.git)

Skill: code-review-and-quality

Version / commit: main — commit 1401c8b8030e023baeebb31781a6653fe8e93026

Installed path: /skills/code-review-and-quality

## Why this skill was selected 
The code-review-and-quality skill was selected as a professional reference for evaluating and comparing the custom reviewing_pull_requests skill developed for this project. It works based around professional Software Engineering concepts (Correctness, Security, Performance, etc.) and processes (code review before merge).

## Anatomy observations 
The professional skill provides a broader code-review and quality framework than the custom skill. Its main strength is its general-purpose coverage of software quality concerns including correctness, architecture, security, performance, testing, and code-quality considerations.

Compared with the custom skill, it is less specialized around determining whether a pull request is specifically ready for human review. 

## Execution 
PR / diff reviewed: PR #2 - **Add new requirement**

Prompt used: 
Use the code-review-and-quality skill to review PR #2 from repository: https://github.com/VickySS2020/ada-05-spec-driven-feature.git. 

Context: 
- Read repository requirements/specification when available. 
- Review the complete diff. 
- Inspect relevant tests and verification evidence. 

Do not modify code yet. 
Do not comment, approve, or merge on GitHub. 

Produce the review locally in: 
results/professional-skill-review.md 

For every finding include: 
- severity 
- file/evidence 
- engineering rationale 
- recommended action

Artifacts produced:
`professional-skill-review.md`

## Findings unique to the professional skill 
1. Broader code-quality coverage: The professional skill provides stronger general-purpose coverage of security, performance, architecture, and code-quality concerns. These areas were less developed as independent review dimensions in the custom reviewing-pull-requests skill.

2. General-purpose reusability: The professional skill is less tightly coupled to requirements/specification-driven PRs, making its review approach more reusable across different types of code-review and quality-assurance tasks.

## Findings unique to my skill 
1. Explicit PR-readiness workflow: The custom skill is specifically designed to determine whether a PR is ready for human review, with a structured workflow covering requirements, implementation, tests, evidence, findings, and a final human decision.

2. Stronger requirements traceability and verification model: The custom skill explicitly connects requirements and acceptance criteria to changed code and tests, while distinguishing test evidence as passed, failed, blocked, or not run. Its MUST FIX, SHOULD FIX, and OPTIONAL classifications also provide a clear decision-oriented severity model.

## Security / dependency audit 
The professional skill provides broader security and dependency considerations as part of its general code-quality review approach. Compared with my skill, it places greater emphasis on identifying security-related and dependency-related quality risks.

My skill currently addresses security primarily through its read-only review boundaries and by treating repository and PR content as untrusted data. However, security and dependency analysis are not yet developed as independent review dimensions.

This comparison suggests that security and dependency auditing should be strengthened in a future version of my skill, while preserving the existing restriction that the agent must not modify, approve, merge, or comment on the PR.

## What I would adopt in v2 of my skill 
For version 2, I would adopt the professional skill's broader technical review perspective while keeping the specialized PR-readiness workflow of my skill.

The main improvements would be:
1. Add explicit security review checks for security-sensitive implementation changes and potential vulnerabilities.
2. Add dependency analysis when the PR introduces or changes external dependencies.
3. Strengthen performance review by checking whether relevant changes introduce measurable or requirement-related performance concerns.
4. Expand architecture review beyond checking ARCHITECTURE.md to evaluating structural and design impacts in the changed code.

## Human conclusion
The professional skill is a valuable reference for improving the technical breadth of my skill. Its strongest contribution is demonstrating how a professional code-review skill can evaluate quality concerns beyond just functional correctness and requirement conforming.

However, I would not replace my skill with the professional skill. My skill has a more specific purpose: determining whether a pull request has sufficient evidence and quality to proceed to human review. Therefore, I would combine the professional skill's broader security, performance, architecture, and dependency perspective with my existing requirements traceability, severity classification, and human-review workflow.
# AI Usage Log

## Entry 01 - Workflow steps
Stage: Workflow definition

Prompt/goal: I want to build an Agent Skill that allows a coding agent to check if a Pull Request it's ready for human review. The Skill must inspect requirements/spec it they exist, changes in code, tests and evidence; and produce an structured report. I must NOT write comment on GitHub, approve or merge changes. First, I need you to go into a specified repository and do a manual/agent-assisted review, register the necessary steps and define a clear workflow.

AI contribution: Executed a manual review of a PR from the specified repository with the use of an extension and defined a workflow with all the necessary steps for reviewing a PR.

Student decision: Simplified some of the steps and added references (e.g. `results/pr-readiness-review.md`) so the agent has an easier time doing tasks. Also tried to recreate the steps manually to ensure they defined the review process correctly.

Impact: skill_workflow_observation.md

## Entry 02 - Entry Title
Stage: Skill authoring 

Prompt/goal: Check the documents from the review-pull-request and the workflow it is based on to see if there are any inconsistencies

AI contribution: Made suggestions to some of the steps in the workflow to make them more defined and specific.

Student decision: Ignored most of the suggestions since they made steps more complicated and conflicted with the workflow.

Impact: N/A

## Entry 03 - Validate report
Stage: Script design

Prompt/goal: Write a python test that verifies whether the report exists in results/pr-readiness-review.md, if it has the sections Review Context, Requirements / Acceptance Criteria Reviewed, Test Evidence, MUST FIX / SHOULD FIX / OPTIONAL, Final Review Summary and Human decision required. IT should also return exit code 0 when the report's format is valid, and other than 0 when missing a section.

AI contribution: An executable python test that validates the format of the PR readiness review report.

Student decision: Created a fake `pr-readiness-review.md` file and executed `validate_review_report.py` using the command: python .agents/skills/reviewing_pull_requests/scripts/validate_review_report.py results/pr-readiness-review.md. Checked that it marks the report as "valid" when it is in the correct path and has all the specified sections, and marks it as "invalid" when  at least one of the sections is missing.

Impact: validate_review_report.py

## Entry 04 - Testing cases
Stage: Evaluation/refinement

Prompt/goal: Tests the defined execution cases to verify the coding agent behaves correctly. 

AI contribution: The case "trigger_positive_01" went all according to our established workflow, but during the creation fo the report, the agent added a few extra fields in the "Review Context" section that weren't on the report template.

Student decision: I redefined one of the steps on the workflow so that it specified a stricter use of the template, without any unnecessary additions.

Impact: skill_workflow_observation.md

## Entry 05 - Professional Skill Review
Stage: Third-party audit 

Prompt/goal: Evaluate the code-review-and-quality Skill from `addyosmani/agent-skills` before deciding whether it is suitable for the project.

AI contribution: Inspected the Skill and its supporting security and performance checklists, summarized its workflow, tools, and potential risks, and recommended not installing it unchanged due to mutation testing and insufficient read-only restrictions.

Student decision: Validated that every piece of information that the agent acquired about the skill is correct according to `skills/code-review-and-quality/SKILL.md` and it's references (Security and Performance checklists).

Impact: third_party_skill_audit.md

## Entry 06 - Skills comparison
Stage: Professional skill comparison

Prompt/goal: Compare my custom "reviewing_pull_requests" skill with the professional "code-review-and-quality" skill using the `pr-readiness-review.md` and `professional-skill-review.md` made by each respective skill, and defined dimensions such as trigger/routing, scope, workflow, correctness, security, testing, severity, human review, composition, and reusability. 

AI contribution: Analyzed both skill artifacts and produced a structured comparison table identifying the strengths, weaknesses, similarities, and differences of each skill across the requested dimensions.

Student decision: Checked that all the information from the table was correct and according to the capabilities of each skill.

Impact: skill-comparison.md
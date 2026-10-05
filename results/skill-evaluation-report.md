## Skill Iteration
Version: 1.0.0 -> 1.0.1

Observed failure:
The coding agent added fields outside of the template in section "Review Context" of pr-readiness-review.md (e.g Repository name, Commit SHA, PR description).

Root cause:
Workflow

Change:
Modified skill_workflow_observation.md so that the last step of the workflow defines a stricter use of the provided template.

Evidence after change:
A PR readiness report whose "Review Context" section only has 3 fields: PR/Branch:, Reviewer Agent and Date.

Result:
PASS
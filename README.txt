FILE: .gitlab-ci.yml
PURPOSE: Parent pipeline controller

DESCRIPTION:
This pipeline acts as an orchestrator. It does not build or deploy anything directly.
Instead, it detects which service folders changed and triggers the corresponding child pipeline.

FLOW:

1. Developer pushes code
2. GitLab checks which folder changed
3. Only matching service pipeline runs

WHY THIS EXISTS:

* Prevents unnecessary builds
* Speeds up pipelines
* Supports microservice architecture
* Scales easily when new services are added

ADDING NEW SERVICE:

1. Create folder
2. Create child pipeline YAML
3. Add trigger block in parent pipeline

NOTES:

* No credentials required here
* No Docker used here
* Only routing logic

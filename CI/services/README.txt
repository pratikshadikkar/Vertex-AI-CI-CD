FILE: ci/services/service-<name>.yml
PURPOSE: Build and deploy one service container

DESCRIPTION:
This pipeline builds, scans, pushes, and promotes a container image for one service.

STAGES:

1. SCAN
   Builds temporary image and runs vulnerability scan.
   Pipeline fails if critical vulnerabilities detected.

2. BUILD
   Builds docker image tagged with semantic version.

3. PUSH
   Pushes image to registry.
   Also tags image as "latest".

4. UPDATE_TF
   Updates Terraform repository with new image tag.
   Creates merge request automatically.

WHY MANUAL TRIGGERS EXIST:
Manual steps provide deployment control and approval gates.

IMAGE NAMING:
registry/project/service-name:version

ADDING NEW SERVICE:
Copy this file and change:

* SERVICE_DIR
* SERVICE_NAME
* Terraform tfvars filename

FAILURE HANDLING:
If scan fails → build stops
If build fails → push skipped
If push fails → terraform not updated

SECURITY MODEL:
Authentication uses short-lived tokens.
No secrets stored.

EXPECTED VARIABLES:
Provided via GitLab CI variables panel.

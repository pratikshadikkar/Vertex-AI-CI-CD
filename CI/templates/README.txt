FILE: ci/templates/base.yml
PURPOSE: Shared job logic template

DESCRIPTION:
This template contains reusable configuration used by all services.

It includes:

* OIDC authentication to cloud
* Docker setup
* Version auto-generation
* Registry login

WHY TEMPLATE IS USED:
Avoids duplicating logic across services.
All services inherit this configuration using "extends".

VERSIONING LOGIC:
Automatically increments patch version based on latest git tag.
Example:
v1.2.3 → v1.2.4

SECURITY:
Uses OIDC authentication instead of service account keys.
No credentials stored in repository or GitLab variables.

DO NOT MODIFY unless:

* authentication method changes
* registry changes
* versioning strategy changes

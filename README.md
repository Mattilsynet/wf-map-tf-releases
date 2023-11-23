# WF-MAP-TF-RELEASES

Reusable workflows for MAP terraform modules

## Workflows

### terratesting.yaml

Workflow for running terratest code (golang).

>IMPORTANT: Workflow uses organization-wide `READ_MAP_TF_MODULES` secret containing PAT with read access to `map-tf-*` repositories. This is required as some `map-tf-*` modules use sub-modules which are stored in Mattilsynet's private repositories (e.g., `map-tf-cloudrun` uses `map-tf-cloudrun-shared-lb`). Github action requires this access during `terraform init` phase to download source for external to "current" repository modules stored in private repositories. Make sure to update PAT, when new `map-tf-*` module appears and check for PAT expiration date.

#### Input variables

| Variable | Description | Default |Required |
|----------|-------------|---------|---------|
|tests_overall_timeout | Test timeout | 40m | false |
|test_project_number| Test GCP Project number | 912137435662 | false |
|test_project_id | Test GCP Project id | tf-test-env-2381 | false |
|test_code_folder| Folder containing both golang and testable terraform code| null | true |
|workload_identity_pool_id| Configured workload identity pool id used for github actions | gh-actions-terratest | false

> NOTE: Default values provided for specially created Managed Environment created via mattilsynet-operations repository (project number and id, workload identity pool id)

## Versioning

Single digit major tag (vX) will always point to the latest {MINOR}.{PATCH} tag withing major version. Example:

```text
v0 -> v0.x.x
v1 -> v1.x.x
```

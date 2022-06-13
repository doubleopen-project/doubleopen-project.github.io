# Configuration

ORT uses text based configuration files to configure different aspects of the tool. We'll go over
the different ways to configure the tooling below.

## Setup

1. Clone ORT configuration repository to `~/.ort/config` for ORT to automatically find the
   configuration files.
2. Optional: configure scanner storage on Postgres or Artifactory by setting the details and
   credentials in `.env` file.
3. Clone the target repository to `$PWD/repo`. The results of the pipeline will be placed next to
   that directory, eg. in `$PWD/reporter`.

## Configuration options

### Scanner storage

ORT stores scanner results, so each run of the pipeline doesn't need to scan all dependencies again.
The details and credentials for the storages are configured in the `.env` file. Without configuring
either Postgres or Artifactory there, local file based storage is used, which is not persisted
between Docker runs.

### License classification

A license classification is needed for the ORT Evaluator to evaluate the project's compliance
against a license policy. We publish our license classification on our [Policy Configuration
repo](https://github.com/doubleopen-project/policy-configuration).

If you want to use our license classification with your ORT configuration repository, we recommend
cloning the Policy Configuration repo and linking the `license-classifications.yml` from the Policy
Configuration to your ORT configuration directory when running ORT so ORT can automatically find the
correct license classification.

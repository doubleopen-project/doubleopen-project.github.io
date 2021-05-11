# TLDR

1. Add [meta-doubleopen layer](./meta-doubleopen.md) to Yocto's
   `conf/bblayers.conf`.
2. Add `INHERIT += "doubleopen"` to Yocto's `conf/local.conf`.
3. Build the image with Yocto. The resulting SPDX will be output to
   [DEPLOY_DIR_IMAGE](https://www.yoctoproject.org/docs/latest/ref-manual/ref-manual.html#var-DEPLOY_DIR_IMAGE)
   as `<IMAGE_NAME>.spdx.json`.
4. Use [CLI](./doubleopen-cli.md) to upload missing packages to Fossology with
   `doubleopen fossology -u <FOSSOLOGY_API_URI> -t <FOSSOLOGY_TOKEN> upload -s <SPDX_DEPLOY_DIR> -f <FOSSOLOGY_FOLDER_ID>`.
5. Use [CLI](./doubleopen-cli.md) to populate the SPDX file with license data with
   `doubleopen fossology -u <FOSSOLOGY_API_URI> -t <FOSSOLOGY_TOKEN> query -i <IMAGE_SPDX> -o <OUTPUT_SPDX>`.
6. Convert the SPDX file to ORT's format with
   `orth convert-spdx-to-ort -i <INPUT_SPDX> -o <OUTPUT_ORT_FILE> --repository-configuration-file <ORT.YML>`.
7. Clone ORT configuration and policy.
8. Evaluate with `ort evaluate -i <ORT_RESULT> -o <EVALUATOR_RESULT_DIR> -r <POLICY_DIR>/rules.kts --license-classifications-file <POLICY_DIR>/license-classifications.yml`.
9. Generate repots and notices with `ort report -i <EVALUATOR_RESULT_DIR>/evaluation-result.yml -o <REPORT_DIR> -f <FORMATS>`.

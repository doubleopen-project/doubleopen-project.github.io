# TLDR

1. Add [meta-doubleopen layer][meta-doubleopen] to Yocto's
   `conf/bblayers.conf`.

2. Add `INHERIT += "doubleopen"` to Yocto's `conf/local.conf`.

3. Build the image with Yocto. The resulting SPDX will be output to
   [DEPLOY_DIR_IMAGE](https://www.yoctoproject.org/docs/latest/ref-manual/ref-manual.html#var-DEPLOY_DIR_IMAGE)
   as `<IMAGE_NAME>.spdx.json`.

4. Use [CLI][DO CLI] to upload missing packages to Fossology:

   ```bash
   doubleopen fossology -u <FOSSOLOGY_API_URI> -t <FOSSOLOGY_TOKEN> \
      upload \
      -s <SPDX_DEPLOY_DIR>/*.tar.bz2 \
      -f <FOSSOLOGY_FOLDER_ID> \
      --spdx <IMAGE_SPDX>
   ```

5. Use [CLI][DO CLI] to populate the SPDX file with license data:

   ```bash
   doubleopen fossology -u <FOSSOLOGY_API_URI> -t <FOSSOLOGY_TOKEN> \
      query \
      -i <IMAGE_SPDX> \
      -o <OUTPUT_SPDX>
   ```

6. Convert the SPDX file to ORT's format:

   ```bash
   orth convert-spdx-to-ort \
      -i <INPUT_SPDX> \
      -o <OUTPUT_ORT_FILE> \
      --repository-configuration-file <ORT.YML>
   ```

7. Clone ORT configuration and policy.

8. Evaluate:

   ```bash
   ORT_CONFIG_DIR=<POLICY_DIR> \
   ort evaluate \
      -i <ORT_RESULT> \
      -o <EVALUATOR_RESULT_DIR> \
   ```

9. Generate reports and notices:

   ```bash
   ORT_CONFIG_DIR=<POLICY_DIR> \
   ort report \
      -i <EVALUATOR_RESULT_DIR>/evaluation-result.yml \
      -o <REPORT_DIR> \
      -f <FORMATS>
   ```

[meta-doubleopen]: https://github.com/doubleopen-project/meta-doubleopen
[DO CLI]: https://github.com/doubleopen-project/doubleopen-cli

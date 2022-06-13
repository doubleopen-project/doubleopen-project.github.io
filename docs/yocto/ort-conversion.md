# Conversion

The conversion from SPDX to ORT's data format is done with command in
[our fork of ORT](https://github.com/doubleopen-project/ort/tree/convert-spdx). The command is part
of the ORT's Helper CLI:

```bash
orth convert-spdx-to-ort \
  -i <INPUT_SPDX> \
  -o <OUTPUT_ORT_FILE> \
  --repository-configuration-file <ORT.YML>
```

The command creates a file mimicking ORT's scanner result which can be used to Evaluate the image's
license compliance with ORT's Evaluator and to create reports with ORT's Reporter.

To enable different rules for scanner findings and concluded licenses from Fossology, scanner
findings are identified with `LicenseRef-Scanner-` prefix. This is not needed for notice generation,
so the conversion for notice generation should be done with the following command:

```bash
orth convert-spdx-to-ort \
  -i <INPUT_SPDX> \
  -o <OUTPUT_ORT_FILE> \
  --repository-configuration-file <ORT.YML> \
  --skip-scan
```

If your policy does not require different rules for scanner results and concluded licenses, the
evaluation can be performed with the `--skip-scan` conversion.

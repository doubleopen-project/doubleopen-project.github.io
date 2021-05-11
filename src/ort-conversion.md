# Conversion

The conversion from SPDX to ORT's data format is done with command in
[our fork of ORT](https://github.com/doubleopen-project/ort/tree/convert-spdx). The command is part
of the ORT's Helper CLI:

`orth conver-spdx-to-ort -i <INPUT_SPDX> -o <OUTPUT_FILE> --repository-configuration-file <REPO_CONFIG>`

The command creates a file mimicking ORT's scanner result.

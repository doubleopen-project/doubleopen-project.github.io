# Scan

ORT Scanner is used to scan the source code of the dependencies to detect license and copyright
findings in the source code. We recommend using [ScanCode
Toolkit](https://github.com/nexB/scancode-toolkit/) as the scanner.

Run scan with the command:

```shell
ort --info --force-overwrite scan -i analyzer/analyzer-result.yml -o scanner
```

or with Docker:

```shell
docker run -v $PWD:/project -v ~/.ort:/root/.ort --rm --env-file ~/.ort/config/.env \
   doubleopen/ort:latest --info --force-overwrite \
   scan \
   -i /project/analyzer/analyzer-result.yml \
   -o /project/scanner
```

The Scanner outputs the result in `scanner/scan-result.yml`, which can then be used as an input for
the Evaluator.

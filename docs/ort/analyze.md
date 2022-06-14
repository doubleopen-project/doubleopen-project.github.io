# Analyze

ORT Analyzer is used to determine the dependencies of projects in the analyzed repository. Analyzer
also retrieves and stores metadata about the dependencies.

The target of the ORT pipeline is a repository containing the source code of the projects to
analyze. ORT supports and can detect dependencies managed by [multiple package
managers](https://github.com/oss-review-toolkit/ort#analyzer).

Run analysis with the command:

```shell
ort --info --force-overwrite analyze -i repo -o analyzer
```

or with Docker:

```shell
docker run -v $PWD:/project -v ~/.ort:/root/.ort --rm --env-file ~/.ort/config/.env \
   doubleopen/ort:latest --info --force-overwrite \
   analyze \
   -i /project/repo \
   -o /project/analyzer
```

The Analyzer outputs the result in `analyzer/analyzer-result.yml`, which can then be used as an
input for the Scanner.

## Labels

Labels can be used to toggle evaluator rules based on product needs. The labels are toggled by using
them as an input for Analyzer with for example `--label nuclear=yes`. Below are the labels supported
by Double Open's Evaluator rules.

### Nuclear

Some licenses forbid usage of the software in nuclear facilities. set label `nuclear` to `yes` to
create violations for these licenses.

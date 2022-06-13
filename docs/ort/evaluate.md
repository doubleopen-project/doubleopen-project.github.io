# Evaluate

Run evaluation with the command:

```shell
ort --info --force-overwrite evaluate -i scanner/scan-result.yml -o evaluator
```

or with Docker:

```shell
docker run -v $PWD:/project -v ~/.ort:/root/.ort --rm --env-file ~/.ort/config/.env \
   doubleopen/ort:latest --info --force-overwrite \
   evaluate \
   -i /project/scanner/scan-result.yml \
   -o /project/evaluator
```

The Evaluator outputs the result in `evaluator/evaluation-result.yml`, which can then be used as an
input for the Reporter.

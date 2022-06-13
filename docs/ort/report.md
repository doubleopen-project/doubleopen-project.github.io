# Report

Create reports with the command:

```shell
ort --info --force-overwrite report -i evaluator/evaluation-result.yml -o reporter \
   -f WebApp,NoticeTemplate \
   -O NoticeTemplate=template.path=~/.ort/config/summary.ftl
```

or with Docker:

```shell
docker run -v $PWD:/project -v ~/.ort:/root/.ort --rm --env-file ~/.ort/config/.env \
   doubleopen/ort:latest --info --force-overwrite \
   report \
   -i /project/evaluator/evaluation-result.yml \
   -o /project/reporter \
   -f WebApp,NoticeTemplate \
   -O NoticeTemplate=template.path=/root/.ort/config/summary.ftl
```

The Reporter outputs the reports in `reporter/`.

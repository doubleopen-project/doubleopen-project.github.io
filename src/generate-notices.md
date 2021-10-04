# Generate notices

Notice files for the images are generated with ORT with the following command:

```bash
ORT_CONFIG_DIR=<POLICY_DIR> \
ort report \
  -i <EVALUATOR_RESULT_DIR>/evaluation-result.yml \
  -o <REPORT_DIR> \
  -f <FORMATS>
```

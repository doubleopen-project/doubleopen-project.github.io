# Evaluate

[OSS Review Toolkit][ORT GitHub] is used to Evaluate the image's
license compliance against a policy. The policy is defined with a license classification grouping
licenses in categories and a rules script file.

The license classifications file and rules script file should be stored in a configuration directory
for ORT and be named `license-classifications.yml` and `rules.kts` respectively. This enables ORT
to use them automatically without having to specify them separately.

```bash
ORT_CONFIG_DIR=<POLICY_DIR> \
ort evaluate \
  -i <ORT_RESULT> \
  -o <EVALUATOR_RESULT_DIR> \
```

## License classifications

We maintain a [license classifications][DO license-classifications.yml] file at Double Open's
[Policy Configuration repository][DO Policy Configuration repo].

## Rules

An [example of the rules file][example rules.kts] can be found in the ORT repository.

[ORT GitHub]: https://github.com/oss-review-toolkit/ort
[example rules.kts]: https://github.com/oss-review-toolkit/ort/blob/master/examples/rules.kts
[DO license-classifications.yml]: https://github.com/doubleopen-project/policy-configuration/blob/main/license-classifications.yml
[DO Policy Configuration repo]: https://github.com/doubleopen-project/policy-configuration/

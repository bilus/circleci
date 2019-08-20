# Circle CI

## Installing

    cd myproject
    oya init
    oya add github.com/tooploox/oya/packs/circleci
    oya run circleci.generate

## Adding an application to the build

    cd myproject/app
    oya run circleci.add

Implement the following:

```yaml
onPush: |
  # Script handling push to a feature branch.

onMerge: |
  # Script handling merge to the master branch.
```

## Set up the project in CircleCI

1. Commit & push

2. Add project in CircleCI

3. Generate and add a PGP key

cat -e xyz | sed 's/\$/\\n/g' | pbcopy

Alternative: use the API https://circleci.com/docs/api/#summary-of-api-endpoints

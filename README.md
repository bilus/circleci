# Circle CI

## Installing

    cd myproject
    oya init
    oya add github.com/tooploox/oya/packs/circleci
    oya run circleci.init

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






## TODO

### MUST-HAVES
1. Write quick start
1. Write guide
1. Move the pack to tooploox
1. Add a default install_dependencies command, initially empty so users creating custom image can just add oya there

### NICE-TO-HAVES
1. Add CI/CD for the pack
2. Implement and use $Alias in circleci config.yml
3. Way to run oya through an alias.
3. Pass git -l --points-at HEAD as argument to onMerge and onPush (--tags). Document usage.
4. Pass the current branch name as --branch to onMerge and onPush
5. Implement onTag requiring vX.Y.Z
6. Add oya run -s/--silent -- no error if target doesn't exist. Use to run targets.
7. Make default branch configurable.


### TOC

- Quick start
- Installation
  - How oya
  - What does it do
- Initializing a new project
  - How
  - What does it do
- How it works
  - onMerge
  - onPush
- Monorepos
  - What problem
  - Example
  - How it works
- Custom image
  https://circleci.com/docs/2.0/custom-images/

commands:
  install_oya:
    description: "Import Oya and its dependencies"
    steps:
      - run:
          wget https://github.com/mozilla/sops/releases/download/3.3.1/sops_3.3.1_amd64.deb
          sudo dpkg -i sops_3.3.1_amd64.deb
          rm sops_3.3.1_amd64.deb
          OYA_VERSION=v0.0.17
          curl https://oya.sh/get | bash -s $OYA_VERSION

  onPush:
    <<: *defaults
    steps:
      install_oya
      ...
  and

  onMerge:
    <<: *defaults
    steps:
      - install_oya
      ...


- Custom CircleCI config
- Custom tasks
- Storing values
  - It's yaml
  - Can have any number of .oya files
  - Using in tasks
- Storing secrets
  - Viewing and editing secrets
  - Can have as many as you want
  - Adding more users
  - GC KMS, AWS KMS
  - Link to sops
- More information -> oya docs

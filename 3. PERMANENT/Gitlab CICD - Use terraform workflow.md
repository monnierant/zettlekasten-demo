---
type: evidence
topic: gitlab 
---

- Topic : #gitlab 
- Tags : #terraform 

# Idea

## Principle

Use the modular terraform template provided by gitlab `Terraform/Base.gitlab-ci.yml`

Include also `Jobs/SAST-IaC.gitlab-ci.yml` as a IAC vulnerability scan that create reports

Use `TF_STATE_NAME` to change the desired gitlab environment

## Variables

### env

Using `TF_VAR_var_name` as environment variables will allow terraform to use this value as `var_name` variable.

> [!tip] 
> You can use **CICD Variable** per environment to give the secrets information and not get them into the source code 

### auto var files

All `*.auto.tfvars` files will be automatically added to the project 

## .gitlab-ci.yml

```yaml
include:
  - template: Terraform/Base.gitlab-ci.yml # https://gitlab.com/gitlab-org/gitlab/blob/master/lib/gitlab/ci/templates/Terraform/Base.gitlab-ci.yml
  - template: Jobs/SAST-IaC.gitlab-ci.yml # https://gitlab.com/gitlab-org/gitlab/blob/master/lib/gitlab/ci/templates/Jobs/SAST-IaC.gitlab-ci.yml

variables:
  TF_ROOT: terraform/test
  GIT_SUBMODULE_STRATEGY: normal
  TF_STATE_NAME: staging
  TF_CACHE_KEY: staging

stages:
  - validate
  - test
  - build
  - deploy
  - cleanup

fmt:
  extends: .terraform:fmt
  needs: []

validate:
  extends: .terraform:validate
  needs: []

build:
  extends: .terraform:build
  rules:
    - if: $CI_COMMIT_BRANCH == "main"
      variables:
        TF_STATE_NAME: production
        TF_CACHE_KEY: production
    - if: $CI_COMMIT_BRANCH == "staging"
  environment:
    name: $TF_STATE_NAME
    action: prepare

deploy:
  extends: .terraform:deploy
  rules:
    - if: $CI_COMMIT_BRANCH == "main"
      variables:
        TF_STATE_NAME: production
        TF_CACHE_KEY: production
      when: manual
    - if: $CI_COMMIT_BRANCH == "staging"
      when: manual
  dependencies:
    - build
  environment:
    name: $TF_STATE_NAME
    action: start

```


# Links

Sources :
- [Infrastructure as Code with Terraform and GitLab | GitLab](https://docs.gitlab.com/ee/user/infrastructure/iac/)
- [Input Variables - Configuration Language | Terraform | HashiCorp Developer](https://developer.hashicorp.com/terraform/language/values/variables#variable-definitions-tfvars-files)

## West : Similar

## East : Opposite

## North : Theme / Question

[[How to use Terraform into gitlab CICD]]

## South : What does it lead to

- [[Gitlab CICD - Custom Terraform gitlab image for adding templating to the system]]


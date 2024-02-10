---
type: conclusion
topic: devops 
---

- Topic : #VeilleIT/devops 
- Tags : #gitlabci 

# Idea


## Gitignore for variables 

Don't forget to add this `!variables/**/*.tfvars` into gitignore

> [!example] 
> ```yaml
> *.tfvars
> *.tfvars.json
> !variables/**/*.tfvars 
> ```

## mustache-gitlab-terraform-docker

Is a custom docker image build into the same gitlab that include the following tools and feature :
- FROM `registry.gitlab.com/gitlab-org/terraform-images/releases/1.5:latest`
- Install mustache template tools (in bash)
- Add a run.sh script
	- Template all `$CI_PROJECT_DIR/$TEMPLATE_SOURCE_DIR/*.secrets.auto.tfvars.template` => `$CI_PROJECT_DIR/$TEMPLATE_SOURCE_DIR/*.auto.tfvars`
	- Move all `$CI_PROJECT_DIR/$TEMPLATE_SOURCE_DIR/*.auto.tfvars` => `$CI_PROJECT_DIR/$TF_ROOT/` folder
	- Run `gitlab-terraform` with forward arguments pass to `run.sh`


[git.promonni : Mustache Gitlab Terraform Docker](https://git.promonni.com/ass/docker/mustache-gitlab-terraform-docker)



## Use custom docker image into gitlabci.yml

Add
```yaml
  image: 
    name: registry.promonni.com/ass/docker/mustache-gitlab-terraform-docker:main
    entrypoint: [""]
  script:
    - /usr/local/bin/run.sh validate
```

in the following jobs
- validate
- build 
- deploy


> [!example] 
>  ```yaml
> validate:
>   extends:
>     - .terraform:validate
>   image: 
>     name: registry.promonni.com/ass/docker/mustache-gitlab-terraform-docker:main
>     entrypoint: [""]
>       script:
>         - /usr/local/bin/run.sh validate
>   needs: []
> ```



> [!warning] 
> Don't forget to add the project that want to use the image into `Settings > CI/CD > Token Access > Project With Acess` 
> 
> Otherwise it will not provide `CI_REGISTRY_TOKEN` permission to acess the registry
> 
> NOTE: Because `CI_REGISTRY_TOKEN` uses `CI_JOB_TOKEN` to authenticate, the access configuration also applies to `CI_REGISTRY_TOKEN`.




# Exemple

```yaml
include:
  - template: Terraform/Base.gitlab-ci.yml # https://gitlab.com/gitlab-org/gitlab/blob/master/lib/gitlab/ci/templates/Terraform/Base.gitlab-ci.yml
  - template: Jobs/SAST-IaC.gitlab-ci.yml # https://gitlab.com/gitlab-org/gitlab/blob/master/lib/gitlab/ci/templates/Jobs/SAST-IaC.gitlab-ci.yml

variables:
  TF_ROOT: terraform
  GIT_SUBMODULE_STRATEGY: normal
  TF_STATE_NAME: staging
  TF_CACHE_KEY: staging
  TEMPLATE_SOURCE_DIR: variables/$TF_STATE_NAME

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
  extends:
    - .terraform:validate
  image: 
    # name: monnierant/mustache-gitlab-terraform:latest
    name: registry.promonni.com/ass/docker/mustache-gitlab-terraform-docker:main
    entrypoint: [""]
  script:
    - /usr/local/bin/run.sh validate
  needs: []

build:
  extends:
    - .terraform:build
  image: 
    # name: monnierant/mustache-gitlab-terraform:latest
    name: registry.promonni.com/ass/docker/mustache-gitlab-terraform-docker:main
    entrypoint: [""]
  script:
    - /usr/local/bin/run.sh plan
    - /usr/local/bin/run.sh plan-json
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
  extends:
    - .terraform:deploy
  image: 
    # name: monnierant/mustache-gitlab-terraform:latest
    name: registry.promonni.com/ass/docker/mustache-gitlab-terraform-docker:main
    entrypoint: [""]
  script:
    - /usr/local/bin/run.sh apply
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
- [git.promonni : Mustache Gitlab Terraform Docker](https://git.promonni.com/ass/docker/mustache-gitlab-terraform-docker)
- [git.promonni : Simple SSH](https://git.promonni.com/ass/terraform/simple-ssh)



## West : Similar

## East : Opposite

## North : Theme / Question

- [[Gitlab CICD - Use terraform workflow]]

## South : What does it lead to


# github-actions

Public repository for reusable github actions 

As is customary for GitHub Actions, we provide release tags for you to reference in your repository's workflow files. The `v1` tag is a moving tag that will always apply to the latest version 1 train release.

## Usage

```yml
jobs:
  ecr-push:
    uses: Fatsoma/reusable-actions/.github/workflows/ecr-push.yml@v1
    with:
      aws-region: us-west-1
      ecr-repository: ${{ github.event.repository.name }}
      environment: staging
      image-tag: latest
```

You can use custom docker build instructions with a `ci-docker-build` make target:

```make
CI_DOCKER_IMAGE=

.PHONY: ci-docker-build
ci-docker-build:
	docker build --tag "$(CI_DOCKER_IMAGE)" .
```

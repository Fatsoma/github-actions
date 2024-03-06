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

  ruby-gem-publish:
    on:
      push:
        branches: main
    uses: Fatsoma/reusable-actions/.github/workflows/ruby-gem-publish.yml@v1
    with:
      gem-name: example-gem

  ruby-lint:
    uses: Fatsoma/reusable-actions/.github/workflows/ruby-lint.yml@v1

  ruby-vulnerabilities:
    uses: Fatsoma/reusable-actions/.github/workflows/ruby-vulnerabilities.yml@v1

  ruby-test:
    uses: Fatsoma/reusable-actions/.github/workflows/ruby-test.yml@v1
```

You can use custom docker build instructions with a `ci-docker-build` make target:

```make
CI_DOCKER_IMAGE=

.PHONY: ci-docker-build
ci-docker-build:
	docker build --tag "$(CI_DOCKER_IMAGE)" .
```

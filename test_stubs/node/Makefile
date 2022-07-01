PACKAGE_DIR=src
DOCKER_TAG=$$(cat ./package.json | yq '.name'):$$(cat ./package.json | yq '.version')

.PHONY: lint-docker
lint-docker:
	@hadolint ./Dockerfile

.PHONY: build-docker
build-docker:
	@docker build --no-cache -t $(DOCKER_TAG) .

.PHONY: scan-docker
scan-docker:
	@docker run --rm -v /var/run/docker.sock:/var/run/docker.sock \
       goodwithtech/dockle:v0.4.5 --no-color $(DOCKER_TAG)
	@trivy image --ignore-unfixed $(DOCKER_TAG)

.PHONY: docker
docker: lint-docker build-docker scan-docker

pre-commit:
	@npm-run-all format lint test
	@make docker


.PHONY: run-docker
run-docker:
	@docker run --rm $(DOCKER_TAG)
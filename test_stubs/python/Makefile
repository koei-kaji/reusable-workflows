PACKAGE_DIR=$$(poetry version | sed 's/-/_/g' | awk '{print $$1}')
DOCKER_TAG=$$(poetry version | awk '{print $$1":"$$2}')

.PHONY: format
format:
	@poetry run isort .
	@poetry run black .

.PHONY: format-check
format-check:
	@poetry run isort --check .
	@poetry run black --check .

.PHONY: lint
lint:
	@poetry run pylint -d C,R,fixme $(PACKAGE_DIR) tests
	@poetry run mypy --show-error-codes $(PACKAGE_DIR) tests

.PHONY: test
test:
	@poetry run pytest tests

.PHONY: lint-docker
lint-docker:
	@hadolint ./Dockerfile

.PHONY: build-docker
build-docker:
	@docker build --no-cache -t $(DOCKER_TAG) .

.PHONY: scan-docker
scan-docker:
	@dockle $(DOCKER_TAG)
	@trivy image --ignore-unfixed $(DOCKER_TAG)

.PHONY: docker
docker: lint-docker build-docker scan-docker

.PHONY: pre-commit
pre-commit: format lint test docker

.PHONY: run
run:
	@poetry run python python_stub/hello.py

.PHONY: run-docker
run-docker:
	@docker run --rm $(DOCKER_TAG)
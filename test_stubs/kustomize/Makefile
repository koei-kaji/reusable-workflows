.PHONY: build
build:
	@kustomize build ./overlays/dummy/ > ./.assets/dummy.yaml

# https://github.com/instrumenta/kubeval/issues/301#issuecomment-1079674123
.PHONY: validate
validate:
	@kubeval \
	  --schema-location https://raw.githubusercontent.com/yannh/kubernetes-json-schema/master \
	  --ignore-missing-schemas \
	  ./.assets/*

fix:
	@cd ./base/ && kustomize edit fix
	@cd ./overlays/dummy/ && kustomize edit fix

.PHONY: pre-commit
pre-commit: fix build validate
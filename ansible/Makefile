.PHONY: configure login clone-repos make-and-push-images deploy clone-build-push-deploy

PROJECT ?= my-project
TAG ?= latest
BRANCH ?= release/2018.1

configure:
	python -m pip install ansible docker-py

login:
	docker login harbor.testing.cmios.ru:443

clone-repos: guard-INVENTORY
	ansible-playbook -i $(INVENTORY) plays/clone-repos.yml -e 'PROJECT=$(PROJECT) BRANCH=$(BRANCH)'

make-and-push-images: guard-INVENTORY
	ansible-playbook -i $(INVENTORY) plays/make-and-push-images.yml -e 'PROJECT=$(PROJECT) TAG=$(TAG)'

deploy: guard-INVENTORY
	ansible-playbook -i $(INVENTORY) plays/deploy.yml -e 'PROJECT=$(PROJECT) TAG=$(TAG) BRANCH=$(BRANCH)'

clone-build-push-deploy: clone-repos make-and-push-images deploy

guard-%:
	@ if [ "${${*}}" = "" ]; then \
		echo "Variable $* not set"; \
		exit 1; \
	fi
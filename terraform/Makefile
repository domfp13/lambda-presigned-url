#####################################################
# Makefile containing shortcut commands for project #
#####################################################
# Created By Enrique Plata

# MACOS USERS:
#  Make should be installed with XCode dev tools.
#  If not, run `xcode-select --install` in Terminal to install.

# WINDOWS USERS:
#  1. Install Chocolately package manager: https://chocolatey.org/
#  2. Open Command Prompt in administrator mode
#  3. Run `choco install make`
#  4. Restart all Git Bash/Terminal windows.


.DEFAULT_GOAL := help

.PHONY: tf-init
tf-init: ## Initialize Terraform
	@ docker-compose run --rm terraform init

.PHONY: tf-fmt
tf-fmt: ## Format files in terraform
	@ docker-compose run --rm terraform fmt

.PHONY: tf-validate
tf-validate: ## Validate Terraform file is valid
	@ docker-compose run --rm terraform validate

.PHONY: tf-plan
tf-plan: ## Run Terraform plan
	@ docker-compose run --rm terraform plan

.PHONY: tf-refresh
tf-refresh: ## Run Terraform refresh
	@ docker-compose run --rm terraform refresh

.PHONY: tf-apply-ecr
tf-apply-ecr: ## Run Terraform apply only for ECR, since its a dependecy
	@ docker-compose run --rm terraform apply -target=aws_ecr_repository.de_presigned_url_ecr

.PHONY: tf-apply
tf-apply: ## Run Terraform apply
	@ docker-compose run --rm terraform apply

.PHONY: tf-destroy
tf-destroy: ## Run Terraform destroy
	@ docker-compose run --rm terraform destroy

help:
	@ echo "Please use \`make <target>' where <target> is one of"
	@ perl -nle'print $& if m{^[a-zA-Z_-]+:.*?## .*$$}' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m  %-25s\033[0m %s\n", $$1, $$2}'

BUILD_TEMP=./.aws-sam
BUCKET={{cookiecutter.deployment_bucket}}
REGION={{cookiecutter.aws_region}}
STACK_NAME={{cookiecutter.application_name}}

# Syntax highlighting. MacOS ships with an old version of Bash that doesn't
# support the \e escape so we need to use this other escape sequence.
ifeq ("$(strip $(shell uname))","Darwin")
ESC=\x1B
else
ESC=\e
endif

# These are mainly just used to create a headline for each target so it's a
# little easier to visually sort through the output.
BOLD=$(ESC)[1m
CYAN=$(ESC)[36m
NORMAL=$(ESC)[0m

all: clean format dist deploy ## Build everything
dist:  ## Build the distribution package
	@echo "\n~~~ $(BOLD)$(CYAN)Building distribution package$(NORMAL) ~~~"
	sam build

deploy:  ## Deploy the package
	aws s3api create-bucket --create-bucket-configuration LocationConstraint=$(REGION) --acl private --bucket $(BUCKET) || true
	sam deploy --stack-name $(STACK_NAME) --s3-bucket $(BUCKET) --capabilities CAPABILITY_IAM

format:
	find . -name "*.py" |xargs black -l 79
	isort .

clean:
	@echo "\n~~~ $(BOLD)$(CYAN)Cleaning up$(NORMAL) ~~~"
	rm -rf $(BUILD_TEMP)

.PHONY: help

help:
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'

.DEFAULT_GOAL := help


# lambda-template-sam

[Cookiecutter](https://github.com/cookiecutter/cookiecutter) template for a basic [Lambda](https://aws.amazon.com/lambda/) function with a [SAM](https://aws.amazon.com/serverless/sam/) template and a [Makefile](https://www.gnu.org/software/make/manual/make.html).

To use this repo

  1. Clone this repo
  1. Install cookiecutter, if you don't already have it.

        `pip install cookiecutter`

  1. Run cookiecutter on this repo

        `cookiecutter .`

What results will be a new directory named according to the application_name
variable you populated in cookiecutter.json. You can create a new Git repo from
this directory and push it to a blank repo created in GitHub or whatever.

      git .
      git add *
      git commit -m "Initial commit"
      git branch -M main
      git remote add origin https://github.com/digitizdat/my-new-project.git
      git push -u origin main

You can deploy the sample Lambda function without modification. If your environment has current AWS credentials in it, simply run `make all`.

      make all

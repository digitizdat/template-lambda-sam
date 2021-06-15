# testproject-lambda-template

To use this repo

  1. Clone this repo
  1. Change the cookiecutter.json file to suit your needs
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

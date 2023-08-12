# Project Name

Project repository for [insert client name]. This project was generated using the Valkyrie Project Template. Please review the Project Guidelines and Set-Up instructions carefully.
All standards and best practicies are outlined in  `docs/standard.md`. 

## Project Guidelines
* Pull in the `main` branch regularly to keep your branch up to date.
* Add new packages with the command `poetry add <package_name>`. This will automatically update `pyproject.toml` and  `requirements.txt`; you do not need to manually update these files. 
* Be sure to only work on your branch.
* Branches should be short-lived. Once your task is complete submit a PR for a team member to review.
* Create a self-titled folder in the notebooks folder for your work. 
* Include docstrings and comments in your code.
* Never commit data to the repo. All data should be in the data folder.
* Don't commit any credentials or your local configuration to your repository. Keep all your credentials and local configuration in `.envrc`


## Set Up Instructions

Follow these steps to set up the repository on your local machine:

1. Clone the repository 
```
git@github.com:ValkyrieIntelligence/project_name.git
```

2. Go into the `project_name` folder and checkout your own branch 
```
cd project_name
git checkout -b [branch_name]
```

3. Verify that poetry shell is available and we can run/build the project without issues.

    - Use `poetry install` to install relevant packages/dependencies to your poetry virtual environment.
    - Then `poetry shell` will spawn a shell with the virtual environment necessary to run/buil the project.
    - Finally, you can use `poetry run python ./valkyrie-project-template/example_script.py` to execute that the project runs/builds on your local machine with the specified poetry environment. If the program returns `Hello World` then you have successfully set up your project! 
    - To deactivate the virtual environment and exit this new shell type `exit`. To deactivate the virtual environment without leaving the shell use `deactivate`.

4. Create a `.envrc` file in the project's root directory. Can be done via `touch .envrc` or via the text editor of your choice.

    - Write or append any necessary local environment variable to this file, as this will contain them within the local scope of the project. Make sure to use best-practices when sharing sensitive information. See the `sample.envrc` for more information. 

5. Check if `nbstripout` is installed in the current repository (status shows path to repository, filters, and attributes if installed):
```
nbstripout --status
```

6. Finally publish your local branch 
```
git push --set-upstream origin [branch_name]
```



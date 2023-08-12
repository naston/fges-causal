# Project Setup
This readme will walk through the process of setting up a project repository for the first time. Day-to-day activity and best-practices is elucidated within `STANDARDS.md`. The `docs/project_README.md` should be used once the initial set up is complete. 


## Prerequisites
The following prerequisites should be met in order to get started with project set-up.

- A shell of your choice. Since we are a Mac-shop this will probably be `zsh` or `bash`. I recommend setting up `oh-my-zsh` for the additional developer tools and tab-completions that it comes with, but not necessary.

- The latest Python version, or any Python version >=3.10, since these are the most feature-complete and stable releases. You can check this with `python --version`. If out of date, google how to upgrade default Python version for your system. An article that can guide you through updating your default Python and Pip versions is found [here](https://opensource.com/article/19/5/python-3-default-mac) 

- The latest compatible Poetry version. Poetry is a tool for dependency management and packaging in python. It ensures repeatable environments from machine-to-machine, and can build your projects for distribution. More about obtaining and setting up `poetry` [here](https://python-poetry.org/docs/).

- An environment manager, like `direnv`. Creating per-project, isolated development environments is critical to maintaining safe coding practices. Tools like `direnv` allow you to specify all your sensitive project materials (API keys, database credentials, etc.) in a `.envrc` file. By isolating these variables to `.envrc` we can prevent leaking information and clogging up your `.zsh_profile` or `.bash_profile`. To install `direnv` 
follow the instructions [here](https://direnv.net/docs/installation.html)

- A GitHub account with `ssh` access set up. This is going to be our new standard since it is much more secure than using `https` for GitHub activities. Read more about setting this up [here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh).


## Creating the project repository
Once all prerequisites have been met, complete the following steps:

1. Create a new empty repository 
    - on Github.com (We will use `example-project` for the new repo name)
    - on local machine 
    ```
    mkdir example-project
    cd example-project
    git init
    git remote add origin git@github.com:example-project.git

    ```

2. Create a bare clone of the template repository outside of the example-project folder:
```
cd ..

git clone --bare git@github.com:naston-project-template.git

```

3. Mirror-push to the new repository:
```
cd naston-project-template
git push --mirror git@github.com:example-project.git

```

4. Remove the local template repository
```
cd ..
rm -r naston-project-template.git

```

5. Pull in changes from origin to the `example-project`
```
cd example-project
git pull origin main
git checkout main

```

6. Change the directory names 
    - update the `pyproject.toml` file
    - rename `naston_project_template` src folder to project name (ie. `example_project`)

7. Replace the template `README.md` with an updated version of the `docs/project_README.md`     

8. Verify that poetry shell is available and we can run/build the project without issues.

    - Use `poetry install` to install relevant packages/dependencies to your poetry virtual environment.
    - Then `poetry shell` will spawn a shell with the virtual environment necessary to run/buil the project.
    - Finally, you can use `poetry run python example_project/example_file.py` to execute that the project runs/builds on your local machine with the specified poetry environment. If the program returns `Hello World` then you have successfully set up your project! 

8. Push Changes to origin
```
git add .  
git commit -m "initial project setup"
git push origin main
```

9. Delete all other branches except `main` via github.com


## Contributors
- Nathan: <nathan@planetpaull.com>
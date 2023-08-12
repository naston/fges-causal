# Project Standards

## Development Workflow
Describes the recommended process and best practices for developers to follow throughout the software development lifecycle, including planning, coding, reviewing, and merging code.

1. Assuming you have followed the project setup tutorial found in `SETUP.md`, the next step is for you to create a new feature branch to begin your work. This can be done with `git checkout -b <your-branch-name>`. For naming conventions and best practices, check the "GitHub" section.
2. Now that you have your own branch, you can work. Three top-level directories exist for development: 
    - `notebooks`: For EDA and *prototyping*. All work in notebooks should be considered as part of the software system for your project. They are step one of our work.
    - `src` or `your-project-name`: For applications and/or packages that we develop during our work. Data pipelines, ML models, and more are candidates for a `src` folder.
    - `tests`: Deeply connected to your `src` folder. This is where we add unit-tests and integration tests. Please write good tests! 
3. When running or testing the code you write, utilize `poetry shell` to create the virtual environment for your project. You might need to `poetry install` packages if any are missing.
4. Now that you've written some code, and hopefully some tests, it's time for a Continuous Integration (CI) check. With Poetry you can run these checks anytime using `poetry run pre-commit run --all-files` in your terminal. These checks exists to keep our team aligned with development standards and practices, for more information see the "Continuous Integration" section. 
5. However, I recommend relying on the `.pre-commit-hooks.yaml` at commit time for two reasons: (1) you are committing your work early and often, which is *great* git practice, and (2) you don't need to interrupt your developer workflow to make and correct CI checks. So, when you are ready to commit some changes to your branch `git commit -m "Please write good commit message"` while automatically trigger your CI, and tell you whether or not your code is compliant with standard CI. 

## GitHub
Provides guidelines and instructions for using GitHub effectively as a version control system, including creating branches, submitting pull requests, resolving conflicts, and managing project repositories.

- Creating Branches: `git checkout -b <your-branch-name>`, but make sure to `git checkout main && git pull` to be sure your new branches are up to date.
- Submitting PRs: When your code is ready to be committed to `main`, you can `git push` your branch and create a pull request to the `main` branch. This will trigger both the project's main CI actions, and notfiy another member of your PR. **ALWAYS** have another individual get eyes on your code before committing to `main` and ensure CI coverage.
- Merging Changes: Whenever the main branch is updated run these lines:

```
git checkout main
git pull origin
git checkout [your-current-branch]
git rebase main
```
- Resolving Conflicts: Godspeed. Using the VS Code Editor can help identify and resolve merge conflicts. 
- Managing Project Repositories: Seek the help of a GitHub admin for helping creating or managing repositories.

## Continuous Integration
Explains the implementation of continuous integration practices, tools, and pipelines to ensure that changes made by developers are regularly integrated into a shared codebase, allowing for early detection of integration issues. The following sections cover each of topics in greater detail.

All work in projects should have a valid `.pre-commit-hooks.yaml` for local CI checks prior to committing code to our remote repositories. Local checks should be used in the development loop frequently to ensure you don't drift too far into technical debt. 

Repository level CI checks are powered by GitHub Actions, which are specified in `.github/workflows`, and should **not** be altered without consulting a GitHub administrator. These YAML files are there to be the standard for coding practices and should ensure that we all produce to high-quality work. We currently enforce protection on the `main` branch only.

## Linting
Defines the linting standards and tools to enforce code quality and style consistency, identifying potential errors, and maintaining a high level of code readability and maintainability.

The tool of choice for linting is `ruff` because it's fast, customizable, and accurate. Use `poetry run ruff check <file-or-folder-to-lint>` to run linting yourself. You can also see `ruff check --help` for a list of helpful arguments; `--fix` is a common argument that can automattically attempt to fix the errors.

This section is in flux, but we aim to have more definition as the tool is used. 

## Formatting
Specifies the code formatting guidelines, tools, and configurations to ensure consistent and uniform code style throughout the project, enhancing readability and reducing code review friction.

The tool of choice is the `black` formatter. 

This section is in flux, but we aim to have more definition as the tool is used. 

## Testing
Outlines the recommended testing strategies, frameworks, and tools to ensure the quality and reliability of the software by validating its behavior, performance, and correctness through unit tests, integration tests, and other relevant testing approaches.

The tool of choice is `pytest`. 

This section is in flux, but we aim to have more definition as the tool is used. 

## Auditing
Describes the process and tools used to perform security and compliance audits, including vulnerability scanning, code analysis, and adherence to relevant standards or regulations, ensuring the project's security and reliability.

Tool not currently defined. 

This section is in flux, and we aim to find a viable solution soon. 

## Miscellaneous 
Covers any additional project standards that do not fit into the other sections, such as documentation guidelines, versioning conventions, code review processes, deployment practices, or any other relevant information that contributes to the project's success.

This section is in flux, but we aim to have more definition as the tool is used. 
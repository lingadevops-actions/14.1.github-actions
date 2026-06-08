# GitHub Actions Basics

* GitHub Actions is a tool provided by GitHub that helps automate tasks in your repository.

For example, whenever you push code to GitHub, it can automatically:
Run tests
Build your project
Deploy your application
Check code quality

Think of it as:
"When something happens in my repository, automatically do these tasks."

Basic Terms
1.Workflow: A workflow is a set of automated steps.

Workflow files are stored in:
.github/workflows/

Example:
.github/workflows/hello.yml

2.Trigger: A trigger decides when the workflow should run.

Example:
on:
  push:

This means: Run the workflow whenever code is pushed to GitHub.

3.Job: A workflow contains one or more jobs.

Example:
jobs:
  hello:

4. Runner: A runner is the machine that executes the job.

runs-on: ubuntu-latest

GitHub creates a temporary Ubuntu machine and runs your commands there.

Steps

Steps are the individual tasks inside a job.

steps:
  - run: echo "Hello World"
Hello World Example

Create a file:

.github/workflows/hello.yml

Add the following code:

name: Hello World

on:
  push:

jobs:
  hello:
    runs-on: ubuntu-latest

    steps:
      - name: Print Message
        run: echo "Hello World!"
How It Works
You push code to GitHub.
git add .
git commit -m "first workflow"
git push
GitHub detects the push.
It starts the workflow.
An Ubuntu runner is created.
The command runs:
echo "Hello World!"
You can see the result in the Actions tab of your repository.

Output:

Hello World!
Using Repository Code

Most workflows need access to the repository files.

steps:
  - uses: actions/checkout@v4

  - run: ls

actions/checkout downloads your repository code to the runner.

Simple Python Example

Suppose you have:

hello.py

print("Hello from Python")

Workflow:

name: Python Demo

on:
  push:

jobs:
  run-python:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-python@v5
        with:
          python-version: "3.12"

      - run: python hello.py

Output:

Hello from Python
Workflow Structure
name: My Workflow

on:
  push:

jobs:
  demo:
    runs-on: ubuntu-latest

    steps:
      - run: echo "Hello"

Structure:

Workflow
 ├── Trigger
 ├── Job
 │    ├── Runner
 │    └── Steps
In One Line

GitHub Actions = Trigger + Job + Steps

Example:

Push Code
    ↓
Start Workflow
    ↓
Run Commands
    ↓
Show Results

That's the core idea. Once you understand this Hello World example, learning testing, building, and deployment workflows becomes much easier.



# Are Jenkins and GitHub Actions the same? What is the difference between them?
* They are similar in purpose but not the same.
* Jenkins — a self-hosted, open-source CI/CD automation server that you install and manage yourself.
* GitHub Actions — a built-in CI/CD platform inside GitHub that runs workflows directly from GitHub repositories.

Very short difference:
Jenkins = more flexible, more setup and maintenance.
GitHub Actions = easier to use, less maintenance, tightly integrated with GitHub.
Both automate building, testing, and deploying software (CI/CD).

### Task 2: Hello Workflow
Create `.github/workflows/hello.yml` with a workflow that:
1. Triggers on every `push`
2. Has one job called `greet`
3. Runs on `ubuntu-latest`
4. Has two steps:
   - Step 1: Check out the code using `actions/checkout`
   - Step 2: Print `Hello from GitHub Actions!`

Push it. Go to the **Actions** tab on GitHub and watch it run.

**Verify:** Is it green? Click into the job and read every step.

```YAML
name: Hello Workflow

on:
  push:

jobs:
  greet:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Say Hello
        run: echo "Hello from GitHub Actions!"
```

---

### Task 3: Understand the Anatomy
Look at your workflow file and write in your notes what each key does:
- `on:`
    - Defines when the workflow should trigger.
    - Example: push means it runs every time code is pushed to the repo.
- `jobs:`
    - Defines the tasks (jobs) the workflow will execute.
    - A workflow can have one or multiple jobs that run in parallel or sequence.
- `runs-on:`
    - Specifies the operating system/environment where the job runs.
    - Example: ubuntu-latest means the job runs on a Linux virtual machine.
- `steps:`
    - Defines the individual actions inside a job.
    - Each job is broken into multiple steps executed in order.
- `uses:`
    - Used to call a pre-built action from GitHub Marketplace.
    - Example: actions/checkout downloads your repository code into the runner.
- `run:`
    - Executes a command or script directly inside the runner.
    - Example: echo "Hello" runs a shell command.
- `name:` (on a step)
    - Gives a readable label to the step.
    - It helps you understand what is happening when viewing the workflow in the Actions tab.

---

### Task 4: Add More Steps
Update `hello.yml` to also:
1. Print the current date and time
2. Print the name of the branch that triggered the run (hint: GitHub provides this as a variable)
3. List the files in the repo
4. Print the runner's operating system

Push again — watch the new run.

---

### Task 5: Break It On Purpose
1. Add a step that runs a command that will **fail** (e.g., `exit 1` or a misspelled command)
2. Push and observe what happens in the Actions tab
3. Fix it and push again

Write in your notes: What does a failed pipeline look like? How do you read the error?

- The workflow will start normally
- All previous steps will pass
- The Break the build intentionally step will FAIL
- The whole pipeline turns RED
- Job status becomes Failed

---
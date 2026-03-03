# Day 39 – What is CI/CD?

## Challenge Tasks

### Task 1: The Problem
Think about a team of 5 developers all pushing code to the same repo manually deploying to production.

Write in your notes:
1. What can go wrong?

- Someone deploys the wrong branch
- Code conflicts between developers
- Forgetting to pull latest changes before deploy
- Missing environment variables in production
- Different dependency versions
- Human mistakes during deployment steps
- No proper testing before release
- Production downtime due to errors

2. What does "it works on my machine" mean and why is it a real problem?

- Different OS (Windows/Linux/Mac)
- Different dependency versions
- Different database versions (e.g., PostgreSQL 14 vs 16)
- Missing environment variables
- Different configurations

3. How many times a day can a team safely deploy manually?

- 1–2 times per day (maximum)
- Because:
   - Manual process takes time
   - Needs careful checking
   - High risk if done repeatedly
   - Stress increases with frequency

---

### Task 2: CI vs CD
Research and write short definitions (2-3 lines each):
1. **Continuous Integration** — what happens, how often, what it catches

- Definition:
    - Continuous Integration is the practice of automatically building and testing code every time developers push changes to the repository. It usually happens multiple times a day.

- What it catches:
    - Build failures
    - Broken tests
    - Integration conflicts between developers

- Real-world example:
    - When a developer pushes code to GitHub, a tool like GitHub Actions automatically runs unit tests and checks if the build passes before merging.

2. **Continuous Delivery** — how it's different from CI, what "delivery" means

- Definition:
    - Continuous Delivery ensures that code is always in a deployable state. After CI passes, the application is automatically prepared and pushed to a staging or production-ready environment — but release to users requires manual approval.

- How it's different from CI:
    - CI focuses on testing and integration.
    - Delivery focuses on making the software ready to release anytime.

- Real-world example:
    After tests pass, the app is automatically deployed to a staging server. A manager clicks “Approve” to release it to production using tools like Jenkins.

3. **Continuous Deployment** — how it differs from Delivery, when teams use it
Write one real-world example for each.

- Definition:
    - Continuous Deployment automatically releases every change that passes tests directly to production — without manual approval.

- How it's different from Delivery:
    - Delivery = manual approval before production.
    - Deployment = fully automatic release to users.

- When teams use it:
    - Mature DevOps teams
    - Strong automated testing setup
    - SaaS products with frequent updates

- Real-world example:
    - A company like Netflix automatically deploys small updates to production whenever all automated tests pass.

---

### Task 3: Pipeline Anatomy
A pipeline has these parts — write what each one does:
- **Trigger** — what starts the pipeline
- **Stage** — a logical phase (build, test, deploy)
- **Job** — a unit of work inside a stage
- **Step** — a single command or action inside a job
- **Runner** — the machine that executes the job
- **Artifact** — output produced by a job

---

### Task 4: Draw a Pipeline
Draw a CI/CD pipeline for this scenario:
> A developer pushes code to GitHub. The app is tested, built into a Docker image, and deployed to a staging server.

Include at least 3 stages. Hand-drawn and photographed is perfectly fine.

![alt text](<ChatGPT Image Mar 3, 2026, 06_35_02 PM.png>)

---

### Task 5: Explore in the Wild
1. Open any popular open-source repo on GitHub (Kubernetes, React, FastAPI — pick one you know)
2. Find their `.github/workflows/` folder
3. Open one workflow YAML file
4. Write in your notes:
   - What triggers it?
        - A code push to the repository
        - Scheduled run (cron job)
        - Manual trigger
   - How many jobs does it have?
        - Build job
        - test job

   - What does it do? (best guess)
        - Pull latest code from repo
        - Install dependencies
        - Run tests
        - Build the application
        - Create Docker image (if used)
        - Push image to registry
        - Deploy to staging or production

---


# learn_gtihub_actions
to learn github actions

# Key Components:
Workflows, Jobs, Steps
Workflow -> Jobs -> Steps

Workflow: Can be many workflows which belongs to a repo. Triggered upon events. Ex: new commit to a Branch.
Jobs: It can have multiple jobs withing the workflow. A Runner execution environment. Can be conditional.
Steps: Actual actions within the Jobs which is executed.

Removed all Actions steps and disabled the git actions.


# First Git Actions: 

name: <name-of-workflow> => name of the workflow
"on: workflow_dispatch" => To manually triggering the workflow


jobs:
  first-job: => job name
  runs-on: ubunntu-latest => runner name
  steps:
    - name: First Step => name of the step
      run: echo "Hello" => command to trigger
    - name: Second Step
      run: | => For multi-line command steps to execute.
        echo "first command"
        echo "2nd command"
        echo "3rd command"


Reference: 
https://docs.github.com/en/actions/reference/events-that-trigger-workflows - (list of actions which can be triggered.)
https://docs.github.com/en/actions/how-tos/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners - (list of runners)


# Actions with push: - pull code from the repo

name: Test Project => name of the workflow
on: push => event of the workflow
jobs: => 
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Get code
        uses: actions/checkout@v4


Ref: https://github.com/marketplace/actions/checkout - (actions workflow)

# (continued) Configuring NodeJS Step

name: Install nodejs
uses: actions/setup-node@v4
with:
  node-version: 18

Ref: https://github.com/actions/setup-node - (search in google - "github actions install nodejs")

# (continued) - Install dependencies

- name: Install dependent packages
  run: npm ci

# (continued) - more than 1 job

jobs: => 2nd job
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Build
        uses: node build

# (continued) - parallel build(default) vs sequential

- for executing job one after the other, "needs" is the key required to be added.

example:

jobs: =>
  test: => 1st job name
    ....
    ....
  deploy: => 2nd job name
    needs: test => requires the 'test' job to be success and runs sequentially.
    runs-on: ubuntu-latest




      

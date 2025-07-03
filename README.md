# learn_gtihub_actions
to learn github actions

# Key Components:
Workflows, Jobs, Steps

Workflow: Can be many workflows which belongs to a repo. Triggered upon events. Ex: new commit to a Branch.
Jobs: It can have multiple jobs withing the workflow. A Runner execution environment. Can be conditional.
Steps: Actual actions within the Jobs which is executed.

Removed all Actions steps and disabled the git actions.


First Git Actions: 

name: <name-of-workflow> => name of the workflow
"on: workflow_dispatch" => To manually triggering the workflow


jobs:
  first-job: => job name
  runs-on: ubunntu-latest => runner name
  steps:
    - name: First Step => name of the step
    - run: echo "Hello" => command to trigger


Reference: 
https://docs.github.com/en/actions/reference/events-that-trigger-workflows - (list of actions which can be triggered.)
https://docs.github.com/en/actions/how-tos/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners - (list of runners)

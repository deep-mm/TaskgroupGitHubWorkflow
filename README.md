# TaskgroupGitHubWorkflow

This is an example to show how can one use taskgroups/template in GitHub workflows similar to how it is possible in Azure DevOps

If you are someone coming from Azure DevOps world to GitHub DevOps tools, 2 major things you would be missing are variable groups and templates. This repository demonstrates how we can get these two features in GitHub by utilizing actions available in GitHub marketplace.

There are 2 methods to achieve this:

## GitHub Composite Action

GitHub Composite action allows one to create a template file containing composite actions. This template file in GitHub is known as a composite action. A composite action takes an input of a variable, and then we can utilize these variables to run same set of actions but in different environments.
For our example, we have created a composite action called [deploy-azure](https://github.com/deep-mm/TaskgroupGitHubWorkflow/blob/main/.github/actions/deploy-azure/action.yml).

This action takes an input of variable environment, which is then utilized in subsequent steps.
This action has 3 composite steps:

1. Echo output
2. Set environment variables - depending on variable input select the variable group
3. Create resource group - depending on variable input deploy the resource group

Then this composite action is utilized in our main workflow [Template-Action-Composite](https://github.com/deep-mm/TaskgroupGitHubWorkflow/blob/main/.github/workflows/template-new.yml), in all three jobs release_dev, release_qa & release_prd. The only change being in the input provided to the composite action.

## Running single workflow in different environments

![Template Workflow Diagram](https://user-images.githubusercontent.com/29853549/120455739-a54fd680-c3b2-11eb-8875-5de1fb34c20c.png)

Detailed information about the same can be found here: [https://deepmehta.co.in/posts/github-template/](https://deepmehta.co.in/posts/github-template/)

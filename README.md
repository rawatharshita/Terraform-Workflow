# Terraform-Workflow

# PHASE-1: Writing the code and merging to MASTER

DevOps write the terraform code and push it to devop's branch in bitbucket. 
Once code is pushed to devOps's branch, a pull request is raised to merge changes to MASTER branch. 
PR triggers a jenkins job which executes the init, plan, lint and format steps and an email step which sends the email to the team and code reviewer.
After successful review, the merge is performed in MASTER branch. 

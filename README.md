# Terraform-Workflow

# PHASE-1: Writing the code and pushing to bitbucket

1) DevOps writes the terraform code.
2) Push it to devop's branch in bitbucket.

# PHASE-2: Merge Request to MASTER  
3) Once code is pushed to devOps's branch, a pull request is raised to merge changes to MASTER branch. 
4) PR triggers a jenkins job which executes the init, plan, lint and format steps and an email step which sends the email to the team and code reviewer.
5) The terraform code will not be applied at this stage as this is just PR event. The jenkins pipeline has 'terraform apply' stage which is not triggered at this point because it runs only when the triggered branch is MASTER.
6) After successful review, the merge is performed in MASTER branch.

# PHASE-3: MASTER branch triggers pipeline and applies code

7) On commiting the code to MASTER, the jenkins job is triggered which performs- init, plan, tflint and terraform apply.
8) The terraform apply will create the infrastructure now.
9) Send an email to the team.

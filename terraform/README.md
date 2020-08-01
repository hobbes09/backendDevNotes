

# Notes

*TF Config* : Contains road map of how to create and maintain different resources via terraform.

## Commands of Terraform config

#### Refresh
Reconcile terraform view of the world with the real world

#### Plan
Identify the changes needs to be done to reach the desired configuration from the current state of the world.

#### Apply
Actually make updates/creates on real resources of the real world

#### Destroy
Makes a destroy plan and removes all resources created in the real world


## Working of Terraform

#### Design
![Terraform Diagram](https://github.com/hobbes09/backendDevNotes/blob/master/terraform/resources/pic1.png "Terraform Diagram")

#### Module
- Black box of infra-structure
- User needs to define the inputs to the module they are using. (Eg : Configs of Redis, like region, name, cluster config)
- Module gives the expected output variables. (Eg : Redis endpoint)

#### Private Registry
- This are published modules
- Publishers can push standardised modules to a module registry (or catalogue)
- Consumers can consume the modules from the registry

# Important Links

#### First tutorial
- Introduction to HashiCorp Terraform with Armon Dadgar

<a href="http://www.youtube.com/watch?feature=player_embedded&v=h970ZBgKINg" target="_blank"><img src="http://img.youtube.com/vi/h970ZBgKINg/0.jpg"
alt="Introduction to HashiCorp Terraform with Armon Dadgar" width="240" height="180" border="10" /></a>


#### AWS IAM EC2 Instance Role using Terraform

https://medium.com/@devopslearning/aws-iam-ec2-instance-role-using-terraform-fa2b21488536

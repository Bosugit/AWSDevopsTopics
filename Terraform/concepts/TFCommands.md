➡️Useful Terraform commands along with brief explanations:- 

1. terraform init: Initializes a working directory containing Terraform configuration files.
2. terraform plan: Generates an execution plan, outlining actions Terraform will take.
3. terraform apply: Applies the changes described in the Terraform configuration.
4. terraform destroy: Destroys all resources described in the Terraform configuration.
5. terraform validate: Checks the syntax and validity of Terraform configuration files.
6. terraform refresh: Updates the state file against real resources in the provider.
7. terraform output: Displays the output values from the Terraform state.
8. terraform state list: Lists resources within the Terraform state.
9. terraform show: Displays a human-readable output of the current state or a specific resource's state.
10. terraform import: Imports existing infrastructure into Terraform state.
11. terraform fmt: Rewrites Terraform configuration files to a canonical format.
12. terraform graph: Generates a visual representation of the Terraform dependency graph.
13. terraform providers: Prints a tree of the providers used in the configuration.
14. terraform workspace list: Lists available workspaces.
15. terraform workspace select: Switches to another existing workspace.
16. terraform workspace new: Creates a new workspace.
17. terraform workspace delete: Deletes an existing workspace.
18. terraform output: Retrieves output values from a module.
19. terraform state mv: Moves an item in the state.
20. terraform state pull: Pulls the state from a remote backend.
21. terraform state push: Pushes the state to a remote backend.
22. terraform state rm: Removes items from the state.
23. terraform taint: Manually marks a resource for recreation.
24. terraform untaint: Removes the 'tainted' state from a resource.
25. terraform login: Saves credentials for Terraform Cloud.
26. terraform logout: Removes credentials for Terraform Cloud.
27. terraform force-unlock: Releases a locked state.
28. terraform import: Imports existing infrastructure into your Terraform state.
29. terraform plan -out: Saves the generated plan to a file.
30. terraform apply -auto-approve: Automatically applies changes without requiring approval.
31. terraform apply -target=resource: Applies changes only to a specific resource.
32. terraform destroy -target=resource: Destroys a specific resource.
33. terraform apply -var="key=value": Sets a variable's value directly in the command line.
34. terraform apply -var-file=filename.tfvars: Specifies a file containing variable definitions.
35. terraform apply -var-file=filename.auto.tfvars: Automatically loads variables from a file.

**************************************
terrform import command:
   
     terraform import <Resource_type>.<Resource_name> <Resource id>

 

   terraform import aws_instance.instancename instnaceid

   terraform import aws_s3_bucket.my_test_bukcet <bucket_id>



****************************************

terraform refresh:

  it takes the latest changes from remote and it update state file accordingly.rember refresh will not any changes in the remote object.its job is its update only state file.

  but run apply 

  terraform apply--->running apply will remove the changes in state file.why because according to the code it should have only two tags.




******************************************
terraform replace command:

terraform plan -replace="aws_instance.instancename" -out instancename

scanrio:  supoose you having two resouce letassume instance1 and instance2,so you want to some changes only one isntance you can apply terraofrm replace command then you need to apply command

terraform apply filename

**************************************

terrform state remove:

terraform state rm aws_instance.instancename

terraform plan --destroy

***********************************************


file:
terraform plan -var-file="stage.tfvars"

terraform apply -var-file="stage.tfvars"

terrafiorm plan -var-file="prod.tfvars"

plan or apply same



only varialbe:
terraform apply -var="instance_type=t2.micro"

Any doubts you can refer:https://jhooq.com/terraform-input-variables/

**********************************************


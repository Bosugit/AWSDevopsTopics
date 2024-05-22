String:

varaible "instance_type"{

description="instance type t2.micro"
type=String
default="t2.micro"

}

number:

varaible "instance_count"{

description="Ec2 instance count"
type=number
default=2

}


bool:

variable "enable_public_ip"{

description="enalbe publicipaddress"

type=boolean

default=true


}

list:

variables "user_names"
{

description="IAM usernames"
type=list(string)        //here you can mention string,number or boolena also
default=["user1","user2","user3"]

}

usage of list in resource section:

 resource "aws_iam_user" "example"{
    count=length(var.user_names)
    name=var.user_names[count.index]

 }
    



Map:

variable "project_enviornment"
{

    description="project name and enviornment"
    type=map(string)
    default={

        project="project-a",
        environment="dev"
    }
}

usage:
tags = var.project_environment



main.tf
varaiable.tf
terraform.tfvars

we already having varaible.tf file why do you need terraform.tfvars

multiple terraform.tfvars:

dev.tfvars
stage.tfvars
production.tfvars

file:
terraform plan -var-file="stage.tfvars"

terraform apply -var-file="stage.tfvars"

terrafiorm plan -var-file="prod.tfvars"

plan or apply same



only varialbe:
terraform apply -var="instance_type=t2.micro"

Any doubts you can refer:https://jhooq.com/terraform-input-variables/


   

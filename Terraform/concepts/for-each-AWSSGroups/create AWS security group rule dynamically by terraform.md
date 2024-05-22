main.tf:
--------

    variable "map_list"{

        type=map(list(any))
    }

    resosurce "aws_security_group" "example"{

        name="allow_tls"
        description="Allow TLs inboud traffic and outbound traffic"
        vpc_id="vpc-12345"
        tags{
            name="allow_tls"
        }
    }

    resource "aws_security_group_rule" ""example"{
        for_each            =var.map_list
        type                =each.value[0]
        from_port           =each.value[1]
        to_port             =each.value[2]
        protocol            =each.value[3]
        cidr_blocks         =[each.value[4]]
        security_group_id   =aws_security_group.example.id

    }


terraform.dev.tfvars:
---------------

map_list={

rule1=["ingress","80","80","tcp","0.0.0.0/32"]

rule2=["ingress","81","81","tcp","0.0.0.0/32"]

}



terraform plan -var-file="terraform.dev.tfvars" 

terraform apply -var-file="terraform.dev.tfvars" -auto-aprove

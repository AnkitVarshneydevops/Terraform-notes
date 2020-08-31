# Terraform-notes
**Terraform Commands**
By default terraform.tfstate file are in json format. If you want to get in more readable  format, we can use 
**terraform show**:- it provide human-readable format of state or plan file. If you extract some information like public_ip. Then, we write the command 

**terraform show | grep public_ip**

let say aws_instance, I know that something wrong in it. I want to have recreated, so if I do terraform plan, it going to compare the remote state with my local state, as there nothing to do, it is not recreated aws_instances. If I want to recreate this aws_instance. I am going to
use command: terraform taint aws_instance.example then output is “The resource aws
_instance.example in the module root has been marked as tainted!”. So even now terraform plan, it is recreate aws_instance and also recreate volume attach with aws_instance because of creating new instance.

**terraform untaint aws_instance.example**

**terraform graph** :- it generate a graph.	
we can generate a nice png using tools that can interpreted by program called GraphViz.

**terraform refresh:-** if you want to refresh the remote state. It going to look remote state at terraform state locally.

**terraform fmt <filename>:** if you want change format of a file into standard format ( 2 spaces).

**terraform import:** import the exist infrastructure into terraform.tfstate.

For example: if the information of aws_instance such as id, ami, AZ etc is delete in  terraform.tfstate file. Then if you want to run  terraform plan, its plan to create a new instance because it does not know about existing instance. it does not have aws_instance in local tfstate file. Therefore terraform import comes in.
terraform import aws_instance.example <instance-id> . You can find instance-id in AWS Management console.

# tf_interview
Interview questions
# you can tell me about yourself and your exposer  on the terraform and AWS.
# Let get started ,can you please tell me aboy yourself

# Lets start from the basic questions 

# Differece b/w sg and acl

# IAM policies
* In Auto Scaling Instances If we are want to encrypt the EBS volumes we need to  the customet managged key  instead of the AWS managed we need to give the neccessary permmisions to resourced based policy to attach the KMS key to the ebs volumes
* To create custom pilies to restrice the instance to particular region and prevet the deletion of resource like vpc flow logs
* 
# How  do you use policies and create heirarchy
IAM- it's a way of practicing least privilege for users and services. It's highly customisable and has great sets of granularity. Permission boundries can be used to set policies for Org leve

# S3 bucky pvt vs publ
What he saying about public and private S3 is wrong. Private bucket means that only authorized users who have the necessary permissions can read, write, and delete files in the bucket. The bucket policy for a private S3 bucket is set to deny public access, which means that the bucket is secured and can only be accessed by authorized users.

# Can you tell me the difference betwen the public IP, Elastic IP and Private IP
 Elastic IP - Static public IP
 public IP - Dynamic public IP changes every time you restart thc instance
  
 # can you please elebrate where we use the public and private serves
 
 web server that uses Nginx and apache that needs the public connectivity and pulbic subnets
 Private subnet shoud be provate and use in private subnets
 
 # can you please explain VPC and peering
 
A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them using private IPv4 addresses or IPv6 addresses. Instances in either VPC can communicate with each other as if they are within the same network. You can create a VPC peering connection between your own VPCs, or with a VPC in another AWS account. The VPCs can be in different Regions (also known as an inter-Region VPC peering connection).

can we send data from one vpc in one acc to another acc VPC

# Diff IGW and NAT gateway

# Auto scaling diff b/w horizopntal and vertical


# Which lb is best suitable for applicataion load balancer and normal lb 
 
# Lets say you need to create a alete to notify the team how can you do it
For resources utilisation alerts.. we can use cloudwatch alerts NOT cloud trail. CW is all about resources logs where as CTL is all about various AWS sevices API calls logs.

# fine <Name> I came  to know you have very good exposure to <services>
Thank you <Name> Its Nice ir Great talking to you
  


# What is Terraform?

Developed by HashiCorp, Terraform is an open-source Infrastructure-as-Code tool used by legions of DevOps teams to automate infrastructure tasks. This tool allows DevOps teams to deploy a single workflow for their multi-cloud setup. It supports all the leading public and private clouds, including Microsoft Azure, Amazon Web Services, and Google Cloud Platform. 

Terraform can be used to define the entire IT infrastructure in code form. One of the best things about this tool is that it allows the users to build and manage multiple clouds from different providers simultaneously. Furthermore, it allows IaC in HashiCorp Configuration Language (HCL), a human-readable language, simplifying the process.

# 1.What are some best practices for using Terraform? 

Best practices for using Terraform include using modules, versioning your code, using remote state, and following the principle of least privilege.

# 2. How do you manage secrets in Terraform?

Secrets should never be stored in your Terraform configuration files. Instead, you should use a tool like HashiCorp Vault to store and manage secrets.

# 3. What is a Terraform modulation concept and why is play a imp role in provosion the infrastrut

A Terraform module is a set of reusable infrastructure code that can be used to provision resources across multiple projects. 
  It also makes easier to maintain and spot the problems in the large infrastructure files to split one lage into mutliple componet,Its eaisse to troble shoot 
  To split the work and organizing our IAC script

# 4. What is a Terraform provider?

A Terraform provider is a plugin that enables Terraform to manage resources in a particular cloud provider or service.

# 5. What is the architecture of a Terraform project?

## Architecture of Terraform:
Terraform follows a standard architecture to fulfill the necessary IaC tasks. It includes two different components; Terraform Core and Providers. The below section will elaborate on these two components of Terraform and how they perform the desired tasks.

**Terraform Core**: 
When it comes to managing dependencies, Terraform relies heavily on graph theory. The Terraform core is responsible for reading configurations and building the dependency graph.

Working of Terraform Core:-Terraform uses two different input sources for accomplishing its tasks. The primary input source is the input the user gives for configuring Terraform and describing the resources that should be created or provisioned. On the other hand, all the data provided to Terraform regarding the existing infrastructure setup is the second input that this component of Terraform’s architecture uses.

After taking these inputs, this tool decides the actions that should be taken for the infrastructure. In addition, it analyzes the user-specified desired state, performs a quick comparison with the existing state, and sets up the architecture that eradicates the gaps in the infrastructure. In simpler terms, the Terraform Core identifies the things that should be created, modified, or deleted to make the most out of your existing infrastructure.

**Providers**: 
Providers are the second component of the Terraform architecture and are referred to as external individual static binaries. The Terraform core communicates with the plugins through Remote Procedure Call (RPC) when the applying and planning phases are going on. These plugins are written in the Go language. In the Terraform configuration file, every provisioner and provider is a plugin.

Working of Providers :Providers in Terraform are cloud providers like Microsoft Azure or Amazon Web Services. However, they can also be any other platform as a service tool. There are several different providers for different technologies, and they all provide access to the users to the resources. For example, if a user uses AWS, Terraform will gain access to all the EC2 instances within the stack. Afterwards, the user can build infrastructure on several various levels.

This was the entire architecture of Terraform, including the two components; Core and Providers. Though it is not a highly complex architecture, it can help complete the infrastructure setup quickly and just through code.

A Terraform project typically consists of a main configuration file, which defines the desired state of the infrastructure, and one or more module files, which contain reusable code for provisioning resources.

# 6. Terraform Workflow:
There are three different stages in the Terraform Workflow: Write, Review, and Apply. These states are briefly explained below. 

## Stage 1: 
Write– The foremost step in the Terraform workflow includes defining the infrastructure resources as code through HCL. These resources can be across different cloud services and providers.
## Stage 2: 
Review-Terraform will begin displaying the plan to add or remove resources in the next stage. Furthermore, the plan will define the infrastructure created, modified, or destroyed depending on the current configuration and infrastructure.
## Stage 3: 
Apply-The final stage in the Terraform workflow is Apply, where you can determine the planned changes for adding or removing any infrastructure resource. Once approved, the terraform will perform the desired actions in the defined execution order.

# 7 Terraform Best Practices for Amazon Web Services–
Amazon Web Services is another widely used cloud service currently. Here are some of the best Terraform practices you should adopt with AWS.

Split Files Logically: In Terraform, the main file that has the provider and creates the resources is the Main.tf. Having a single file can enhance the complexity of readability. Even though the Terraform code can be written in a single file, one of the Terraform best practices in AWS is to split the files logically. These files are:
Main.tf – locals, call modules, and data sources to create the resources
Variables.tf – This file contains the details of the variables used in the main.tf file.
Outputs.tf – Every output generated in the main.tf from the resources are found in this file.
As mentioned earlier, having a single file may reduce the file’s readability, which is why the best practice is to split the files into these formats for better readability.
Locking the State File: One of the most typical reasons for data loss, conflicts, and state file corruption is having multiple runs on the same state file. When working on a project, you cannot risk data loss. Terraform has a locking feature that can lock the state file and avoid any parallel run of the same state. Only a single member can run the Terraform configurations when a state file is locked, preventing the above mentioned scenarios.
Metadata Extraction: The only data source that extracts data from the Terraform backend is terraform_remote_state. With this source, you can use the root-level output of Terraform configurations as input data for other configurations. Network, application, and database are some of the layers the user needs to manage. Upon creating the basic network resources, the application and the database layer should directly refer to the resource from the vpc layer through the terraform_remote_state data source.
Tag your Amazon Resources: Terraform allows the user to assign custom metadata to every resource as tags. By tagging your AWS resources, you can categorize them in any way you want. Tagging is extremely useful when there are multiple resources of the same type, allowing you to find the desired resource per the assigned tag.

# 8. Terraform file structure 

Terraform file structurecan vary with the project as well as the users. However, a basic structure for any Terraform code is mentioned below:

Variables.tf for defining variables needed by provider resource parameters.
Providers.tf to define providers and their versions.
Examples.tfvars showcases the input values for the variables.
Outputs.tf defines the Terraform output variables.
Locals.tf for local interpolation and variables.
Main.tf will describe the provider resources.

# 9. Which command can be used to reconcile the Terraform state with the actual real-world infrastructure?

# 10 . How do you use resource dependencies in Terraform and what are some examples of resource dependencies that you have used or can use?

# 11 .How do you use resource meta-arguments in Terraform and what are some examples of resource meta-arguments that you have used or can use?


# 12 .How do you use terraform backend in Terraform and what are some examples of backends that you have configured or can configure using this feature?

# 13 .How do you write documentation for your Terraform code and what are some best practices or guidelines that you follow or can follow to write documentation for your Terraform code?

One less popular step is documentation. Yes - the documentation you haven’t written. You know what I mean.

No matter how well written your code is, there usually is a gap between today’s YOU and the future YOU, who has to work with and pick up what you leave behind.

This is usually also the reason for writing the documentation last. Better to have something than nothing, right?

# 14 . Is there a way to bulk import the state of current cloud subscription into Terraform state ?
Ans. You can use the terraform import command to import individual resources into your Terraform state, but there is not currently a bulk import tool.

# 15 .Can you explain the core concepts of Terraform, such as providers, resources, and modules?

Providers in Terraform are plugins that are responsible for translating the HCL code to API calls to specific cloud providers or platforms, such as AWS, Azure, or GCP. Resources are the primary components of your infrastructure, such as compute instances, storage, or networking. They are defined using HCL code and managed by Terraform. Modules are reusable packages of Terraform code that contain multiple resources for a specific functionality or infrastructure configuration, allowing to reuse code and share it across various projects.

# 16 .What are the key differences between Terraform and other Infrastructure as Code tools, such as CloudFormation or Ansible?

Terraform is cloud-agnostic, so it can work with multiple cloud providers and platforms, while CloudFormation is AWS-specific. Terraform uses a declarative language (HCL), meaning you define the desired end state, and Terraform calculates the steps to achieve it; whereas, Ansible uses a procedural language, which means you define the steps and actions that need to be executed. Terraform also strongly focuses on idempotency and allows for complex dependencies management between resources, making it suitable for managing entire infrastructure stacks.

# 17 .Can you describe the lifecycle of a Terraform project, including its main commands?

The Terraform lifecycle typically consists of these stages - Initialization, Planning, Applying, and Destruction. The main commands used are - `terraform init` Initializes the backend and downloads the providers required for the project. - `terraform plan` Creates an execution plan by comparing the current state with the desired state defined in the code. - `terraform apply` Executes the plan, creating or updating the infrastructure resources as needed to match the desired state. - `terraform destroy` Deletes the resources created by Terraform, removing them from the cloud provider.

# 18 .How do you manage remote Terraform state, and why is it important?
Remote Terraform state is managed using backend configurations that store the state file in a shared and centralized location, such as Amazon S3, Azure Blob Storage, or Google Cloud Storage. It is essential to manage remote state because it enables collaboration between team members, allows you to maintain a single source of truth for your infrastructure, provides locking mechanisms to prevent conflicting infrastructure changes, and ensures secure storage of sensitive information.



# 19 .What happens when multiple enginers start developing infrastrutre using the same state file

# 20 . What is the null resources?

# 21 . Difference b/w cloud formation and Terraform 

# 22 . When to use  target resources on terraform
  
# 23 .Terraform template file  
  
  data "template_file" "userdata" {
  template = file("${path.module}/userdata.sh")
  vars = {
    DOCKER_VERSION             = var.DOCKER_VERSION
    ANSIBLE_VERSION            = var.ANSIBLE_VERSION
  }
}
  
  resource "aws_launch_configuration" "bitslovers-lc" {
  name_prefix          = "${var.my_environment_name}-lc-"
  image_id             = "ami-12345"
  instance_type        = var.INSTANCE_TYPE
  security_groups      = [aws_security_group.inst.id]
  user_data            = data.template_file.userdata.rendered
  key_name             = "bitslovers-keypair"
  iam_instance_profile = aws_iam_instance_profile.iam_profile.name
 }

# 24 . Drift Detection Strategies:
 There is a common misunderstanding among developer teams that the templates used to run the deployments are faultless sources of truth when using infrastructure as code tools. Though, configuration drift is one of the fundamental challenges for architecture built using tools like the Terraform.
Configuration drift occurs when the actual state of the infrastructure starts to accumulate changes and deviates from the particular configurations defined in the code. Regardless of your performance in DevOps, configuration drift can happen for many reasons, like modifying, adding, or removing resources.
**Terraform state**
To understand how the drift configuration happens, you must first understand how Terraform drift can occur. Besides containing environmental metadata, the most significant function of the terraform state is that its the single source for the truth of your backed-end APIs.
Terraform uses resource mapping and a declarative approach to configure and bind each remote object to a particular resource. Then, this association is recorded in the Terraform state file.
Learning how to solve infrastructure problems using terraform takes time, and students in this course must find ways of getting extra time for practice.
  
  ## Running new terraform plan sequence operation
  
  ## terraform refresh
  
  ## CloudQuery 
   This is an open-source cloud asset inventory that SQL powers. It extracts all the resources from the desired cloud provider, then formats them before loading the formatted resources into PostgreSQL. As a result, a drift detection command is created on top of PostgreSQL to turn the drift problem into a data issue.
  
  After installing the CloudQuery CLI, you can continue detecting the S3 bucket drifts. As explained in the above paragraph, the first command of the process fetches all the resources from the particular cloud provider and puts them on the PostgreSQL table.
  
  The output of this process will clearly show the results that are managers and ones that are unmanaged. You will also find out that most buckets have drifted due to the bugs
  
 Fast enumeration of the cloud resources with the fetch command.
  
Support for scanning multiple state files.
  
Easy detection of unmanaged resources with a simple drift scan command.
  
  ##Driftctl
  
  This free, open-source tool warns, detects, and warns you of any signs of infrastructure drift. So, the tool detects, tracks and alerts you on both managed and unmanaged drift that may happen.

  The benefits of using this tool include detecting drifts on managed and unmanaged resources with just a command. It also supports the scanning of multiple state files when using infrastructure as code tools
  
# When you need to create the VPC, load balancer, Application
vpc - cidr blocks, sub net cidrs, azes asg - min max ami id,sg ports,region and lb -health checks,backend pool
  
# terraform automations?
log managenement , monetering ,standered, acc standeredizationm,aws config
  
# Industry standerds to maintain to develop the terraform code
1. prevennt Hard code and varibilaze 
2. proper tagging
3. resources pointng in the output file
4. Sercurity standerd
5.Encryptions
  
# How do you create a terraform template file if you need to create VPC,EC2, Cloudtrail and IAM policies  
  
# How do you  debug terraform  
  
# can you explaing the use case of terraform show

# # can you explaing the use case of terraform state list
# Is t possible to manage existing resource in terraform 
  
  

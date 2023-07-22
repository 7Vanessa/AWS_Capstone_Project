# AWS Capstone Project

## Contributors:

* Sabrina MOHAMMEDI
* Vanessa MOHAMMEDI
* Nelson FOSSI


# Quiz : network quiz - Answers

 1. Which definition describes a virtual private cloud (VPC) ? **Option C**

 2. A company's VPC has the CIDR block 172.16.0.0/21 (2048 addresses). It has two subnets (A and B). Each subnet must support 100 usable addresses now, but this number is expected to rise to at most 254 usable addresses soon. Which subnet addressing scheme meets the requirements and follows AWS best practices ? **Option C**

 3. Which combination of actions enables direct internet access for IPv4 hosts in a virtual private cloud ? **Options C,E & F**

 4. Several EC2 instances launch in a virtual private cloud (VPC) that has internet access. These instances should not be accessible from the internet, but they must be able to download updates from the internet. How should the instances launch ? **Option D**


# Quiz: iam quiz - Answers

 1. Which statement describes AWS Identity and Access Management (IAM) users ? **Option C**

 2. How can you grant the same level of permissions to multiple users within an account ? **Option A**

 3. Which statements describe AWS identity and Access Management (IAM) roles ? **Options C & D**

 4. Which statement describes a resource-based policy ? **Option D**

 5. How does AWS Identity and Access Management (IAM) evaluate a policy ? **Option B**

 6. A team of developers needs access to several services and resources in a virtual private cloud (VPC) for 9 months. How can you use AWS Identity and Access Management (IAM) to enable access for them ? **Option C**

 7. How does identity federation increase security for an application that is built in Amazon Web Services (AWS) ? **Option A**


# Quiz policies - Answers

 1. What actions are allowed for EC2 instances and S3 objects based on this policy? What specific resources are included ?
    * Actions allowed : **ec2:DescribeVpcs**, **ec2:DescribeSubnets** and **ec2:DescribeSecurityGroups**
    * Resources included : **Resource: "*"**

 2. Under what condition does this policy allow access to VPC-related information ? Which AWS region is specified ?
    * The actions are allowed only when the S3 object key starts with either "documents/" or "images/".
    * The AWS region is not specified in this policy. 

 3. What actions are allowed on the "example-bucket" and its objects based on this policy? What specific prefixes are specified in the condition ?
    * The policy allows the IAM user to perform two actions related to IAM users within the AWS account :
      * iam:CreateUser: This action allows the IAM user to create new IAM users within the AWS account.
      * iam:DeleteUser: This action allows the IAM user to delete IAM users within the AWS account.
    * There are no specific prefixes specified in the conditions.

 4. What actions are allowed for IAM users based on this policy? How are the resource ARNs constructed ?
    * The policy allows the IAM user to perform two actions :
      * iam:Get*: This action grants permission to perform any IAM read-related actions that begin with "Get," such as iam:GetUser, iam:GetGroup, iam:GetPolicy, etc. Essentially, it allows users to retrieve information about IAM entities.
      * iam:List*: This action grants permission to perform any IAM list-related actions that begin with "List," such as iam:ListUsers, iam:ListGroups, iam:ListPolicies, etc. It allows users to list IAM entities.
    * The resource ARNs (Amazon Resource Names) are constructed based on the AWS service and the specific resource within that service. ARNs are used to uniquely identify resources in AWS and are typically formatted as follows: arn:aws:<service>:<region>:<account-id>:<resource-type>/<resource-name>

 5. Which AWS service does this policy grant you access to? Does it allow you to create an IAM user, group, policy, or role? Go to https://docs.aws.amazon.com/IAM/latest/UserGuide/ and in the left navigation expand Reference > Policy Reference > Actions, Resources, and Condition Keys. Choose Identity And Access Management. Scroll to the Actions Defined by Identity And Access Management list. Name at least three specific actions that the iam:Get* action allows.
    * This policy grants access to the Amazon Elastic Compute Cloud (Amazon EC2) service in AWS. Specifically, it allows access to create and start EC2 instances with instance types "t2.micro" and "t2.small." However, the "Effect" of this policy is set to "Deny," which means that the specified actions (ec2:RunInstances and ec2:StartInstances) are denied for instances with the mentioned instance types.
    * No, the policy does not allow the creation of IAM users, groups, policies, or roles.
    * **iam:GetUser**, **iam:GetGroup** and **iam:GetPolicy**

 6. What actions does the policy allow ? Say that the policy included an additional statement object, like this example: How would the policy restrict the access granted to you by this additional statement ? If the policy included both the statement on the left and the statement in question 2, could you terminate an m3.xlarge instance that existed in the account ?
    * The policy allows the following actions:
      * EC2 Actions:
        *   ec2:RunInstances: Allows the user to launch EC2 instances.
        *   ec2:TerminateInstances: Allows the user to terminate EC2 instances.
      * S3 Actions:
        * s3:GetObject: Allows the user to retrieve (download) objects from the specified S3 bucket.
        * s3:PutObject: Allows the user to upload objects to the specified S3 bucket.
    * This statement grants the user permission to perform any EC2 action. The ec2:* wildcard means the user has full EC2 access, including actions not explicitly listed in the original policy.
    * If the policy included both the original statement and the additional statement allowing ec2:*, then yes, you would have the permission to terminate an m3.xlarge instance that exists in the account. This is because the ec2:TerminateInstances action is already explicitly allowed by the first statement, and the additional statement grants full EC2 access, including the ability to terminate any EC2 instance type, including m3.xlarge instances. 


# AWS Cloud & Big Data Architectures - Project

## Architecture diagram

![architecture_diagram.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Farchitecture_diagram%2Farchitecture_diagram.png)


## Step 1: VPC creation

![1.a-Creation_VPC.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FVPC_creation%2F1.a-Creation_VPC.png)

## Step 2: Subnets creation and association with the VPC

![screenshot_2023-07-22_16.23.49.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_subnets%20_et_association_avec_le_VPC%2Fscreenshot_2023-07-22_16.23.49.png)

![screenshot_2023-07-22_16.23.55.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_subnets%20_et_association_avec_le_VPC%2Fscreenshot_2023-07-22_16.23.55.png)

![screenshot_2023-07-22_16.24.02.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_subnets%20_et_association_avec_le_VPC%2Fscreenshot_2023-07-22_16.24.02.png)

![screenshot_2023-07-22_16.24.08.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_subnets%20_et_association_avec_le_VPC%2Fscreenshot_2023-07-22_16.24.08.png)

![screenshot_2023-07-22_16.24.13.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_subnets%20_et_association_avec_le_VPC%2Fscreenshot_2023-07-22_16.24.13.png)

![screenshot_2023-07-22_16.24.40.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_subnets%20_et_association_avec_le_VPC%2Fscreenshot_2023-07-22_16.24.40.png)


## Step 3: Internet Gateway creation and association with the VPC

![screenshot_2023-07-22_16.25.35.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_Internet_Gateway_et_association_avec_le_VPC%2Fscreenshot_2023-07-22_16.25.35.png)

![screenshot_2023-07-22_16.26.02.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_Internet_Gateway_et_association_avec_le_VPC%2Fscreenshot_2023-07-22_16.26.02.png)

![screenshot_2023-07-22_16.26.21.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_Internet_Gateway_et_association_avec_le_VPC%2Fscreenshot_2023-07-22_16.26.21.png)


## Step 4.a: Route tables creation & Association to the VPC & association to the subnets

![screenshot_2023-07-22_16.27.17.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_routes_tables_association_au_VPC_association_aux_subnets%2Fscreenshot_2023-07-22_16.27.17.png)

![screenshot_2023-07-22_16.27.42.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_routes_tables_association_au_VPC_association_aux_subnets%2Fscreenshot_2023-07-22_16.27.42.png)

![screenshot_2023-07-22_16.28.21.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_routes_tables_association_au_VPC_association_aux_subnets%2Fscreenshot_2023-07-22_16.28.21.png)

![screenshot_2023-07-22_16.28.48.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_routes_tables_association_au_VPC_association_aux_subnets%2Fscreenshot_2023-07-22_16.28.48.png)

![screenshot_2023-07-22_16.29.16.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_des_routes_tables_association_au_VPC_association_aux_subnets%2Fscreenshot_2023-07-22_16.29.16.png)


## Step 4.b: Add route to the Public Route Table towards the Internet Gateway

![Add_route_to_Public_Route_Table_vers_Internet_Gateway.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FAdd_route_to_Public_Route_Table_towards_Int_Gat%2FAdd_route_to_Public_Route_Table_vers_Internet_Gateway.png)


## Step 4.c: Global Vision

![4.c-Vision_globale.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FGlobal_Vision%2F4.c-Vision_globale.png)


## Step 5: Security Groups creation

![screenshot_2023-07-22_16.37.14.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FSecurity_Groups_creation%2Fscreenshot_2023-07-22_16.37.14.png)

![screenshot_2023-07-22_16.38.18.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FSecurity_Groups_creation%2Fscreenshot_2023-07-22_16.38.18.png)

![screenshot_2023-07-22_16.38.53.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FSecurity_Groups_creation%2Fscreenshot_2023-07-22_16.38.53.png)

![screenshot_2023-07-22_16.40.04.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FSecurity_Groups_creation%2Fscreenshot_2023-07-22_16.40.04.png)

![screenshot_2023-07-22_16.41.10.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FSecurity_Groups_creation%2Fscreenshot_2023-07-22_16.41.10.png)


## Step 6: Creation of an EC2 instance and association to security group Inventory-App

![screenshot_2023-07-22_21.27.43.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_creation_and_association_to_Inventory-App_SG%2Fscreenshot_2023-07-22_21.27.43.png)

![screenshot_2023-07-22_21.27.50.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_creation_and_association_to_Inventory-App_SG%2Fscreenshot_2023-07-22_21.27.50.png)

![screenshot_2023-07-22_21.27.56.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_creation_and_association_to_Inventory-App_SG%2Fscreenshot_2023-07-22_21.27.56.png)

![screenshot_2023-07-22_21.28.02.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_creation_and_association_to_Inventory-App_SG%2Fscreenshot_2023-07-22_21.28.02.png)


## Step 7: Creation of an IAM-Inventory-Role

![screenshot_2023-07-22_14.53.19.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreation_of_an_IAM_Inventory-Role%2Fscreenshot_2023-07-22_14.53.19.png)


## Step 8: Add IAM-Inventory-Role to the EC2 instance

![screenshot_2023-07-22_14.56.31.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FAdd_IAM-Inventory-Role_to_the_EC2_instance%2Fscreenshot_2023-07-22_14.56.31.png)

![screenshot_2023-07-22_14.56.43.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FAdd_IAM-Inventory-Role_to_the_EC2_instance%2Fscreenshot_2023-07-22_14.56.43.png)


## Step 9: Edit inbound rules of the Capstone-DB Security group (add inbound rule and source is Inventory-App)

![screenshot_2023-07-22_16.49.59.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEdit_inbound_rules_of_the_Capstone-DB_SG%2Fscreenshot_2023-07-22_16.49.59.png)


## Step 10: Edit inbound rules of Inventory-App security group (source is ALBSG)

![screenshot_2023-07-22_16.51.24.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEdit_Inbound_rules_inventory-App_SG%2Fscreenshot_2023-07-22_16.51.24.png)


## Step 11: EC2 instance for commands

1. Creation:

![screenshot_2023-07-22_18.12.56.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FCreation%2Fscreenshot_2023-07-22_18.12.56.png)

![screenshot_2023-07-22_18.13.02.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FCreation%2Fscreenshot_2023-07-22_18.13.02.png)

![screenshot_2023-07-22_18.13.09.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FCreation%2Fscreenshot_2023-07-22_18.13.09.png)

![screenshot_2023-07-22_18.13.18.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FCreation%2Fscreenshot_2023-07-22_18.13.18.png)

![screenshot_2023-07-22_18.18.01.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FCreation%2Fscreenshot_2023-07-22_18.18.01.png)

![screenshot_2023-07-22_18.19.42.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FCreation%2Fscreenshot_2023-07-22_18.19.42.png)


2. Install a LAMP Webserver on Amazon Linux 2:

![sudo_amazon-linux-extras_install-y...png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FInstall_LAMP_Webserver_on_Amazon_Linux_2%2Fsudo_amazon-linux-extras_install-y...png)

![sudo_systemctl_enable_httpd.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FInstall_LAMP_Webserver_on_Amazon_Linux_2%2Fsudo_systemctl_enable_httpd.png)

![sudo_systemctl_start_httpd.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FInstall_LAMP_Webserver_on_Amazon_Linux_2%2Fsudo_systemctl_start_httpd.png)

![sudo_yum-y_update.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FInstall_LAMP_Webserver_on_Amazon_Linux_2%2Fsudo_yum-y_update.png)

![sudo_yum_install-y_httpd_mariadb-server.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FInstall_LAMP_Webserver_on_Amazon_Linux_2%2Fsudo_yum_install-y_httpd_mariadb-server.png)


3. Update Security Group:

![screenshot_2023-07-22_18.34.11.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FUpdate_security_group%2Fscreenshot_2023-07-22_18.34.11.png)


4. Unzip data:

![sudo_unzip_Example.zip-d__var_www_html_.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FUnzip_data%2Fsudo_unzip_Example.zip-d__var_www_html_.png)


5. Open site with IPv4 of EC2 instance

![screenshot_2023-07-22_18.42.03.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FOpen_site_ipv4_of_ec2_instance%2Fscreenshot_2023-07-22_18.42.03.png)

![Query_does_not_work.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FEC2_Instance_for_commands%2FOpen_site_ipv4_of_ec2_instance%2FQuery_does_not_work.png)


## Step 12: Create a MySQL RDS database instance

1. Create a DB subnet group:

![screenshot_2023-07-22_18.56.03.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fcreate_db_subnet_group%2Fscreenshot_2023-07-22_18.56.03.png)

![screenshot_2023-07-22_18.56.09.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fcreate_db_subnet_group%2Fscreenshot_2023-07-22_18.56.09.png)

![screenshot_2023-07-22_18.56.44.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fcreate_db_subnet_group%2Fscreenshot_2023-07-22_18.56.44.png)

2. Creation

![screenshot_2023-07-22_19.06.20.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fscreenshot_2023-07-22_19.06.20.png)

![screenshot_2023-07-22_19.06.26.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fscreenshot_2023-07-22_19.06.26.png)

![screenshot_2023-07-22_19.06.32.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fscreenshot_2023-07-22_19.06.32.png)

![screenshot_2023-07-22_19.06.39.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fscreenshot_2023-07-22_19.06.39.png)

![screenshot_2023-07-22_19.06.45.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fscreenshot_2023-07-22_19.06.45.png)

![screenshot_2023-07-22_19.06.52.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fscreenshot_2023-07-22_19.06.52.png)

![screenshot_2023-07-22_19.07.00.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fscreenshot_2023-07-22_19.07.00.png)

![screenshot_2023-07-22_19.40.20.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_mysql_rds_db_instance%2Fscreenshot_2023-07-22_19.40.20.png)


## Step 13: Commands in the EC2 instance

![Download_SQL_dump_file.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCommand_in_ec2_instance%2FDownload_SQL_dump_file.png)


## Step 14: Load Balancer creation

1. Create a target group:

![screenshot_2023-07-22_20.01.40.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_load_balancer%2FCreate_target_group%2Fscreenshot_2023-07-22_20.01.40.png)

![screenshot_2023-07-22_20.01.46.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_load_balancer%2FCreate_target_group%2Fscreenshot_2023-07-22_20.01.46.png)

2. Creation:

![screenshot_2023-07-22_20.02.54.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_load_balancer%2Fscreenshot_2023-07-22_20.02.54.png)

![screenshot_2023-07-22_20.03.00.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_load_balancer%2Fscreenshot_2023-07-22_20.03.00.png)

![screenshot_2023-07-22_20.03.07.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_load_balancer%2Fscreenshot_2023-07-22_20.03.07.png)

![screenshot_2023-07-22_20.03.14.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_load_balancer%2Fscreenshot_2023-07-22_20.03.14.png)

![screenshot_2023-07-22_20.03.20.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_load_balancer%2Fscreenshot_2023-07-22_20.03.20.png)

![screenshot_2023-07-22_20.04.43.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_load_balancer%2Fscreenshot_2023-07-22_20.04.43.png)


## Step 15: Check database content

![screenshot_2023-07-22_20.10.40.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcheck_db_content%2Fscreenshot_2023-07-22_20.10.40.png)

![screenshot_2023-07-22_20.23.05.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcheck_db_content%2Fscreenshot_2023-07-22_20.23.05.png)

![screenshot_2023-07-22_20.28.24.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcheck_db_content%2Fscreenshot_2023-07-22_20.28.24.png)

![screenshot_2023-07-22_20.28.44.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcheck_db_content%2Fscreenshot_2023-07-22_20.28.44.png)

![screenshot_2023-07-22_20.29.53.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcheck_db_content%2Fscreenshot_2023-07-22_20.29.53.png)


## Step 16: Create parameters

![screenshot_2023-07-22_20.33.13.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_parameters%2Fscreenshot_2023-07-22_20.33.13.png)

![screenshot_2023-07-22_20.34.44.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_parameters%2Fscreenshot_2023-07-22_20.34.44.png)

![screenshot_2023-07-22_20.35.24.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_parameters%2Fscreenshot_2023-07-22_20.35.24.png)

![screenshot_2023-07-22_20.36.15.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_parameters%2Fscreenshot_2023-07-22_20.36.15.png)

![screenshot_2023-07-22_20.36.29.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FCreate_parameters%2Fscreenshot_2023-07-22_20.36.29.png)


## Step 17: Test Query before image creation

![screenshot_2023-07-22_20.37.32.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2FQuery%2Fscreenshot_2023-07-22_20.37.32.png)


## Step 18: Image creation

![screenshot_2023-07-22_20.39.38.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fimage_creation%2Fscreenshot_2023-07-22_20.39.38.png)

![screenshot_2023-07-22_20.39.44.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fimage_creation%2Fscreenshot_2023-07-22_20.39.44.png)

![screenshot_2023-07-22_20.40.24.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fimage_creation%2Fscreenshot_2023-07-22_20.40.24.png)


## Step 19: Create launch template

![screenshot_2023-07-22_20.48.52.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_launch_template%2Fscreenshot_2023-07-22_20.48.52.png)

![screenshot_2023-07-22_20.48.59.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_launch_template%2Fscreenshot_2023-07-22_20.48.59.png)

![screenshot_2023-07-22_20.49.05.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_launch_template%2Fscreenshot_2023-07-22_20.49.05.png)

![screenshot_2023-07-22_20.49.12.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_launch_template%2Fscreenshot_2023-07-22_20.49.12.png)

![screenshot_2023-07-22_20.49.26.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_launch_template%2Fscreenshot_2023-07-22_20.49.26.png)


## Step 20: Create an autoscaling group

![screenshot_2023-07-22_20.51.35.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-22_20.51.35.png)

![screenshot_2023-07-22_20.51.41.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-22_20.51.41.png)

![screenshot_2023-07-22_20.53.53.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-22_20.53.53.png)

![screenshot_2023-07-22_20.53.59.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-22_20.53.59.png)

![screenshot_2023-07-22_20.54.46.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-22_20.54.46.png)

![screenshot_2023-07-22_20.55.48.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-22_20.55.48.png)

![screenshot_2023-07-22_20.55.55.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-22_20.55.55.png)

![screenshot_2023-07-22_20.56.35.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-22_20.56.35.png)

![screenshot_2023-07-22_20.57.00.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-22_20.57.00.png)

![screenshot_2023-07-22_21.31.37.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-22_21.31.37.png)

![screenshot_2023-07-23_1.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-23_1.png)

![screenshot_2023-07-23_2.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-23_2.png)

![screenshot_2023-07-23-3.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcreate_autoscaling_group%2Fscreenshot_2023-07-23-3.png)


## Step 21: Get the DNS name of the load balancer

![dns_load_balancer.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fdns_load_balancer%2Fdns_load_balancer.png)


## Step 22: Check the output by using the DNS name of the load balancer and try a query

![check_output_using_loadbalancer_dns_name.png](images%2FAWS%20Cloud%20%26%20Big%20Data%20Architectures%2Fcheck_output_using_dns_load_balancer%2Fcheck_output_using_loadbalancer_dns_name.png)


# Big Data - Data Visualization With AWS QuickSight

Screenshots taken afterward by another member as we realized that we forgot to take it the first time (to show the process we followed to import our data).

* Data importation:

![1.png](images%2FQuicksight%2F1.png)

![2.png](images%2FQuicksight%2F2.png)

![3.png](images%2FQuicksight%2F3.png)

![4.png](images%2FQuicksight%2F4.png)

![5.png](images%2FQuicksight%2F5.png)

![6.png](images%2FQuicksight%2F6.png)

![7.png](images%2FQuicksight%2F7.png)


* Dashboard creation:

![sum_of_cost_by_category_and_admit_date.PNG](images%2FQuicksight%2Fsum_of_cost_by_category_and_admit_date.PNG)

![sum_of_discount_sum_of_profit_by_category_and_admit_date.PNG](images%2FQuicksight%2Fsum_of_discount_sum_of_profit_by_category_and_admit_date.PNG)

![sum_of_profit_by_category.PNG](images%2FQuicksight%2Fsum_of_profit_by_category.PNG)

![sum_of_profit_by_hospital.PNG](images%2FQuicksight%2Fsum_of_profit_by_hospital.PNG)

![sum_of_revenue_by_admit_date.PNG](images%2FQuicksight%2Fsum_of_revenue_by_admit_date.PNG)

![top3_category_for_total_profit.PNG](images%2FQuicksight%2Ftop3_category_for_total_profit.PNG)

![YoY.PNG](images%2FQuicksight%2FYoY.PNG)

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

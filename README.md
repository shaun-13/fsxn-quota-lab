# FSx for ONTAP Quota Lab CloudFormation Template

## Description

This AWS CloudFormation template is used in the technical walkthrough featured in the second part of the two-part blog series on quotas within Amazon FSx for NetApp ONTAP (FSx for ONTAP). This template automates the deployment of an AWS environment that includes a new VPC, a single-AZ FSx for NetApp ONTAP file system, and two EC2 instances serving as a bastion host and an NFS client. The stack deployment includes the creation of all necessary networking components, security groups, and IAM roles for resource access and management.

For an in-depth understanding of how this template is used, be sure to read the blog posts on quota management in FSx for ONTAP:
- [Part 1: Mastering Quota Management in Amazon FSx for NetApp ONTAP](https://community.netapp.com/t5/Tech-ONTAP-Blogs/Mastering-Quota-Management-in-Amazon-FSx-for-NetApp-ONTAP/ba-p/453445)
- [Part 2: Quota Configuration in Amazon FSx for NetApp ONTAP: A Technical Implementation Guide](https://community.netapp.com/t5/Tech-ONTAP-Blogs/Quota-Configuration-in-Amazon-FSx-for-NetApp-ONTAP-A-Technical-Implementation/ba-p/453447)


**WARNING**: Deploying this template will create AWS resources and incur costs estimated at approximately 2 USD per hour. To avoid ongoing charges, please terminate the stack after completing the walkthrough.

## Parameters


- `EnvironmentName`: Prefixed to the names of created resources.
- `VpcCIDR`: IPv4 CIDR block for the new VPC.
- `PublicSubnet1CIDR`: IPv4 CIDR block for the public subnet.
- `PrivateSubnet1CIDR`: IPv4 CIDR block for the private subnet.
- `FsxAdminPassword`: Password for managing the file system.
- `EC2KeyPair`: Name of an existing Amazon EC2 Key Pair.
- `InstanceType`: EC2 instance type for the bastion host and NFS client.

## Resources Created

- **VPC**: A virtual private cloud configured with specified CIDR blocks.
- **InternetGateway**: An internet gateway for the VPC.
- **EC2 Instances**: Linux bastion host and NFS Client instances.
- **FSx for NetApp ONTAP File System**: A single-AZ deployment in the private subnet.
- **Security Groups**: Configured to allow necessary access to the file system and EC2 instances.
- **IAM Roles and Instance Profile**: For EC2 instances to describe FSx resources.

## Deployment Procedure

1. Download the CloudFormation template from this GitHub repository.
1. In the AWS Management Console, navigate to the CloudFormation service and select 'Create Stack'.
1. In the **Specify template** section, upload the CloudFormation template file.
1. Input the required parameters when prompted. You can use all the default values as provided.
1. Review the parameters and acknowledge the creation of IAM resources.
1. Initiate stack creation and monitor progress in the CloudFormation console.

## Estimated Deployment Time

The stack may take up to 60 minutes to deploy fully.

## Post-Deployment

- SSH into the Linux Bastion Host to access the FSx file system.
- Utilize the NFS Client EC2 instance for interacting with the FSx for ONTAP filesystem qtrees.

## Cleanup Instructions

To avoid incurring additional charges:
1. Go to the AWS CloudFormation console.
2. Select the stack.
3. Click 'Delete Stack'.

## License
MIT License

Copyright (c) 2024 Shaun Phua

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

> [!IMPORTANT]
> This lab environment is not meant for production use.

 Secure Access to Private Subnets Using an AWS Bastion Host

![Alt text](Ola-AWS Bastion Host Reference Architecture)


By serving as a safe point of entry for administrative access, an AWS bastion host
safeguards infrastructure within a private subnet. Databases and EC2 instances are 
examples of private subnet resources that cannot be accessed directly from the internet
and lack public IP addresses. Only the bastion host, which is situated in a public subnet 
and protected by multi-factor authentication (MFA), SSH keys, and IAM policies, allows access.
Strong network isolation and a smaller attack surface are achieved by security groups, which
only permit incoming traffic to private resources from the bastion host. AWS services like 
CloudTrail and CloudWatch can log and monitor activity because all access is centralized, 
facilitating auditing and quicker incident response. All things considered, an AWS bastion 
host improves cloud security for private subnet infrastructure and offers defense-in-depth.


The solution is built within a custom Amazon Virtual Private Cloud (VPC) and is designed
for high availability across two Availability Zones (AZs).

AWS Resources Used

VPC with public and private subnets distributed across two AZs

Internet Gateway (IGW) to enable public internet access for resources in public subnets

Route Tables associated with public and private subnets to control traffic routing

NAT Gateway to allow outbound internet access for resources in private subnets

Bastion Host to provide secure administrative access to private resources

Security Groups acting as stateful firewalls to control inbound and outbound traffic

VPC Flow Logs to monitor and log inbound and outbound network traffic

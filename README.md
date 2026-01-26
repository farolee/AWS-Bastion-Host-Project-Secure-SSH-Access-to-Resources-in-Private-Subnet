      Secure Access to Private Subnets Using an AWS Bastion Host
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

The solution is built inside a custom Virtual Private Cloud (VPC) and designed for high availability across two Availability Zones (AZs).
Key Architecture Components
•	VPC with public and private subnets across two AZs
•	Internet Gateway for public internet access
•	Route tables for the Subnets.
•	NAT Gateway for outbound internet access from private resources
•	Bastion Host for secure administrative access
•	Security Groups acting as firewalls.
•	VPV flow-logs monitor outbound and inbound traffic.


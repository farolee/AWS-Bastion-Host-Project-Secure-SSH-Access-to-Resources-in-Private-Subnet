
 Secure Access to Private Subnets Using an AWS Bastion Host

<img width="733" height="734" alt="image" src="https://github.com/user-attachments/assets/ebc4ac3e-6ba9-4470-b8c1-8ee1a4501a98" />

📌AWS Networking: Granting Internet Access to Resources in Private Subnets
The Default State

The resources deployed within a Private Subnet in an Amazon VPC do not have 
direct outbound internet access. Likewise, external users on the internet cannot
directly reach or access those resources. This isolation improves security by
keeping sensitive systems away from public exposure.

The Solution: NAT Gateway
To enable resources in private subnets to securely access the internet without
allowing inbound public access, a NAT Gateway must be deployed in a Public Subnet. 
The NAT Gateway acts as an intermediary, allowing private resources to initiate 
outbound internet connections while remaining inaccessible from the public internet.

Routing the Traffic:
Deploying a NAT Gateway alone is not sufficient. You must also configure a Route Table
for the Private Subnet. The route table should include a default route (0.0.0.0/0) that
directs outbound internet traffic through the NAT Gateway. This ensures that resources 
in the private subnet can communicate with external services such as software repositories,
update servers, and cloud-based applications while maintaining a secure network architecture.

A Bastion Host (also called a Jump Host) is a secure server that provides controlled access 
to resources located inside a private network, such as EC2 instances in private subnets within 
an Amazon VPC. In AWS environments, a Bastion Host is typically deployed in a Public Subnet and
configured with a public IP address.Administrators first connect securely to the Bastion Host 
using SSH (for Linux) or RDP (for Windows), and thenuse it as a gateway to access servers located
in Private Subnets.

An AWS bastion host safeguards infrastructure within a private subnet by serving as a
safe point of entry for administrative access.Our Databases and EC2 instances are 
examples of resources in the private subnet that shouldnt be accessed directly from the internet,
not only becasaue it lack public IP addresses, but also the security implication in our network.
Internal servers remain private and inaccessible from public networks and the number of exposed 
system attacker can target are limited.Only the bastion host, which is situated in a public subnet 
and protected by multi-factor authentication (MFA), SSH keys, and IAM policies, allows access.
Internal servers remain private and inaccessible from public networks.

📌Strong network isolation and a smaller attack surface are achieved by security groups, which
only permit incoming traffic to private resources from the bastion host. AWS services like 
CloudTrail and CloudWatch can log and monitor activity because all access is centralized, 
facilitating auditing and quicker incident response. All things considered, an AWS bastion 
host improves cloud security for private subnet infrastructure and offers defense-in-depth.
With the Jump server in the private Subnet,the infrastures in the private subnet can be securely
achived the following :

✔ OS updates

✔ Downloading packages & dependencies

✔ Applications needing external APIs

✔ Legacy software that needs internet access


The solution is built within a custom Amazon Virtual Private Cloud (VPC) and is designed
for high availability across two Availability Zones (AZs).

📌AWS Resources Used

✔ VPC(Kubby_VPC) with public subnet and private subnets distributed across two AZs

✔ Internet Gateway (IGW_Kubby) to enable public internet access for resources in public subnets

✔ Route Tables associated with public and private subnets to control traffic routing

✔ NAT Gateway to allow outbound internet access for resources in private subnets

✔ Bastion Host to provide secure administrative access to private resources

✔ Security Groups acting as stateful firewalls to control inbound and outbound traffic

#✔ VPC Flow Logs to monitor and log inbound and outbound network traffic.


📌Outcomes And Challenges

Successfully deployed a production ready infrastrueture,didnt come without its challenges,
in term of cost and and choice of service and Implemented AWS best practices for security
and scalability. Gained hands-on experience with real-world reference architecture
Demonstrated end-to-end infrastructure design using AWS services











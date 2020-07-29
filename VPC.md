## Virtual Private Cloud (VPC)
- its a public cloud in AWS with security around it to give virtual privacy
- Personal data center in the cloud
-VPN connections can be made to the VPC
- subnets can be created in the VPC
  - Public subnet
  - Private subnet
- Multiple VPCs can be interconnected by VPC pairing
- VPC endpoints can be connected to amazon resources
- Default VPC is created once in each region.
- Dynamic private IP
- Dynamic public IP
- AWS-provisioned DNS names
- Private/Public DNS names

### DHCP (Dynamic Host Configuration Protocol)
- DHCP will be used to provide dynamic addresses where required within the VPC.
- The DNS domain name can be configured in the option set.
- DHCP Option: In addition to Ip address/subnet mask device will also receive these configured options

### Elastic IP Addresses
- Public IP adresses from the VPC region
- Permanently allocated to your account until released
- Account is charged until released
- EIPs can be moved between instances in the same region

### Elastic Network Interfaces (ENIs)
- Virtual network interface attached to an instance.
- Only available within VPC
- Assicated with a subnet
- Allows dual-homing: Multiple ENIs connected to single instance allow dual-homing

### Endpoints
- AWS endpoints connect VPCs to AWS services (S3 or glacier)
- Can enforce policies on different endpoints
#### Creating an endpoint
- Specify the amazon VPC
- Specify the service: com.amazonaws.<region>.<service>
- Specify the policy
- Specify route tables  
  
### VPC Peering
- Connecting one VPC to another
- VPC is not tranisitive
#### creating VPC Peers
  - Initiating VPC sends request to the receiving VPC
  - Owner role required
  - IP CIDR blocks in each VPC must not overlap : All VPCs should have their own CIDR blocks
  - Receiving VPC accepts is required.
  - Each VPC needs a defined route to the other VPC
  - Security group rules
  
### Security Groups
- Acts like a firewall
- Assign to an instance in VPC and not to subnet
- Defines allowed traffic flows
  - Ingress(entrance)
  - Egress(exit)
- supports only allow rules
- Stateful processing is used

#### NACLs (Network access control lists)
- Applied on subnets
- Stateless process
- Supports both allow and deny rules.
- Rule number defines precedence.
  - Lowest numbered rules first
  - First match applies
  
### Network Address Translation (NAT)
- NAT is used to interconnect point private networks and public networks
- elastic IP is assicated with NAT instance for the public facing side.
- INstances on the private subnet of the VPC use the NAT to connect to the internet
- NAT can be implemented using dedicated NAT instance or using AWS NAT gateway

### Virtual private Gateway - AWS side
- VPG enables connects local network to the VPC
- 
### Customer Gateway (CGW) -Customer side
- Physical device or software application
- anchor on customer side
  - connects to the VPG
combination of both gives VPN connection

*Alternatives:*
- AWS hardware VPN
- AWS Direct connect
- VPN cloudhub
- software VPN
  

  
  
  

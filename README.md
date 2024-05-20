Deployment of Multi-Tenant Cloud WAN Services

Objective:  Create an environment where a Managed Service Provider (MSP) creates a 'Hosted' account that is associated with a single enterprise.  Within that 'Hosted' account, the MSP deployes a CloudFormation template that creates a Global Network and Core Network for a managed Cloud WAN solution.  The Cloud WAN Core Network is shared with a 'Customer' account using Resource Access Manger.  Once the resource share is accepted by the Customer account, the administrator of the 'Customer' account can create self-managed attachments to the managed Cloud WAN using VPC attachments, TGW peering, and Core Network Edge Connect attachments.

Resource Requirements

- An MSP 'provider' account
- An MSP 'hosted' account (assigned to a single customer)
   - Privileges granted to the 'provider' account to build Cloud WAN resources
- A 'customer' account (connecting resources to the 'hosted' account)

Sequence
1. Obtain adminstrative privileges in the 'Provider Account'
2. Assume a management role in the 'hosted Account'
3. Deploy the Cloud WAN CloudFormation template in the 'hosted Account'
4. Execute a RAM share of the Cloud WAN Core Network from the 'hosted Account' to the 'Customer Account'
5. Execute a RAM acceptance of the shared Cloud WAN Core Network from the 'Customer Account' (Console or CLI)
6. Create attachments to the 'Hosted Account' Cloud WAN from the 'Customer Account'
   - VPC Attachment into Shared Services Segment
   - Add Route to Cloud WAN CIDR in VCP Route Table
7. Implement CNE Connect in Hosted Account
   - Connect Attachment via Shared Services VPC Attachment ( GRE in Shared Services)
   - Connect Attachment via Shared Services VPC Attachment (GRE in CustomerData Services)
   - Connect Attachment via Shared Services VPC Attachment (GRE in Management Services)
8. Implement VNF Adjacency to reach the Cloud WAN
   - Create VNF with IPv4 Address in Shared Services VPC
   - Configure Static Route for Cloud WAN CIDR Pointing to Subnet Gateway
   - Configure GRE Tunnels in VNF with Adjacency to CNE Connect Peers
   - Configure External BGP Adjacency between VNF and CNE Connect Peers (eBGP Multi-hop)

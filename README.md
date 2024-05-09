Deployment of Multi-Tenant Cloud WAN Services

Objective:  Create an environment where a Managed Service Provider (MSP) creates a 'Hosted' account that is associated with a single enterprise.  Within that 'Hosted' account, the MSP deployes a CloudFormation template that creates a Global Network and Core Network for a managed Cloud WAN solution.  The Cloud WAN Core Network is shared with a 'Customer' account using Resource Access Manger.  Once the resource share is accepted by the Customer account, the administrator of the 'Customer' account can create self-managed attachments to the managed Cloud WAN using VPC attachments, TGW peering, and Core Network Edge Connect attachments.

Resource Requirements

- An MSP 'provider' account
- An MSP 'hosted' account (assigned to a single customer)
   - Privileges granted to the 'provider' account to build Cloud WAN resources
- A 'customer' account (connecting resources to the 'hosted' account)

Sequence
1. Obtain adminstrative privileges in the 'provider' account
2. Assume a management role in the 'hosted' account
3. Deploy the Cloud WAN CloudFormation template in the 'hosted' account
4. Execute a RAM share of the Cloud WAN Core Network from the 'hosted' account to the 'customer' account
5. Execute a RAM acceptance of the shared Cloud WAN Core Network from the 'customer' account
6. Create attachments to the 'hosted' Cloud WAN from the 'customer' account
   - VPC Attachment
   - Connect Attachment via VPC Attachment
   - TGW Peering
   - TGW Route-Table Attachment
7. Implement routing in the 'customer' account to reach the Cloud WAN

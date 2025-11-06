# Zero Trust Cloud Network Notes  

These notes summarize the AWS re:Inforce 2025 session "Integrate Zero Trust into your cloud network".

## Key Takeaways  

- **Zero Trust Overview:** Traditional perimeter-based security is insufficient for modern cloud workloads. Zero Trust assumes no implicit trust within the network; every access request must be authenticated, authorized, and continuously validated.  
- **Use of AWS VPC Lattice:** VPC Lattice provides application-layer networking across VPCs and AWS accounts, enabling fine‑grained service-to-service communication. Lattice applies policies based on identities and request attributes, reducing reliance on network-layer routing.  
- **AWS Verified Access:** Verified Access offers secure, VPN‑less connectivity to web applications. It uses identity-aware policies and integrates with identity providers (IdPs) to authenticate users and devices before allowing access. This supports remote workforce access without opening networks.  
- **Identity Providers and IAM:** The session emphasized using standards‑based identity providers (e.g., AWS IAM Identity Center, SAML/OIDC providers) to authenticate users. IAM roles and policies enforce least‑privilege access; device posture signals can also factor into decisions.  
- **Network Controls:** Zero Trust complements, not replaces, traditional network controls. Use AWS Network Firewall, security groups, and route tables to enforce segmentation. Combined with identity‑aware controls, this provides defense in depth.  
- **Monitoring and Continuous Verification:** Continuous monitoring of traffic and user/device posture is essential. Services like AWS CloudTrail, Amazon CloudWatch, and VPC Flow Logs provide visibility; integration with security information and event management (SIEM) tools helps detect anomalies.  

## Architecture Components  

1. **Identity Layer:** Centralized identity provider and IAM roles govern user and device authentication and authorization.  
2. **Access Layer:** AWS Verified Access acts as the secure entry point for users, evaluating policies before granting access to applications.  
3. **Service Networking:** AWS VPC Lattice connects services across VPCs and accounts with fine‑grained, identity‑aware policies. Services are registered into service networks.  
4. **Traditional Network Controls:** Security groups, network ACLs, and firewalls enforce baseline segmentation.  
5. **Monitoring:** CloudTrail, VPC Flow Logs, and CloudWatch capture audit logs and metrics; these feed into your SIEM for threat detection and compliance.  

## Steps to Implement  

1. **Define Trust Policies:** Identify applications, users, and devices. Establish policies describing who can access each service and under what conditions.  
2. **Configure Identity Provider:** Set up AWS IAM Identity Center or integrate your existing IdP (SAML/OIDC). Configure users, groups, and device posture checks if supported.  
3. **Deploy AWS Verified Access:** Create a Verified Access instance, configure trust providers (IdP) and device trust providers, and define access groups and policies for your applications.  
4. **Set Up AWS VPC Lattice:** Register your services with VPC Lattice, create service networks, and define listener rules and auth policies referencing identities or request attributes.  
5. **Implement Network Segmentation:** Use VPCs, subnets, security groups, and AWS Network Firewall to isolate workloads and control traffic at the network layer.  
6. **Enable Monitoring:** Turn on CloudTrail, VPC Flow Logs, and CloudWatch metrics. Create dashboards and alerts. Integrate logs into your SIEM for continuous monitoring.  
7. **Test and Iterate:** Simulate access requests from various user roles and devices; verify that policies enforce least‑privilege access. Continuously refine policies based on monitoring insights.

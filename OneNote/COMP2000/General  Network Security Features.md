General / Network security features

  

**Protect against security threats on Azure:**

- **Azure Security Center**

Entry point for Azure security services

Monitoring & visibility for both azure and on-prem

Based on set criteria of cybersecurity policies and controls

  

**Goals**

- Monitor Cloud / Hybrid workloads
- Apply automatic security settings
- Provide recommendations based on current deployments
- Perform security assessments on vulnerabilities
- Detect/block malware using machine learning on your VMs
- Detect/analyze inbound attacks
- Post breach reporting

  

**Secure Score**

- Security center provides your org with a secure score
- Secure score is based on security best practices
- Scores are based on percent of security controls you have in place regarding best practices
- Higher the score the more secure your implementation
- Goals of secure score is - liability, proof to insurance that you're doing your part
    
    - Reporting on current security posture
    - Compare benchmarks and help establish KPIs
    - Improve your security posture

  

**Defense Methods**

- Just-in-time VM access - only get access when you need it
- Adaptive application controls - using AI - creates rules for resource groups to allow them to function, stops suspicious applications
- Adaptive network hardening - monitors your network, recommends stops from suspicious activities
- File integrity monitoring - monitors files, makes sure nothing suspicious is being done in the background, stops and protects
  
- **Azure Sentinel**

  

Security Information and Event Management System (SIEM)

Combines security data from multiple sources

Provides threat detection/response capabilities

Meant to connection pre-existing Microsoft solution

Can use more than just azure to it (AWS, VMWare, citrix (?), etc.

  

**Capabilities** / **Threat Detection**

- Collect cloud data at scale
- Detect undetected threats
- Investigate threats - uses AI
- Incident response

  

- **Azure Key Vault**

Centralized cloud service for storing an application's secrets in a single, central location.

Provides secure access to sensitive information by providing access control and logging capabilities

  

- **Azure Dedicated Hosting - $$$$**

Provides dedicated physical servers to host your Azure VMs for windows and Linux

For organizations with strict regulatory or compliance requirements

Let's you choose the processors, server capabilities, VM series and size on host

  

**Secure network connectivity on Azure**

  

- **Azure Firewall**

Managed cloud base network security service

Protects Azure virtual networks

Allows for communication between azure resources, internet, and on-prem networks.

Virtual stateful firewall

  

**Features**

- High availability built-in
- Unrestricted cloud scalability
- Inbound/outbound filtering rules
- Inbound Destination Network Address Translation (DNAT) support
- Azure Monitor logging

  

- **DDoS protection**

DDoS - Distributed Denial of Service

DDoS traffic is analyzed and discarded at the Azure network edge

Protection takes advantage of scale and elasticity of Microsoft's Global Network

Two service tiers: Basic and Standard

  

**DDoS Attacks**

- Volumetric - spam all the pings
- Protocol - look for vulnerabilities
- Resource / Application layer - flood the application layer
  
- **Security Groups**

  

Network Security Groups (NSGs)

Allow for mor granular network traffic filtering

Act as an internal firewall

Typical rules - source / destination ip, port, protocol

  

**Security Takeaways**

- Security is a layered approach - onion
- Layer / combine services to reduce your attack surfaces
- Segment your network and implement access controls
- Restrict inbound and outbound internet access where needed
- Implement secure connectivity to on-prem networks (VPN)
- Deny by default
- Don’t leave RDP open on the public-facing web - you will be fired, like fr. #important
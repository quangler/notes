## Security Policies (Operational and Organizational)
### Definitions
**Policies** - high-level broad statements of what an organization wants to accomplish; made by management when laying out org's position on an issue
**Procedures** - step-by-step instructions how to implement policies; describe how employees are expected to act in a given situation 
**Standards** - mandatory elements regarding the implementation of a policy; accepted specs providing specific details on how a policy is to be enforced
**Guidelines** - recommendations relating to a policy (not mandatory)

**Security Perimeter** - what is connected to the network, IDS, etc.
**Physical Security** - false ceiling, raised floor, airlock doors, etc.
**Physical Access Control** - need key to locked door, guards who know you, etc.
**Physical Barriers** - airlock doors, needing keys, etc.
### Implementation of a Policy life cycle
1. **Plan (or adjust) for security in the organization** 
	- develop policies, procedures, guidelines
2. **Implement the plans** 
	- includes an instruction period
3. **Monitor the implementation** 
	- ensures effectiveness
4. **Evaluate the effectiveness** 
	- vulnerability assessment and penetration test
### Change Management Process
Change management ensures proper procedures are followed when modifications to the IT infrastructure are made
The change management process includes various stages:
- **Request Change**
- **Review and Approve Process**
- **Examine Consequences**
- **Resolution / Mitigation of any detrimental effects the change might cause**
- **Implement Change**
- **Document Process of change**
### Importance of HR policies as it relates to IT
Since humans are the weakest link in a security chain, there needs to be policies in place
- **Job rotation** - if only one person knows how to do something important and they leave, it can be very bad
- **Employee Hiring / Promotion** - need to ensure the employee has the correct permissions and will not abuse them
- **Retirement** - limit access to documents
- **Forced Retirement** - make sure they don't become disgruntled
- **New Job Offer** - carefully consider continued access to sensitive data
- **Termination** - assuming that they are disgruntled and need to take away access to work resources
- **Vacation** - people who never take time off could be doing something nefarious - mandatory vacations can allow a time for security audits
- **Acceptable Use Policy (AUP)** - the goal is to have employees working effectively and that they aren't using technology in a way the organization doesn't like
	- internet usage policy - protects organization if a user does something they weren't supposed to - can be fired now :)
	- email usage policy - same thing, monitors emails to make sure no documents are being sent when they shouldn't be
- **Clean Desk Policy** - regarding sensitive information being left on the desk physically, especially passwords
- **BYOD** - tries to lower the risk of bringing your own infected device onto the network to infect the network
The basic idea of how HR policies are important is because you want to make sure users follow the rules and don't break the security that is put in place already, or so they aren't actively sabotaging the company - and so the company can fire them if they are doing those things.

### Incident Response Policy / Procedures
- outline how the organization will prepare for security incidents and respond to them **when** they occur
- should cover five phases:
	- Preparation
	- Detection
	- Containment and Eradication
	- Recovery
	- Follow-up actions
## Risk Management
### Definitions
**Risk** - possibility of harm or loss
**Risk Management** - IDing threats and vulnerabilities, what are their impacts? Determining costs to mitigate those events. What is cost effective control for those?
**Risk Assessment/Analysis** - checking an environment to identify risks (threats / vulnerabilities); determining the impact of an event that would affect a project, program, or business
**Asset** - resource or information an organization needs to conduct its business
**Impact** - the loss or harm resulting when a threat exploits a vulnerability
**Threat** - any circumstance or event with the potential to cause harm to an asset
**Threat Actor / Agent** - entity behind a threat
**Threat vector** - the method used to effect a threat (ex, malware (threat) delivered by a watering-hole attack (vector))
**Vulnerability** - any characteristic of an asset that can be exploited by a threat to cause harm
**Control / Countermeasure / Safeguard** - measure taken to detect, prevent, or mitigate risk associated with a threat 
**Single Loss Expectancy (SLE)** - monetary loss or impact of each occurrence of a threat exploiting a vulnerability
**Exposure Factor** - measure of the magnitude of loss of an asset - used in calculating the SLE
**Annualized rate of occurrence (ARO)** - how often an event is expected to happen per year
**Annualized loss expectancy (ALE)** - how much an event is expected to cost per year
**Hazard** - circumstance that increases the likelihood or probable severity of a loss
### Difference between Qualitative and Quantitative Risk Assessment
**Qualitative Risk Assessment** - process of *subjectively* (based on vibes) determining the impact of an event - uses expert judgement, experience, or group consensus
**Quantitative Risk Assessment** - process of *objectively* (based on numbers) determining the impact of an event - uses metrics and models
- It is impossible to conduct risk management that is purely quantitative (based on metrics)
	- it is impossible to define and quantitatively measure all factors that exist in a given risk assessment
- It is possible to accomplish purely qualitative (based on vibes) risk management
- usually both are used during a risk assessment.
### Systematic vs Unsystematic Risk
**Systematic Risk** - the chance of loss that is predictable under relatively stable circumstances (think flood, fire, earthquake - things you can plan for)
**Unsystematic Risk** - the chance of loss that is unpredictable in the aggregate because it results from forces difficult to predict (think war, covid - things you can't really plan for)
### Risk Management Model
there are several models, we talk about general risk management:
1. **Asset Identification**
	- identify what needs protection because they are vulnerable to threats - allows you to prioritize assets, systems, processes; evaluate the cost of addressing the associated risks
2. **Threat Assessment**
	- identify the possible threats and possible vulnerabilities associated with each asset and the likelihood of their occurrence
		- common threats: natural disasters, terrorism, errors, theft, fraud
		- common vulnerabilities: unprotected facilities, unprotected data, insufficient procedures and controls
3. **Impact Determination and Quantification**
	- when a threat is realized (it happens) the risk is then turned into an impact,
	- **Tangible Impact** - results in financial loss or physical damage - easy to determine cost (broken equipment, loss of money)
	- **Intangible Impact** - hard to assign financial value to the impact (breach of confidence, loss of reputation)
4. **Control Design and Evaluation**
	- determining what controls to put into place to mitigate risks
	- **Preventative Controls** - designed to prevent the vulnerability from causing an impact
	- **Detective Controls** - designed to inform someone when a vulnerability has been exploited so that action can be taken
5. **Residual Risk Management**
	- **RISK CANNOT BE FULLY ELIMINATED**
	- **Residual Risk** - risk that remains after implementing controls
	- further evaluating residual risks to identify where you can add controls to reduce risk even more
### Risk Management Strategies
- **Risk-Avoidance** - don't deploy things that add risk
- **Transference** - purchase insurance - allows risk to be transferred to a third party
- **Acceptance** - if the cost of mitigation is higher than the impact cost, you can just acknowledge it | residual risks have to be accepted
- **Mitigation** - reducing impact of attack, when an impact beyond the accepted risk happens - notify someone, turn something off, etc.
## DR and Business Continuity
### Difference between DR and Business Continuity
**Business Continuity (BC)** - keeping an organization running when something disrupts operations; lots of planning and testing those plans
**Disaster Recovery Plan (DRP)** - recovering and rebuilding the organization after a disaster has occurred; a major focus being protecting human life - safety should be a theme throughout the DRP, evacuation and system shutdown should be addressed
The difference between a disaster recovery plan and a business continuity plan is the **focus**:
- **business continuity plan** is focused on **keeping the business** going by spending time and energy on critical systems, albeit in a degraded state until operation comes back to normal
- a **disaster recovery plan** is focused more on **rebuilding the business** and keeping people safe
### RTO vs RPO
**Recovery Time Objective (RTO)** - target time that is set for a resumption of operations after an incident - defines requirements of business continuity
**Recovery Point Objective (RPO)** - time period representing the maximum period of acceptable data loss - defines backup frequency
they are very different things,
**RTO** is how quick things need to be up and running
**RPO** is how often you back things up, and how much data you can lose
### Business Continuity Plan
The point of the BCP is to continue the essential operations of a business when things go wrong
- a tactical necessity until operations can be restored to normal
- emphasis on a limited number of critical systems the organization needs to operate
- critical function and short term needs
### IT Contingency Plan
a part of the business continuity plan
- refer to what to do in the event of a computer failure, virus, DDoS etc. | essentially an even where an organization loses access / use of some or all of the computing resources.
- the IT contingency plan is important because it is more likely to be needed than other parts of a BCP

## Auditing
### Importance of auditing users and various system resources within the organizations
- allows you to identify any risks or vulnerabilities that may be caused from misuse and or incorrectly configured devices / policies or procedures.
### What tools are used for auditing
- Windows Event Viewer
- Nmap
- Vulnerability Scanners
- SolarWinds
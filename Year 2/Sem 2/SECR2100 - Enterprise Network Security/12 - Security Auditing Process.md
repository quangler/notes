**AAAA**
**A**uthorization
**A**uthentication
**A**ttestation
**A**ccounting

### **What is Security Auditing?**
- a detailed review of a network, system or collection of processes.
- mostly concerned with risk and how that risk is addressed

### **What is the purpose of Auditing?**
- technical assessment of an organization's IT infrastructure - OS, Apps, etc.
	- internal auditors - senior IT managers
		- internal audits are done before external audits to make sure nothing is missed and the company doesn't get fined
	- external auditors - third party entities who specialize in auditing

Accounting - collecting information about the network

### The Auditing Process
1. **Planning**
	- Determine scope of audit - can't realistically do the whole environment
	- Obtain permission to perform audit - still need permission, even if you own the company / gear
	- Obtain authority to perform audit
	- Review relevant policies and procedures

2. **Testing and Evaluating Controls** - need a baseline, lets you know the environment
	- Review Logs
	- Review Configurations
	- Use appropriate tools to test

3. **Reporting**
	- Identify shortcomings in policies and procedures
	- Identify errors in configuration

### Common IT Security Standards
**ISO Compliance**
- ISO/IEC 27001 family of standards are some of the most relevant to system administrators - focus on keeping information secure
- ISO/IEC 27001 is known for its information security management system requirements

**HIPAA Security Rule (Health Insurance Portability and Accountability Act)**
- guidelines how organization should protect patients' electronic personal health information
- will ask about this (multiple choice)

**PCI DSS Compliance (Payment Card Industry Data Security Standard)**
- guidelines for companies dealing with any sort of customer payment

### Auditing Tools
- Windows Event Viewer
- NMAP
- Vulnerability Scanners
- SolarWinds

### IT Auditing Checklist
- record who performs audits and what infrastructures were audited
- document all security procedures and policies
- identify trained and untrained employees with regards to detecting threats
- ensure all systems are patched and up to date
- conduct test on infrastructure system to identify vulnerabilities (including Routers, FWs, Servers, etc.)
- record/check who has access to sensitive data
- implement encryption best practices
- regularly review logs to keep human errors at a minimum

#### Auditing: on the test bro
**GPO:**
Computer Configuration > Policies > Windows Settings > Security Policies > Local Policies > Audit Policies > Audit Object Access
- check success and failure
**Folder:**
right click > properties > security tab > advanced > auditing tab > add
- add who you want to audit, and select audit on both success and fail
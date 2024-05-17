## Postmortem Report: Web Application Outage

https://docs.google.com/document/d/18iJx0ALVwVg4A0o7hBIM4SWyofROh7_W_4ANdxX5qRo/edit?usp=sharing

# Issue Summary:
## Duration of the Outage:
- **Start Time:** May 12, 2024, 2:30 PM (PDT)
- **End Time:** May 12, 2024, 4:00 PM (PDT)
## Impact:
The primary web application service was down.
Users experienced a complete inability to access the site.
Approximately 75% of users were affected during the outage.
## Root Cause:
A misconfigured firewall rule blocked incoming traffic to the web servers.
## Timeline:
- **2:30 PM:** Issue detected via automated monitoring alert indicating a sharp drop in incoming traffic.
- **2:32 PM:** On-call engineer notified and begins investigation.
- **2:35 PM:** Initial assumption that the issue was related to a recent code deployment.
- **2:40 PM:** Rollback of the recent deployment initiated as a precaution.
- **2:50 PM:** Rollback completed, but the issue persists.
- **3:00 PM:** Network team contacted to investigate potential network-related issues.
- **3:10 PM:** Network team discovers recent changes to firewall rules.
- **3:20 PM:** Misconfigured firewall rule identified.
- **3:25 PM:** Firewall rule corrected.
- **3:30 PM:** Monitoring shows gradual recovery of incoming traffic.
- **4:00 PM:** Full functionality restored and confirmed by monitoring and user reports.
## Root Cause and Resolution:
## Root Cause:
The outage was caused by a misconfigured firewall rule. The rule inadvertently blocked HTTP and HTTPS traffic to the web servers, preventing users from accessing the application.
This misconfiguration occurred during routine maintenance intended to update security policies.
## Resolution:
Once the network team identified the incorrect firewall rule, they promptly corrected the configuration to allow proper traffic flow.
Post-correction, the monitoring tools confirmed the resumption of normal traffic patterns, and user access was restored.
Corrective and Preventative Measures:
## Improvements/Fixes:
Implement a more rigorous change management process for firewall rules.
Enhance monitoring to include checks for firewall rule changes and their impacts on traffic.
Conduct regular audits of firewall configurations.
Tasks to Address the Issue:
Patch Firewall Management System:
Ensure the latest patches are applied to the firewall management system to avoid configuration errors.
## Update Change Management Protocol:
Introduce a mandatory peer review process for firewall changes.
## Enhance Monitoring:
Add specific alerts for significant drops in traffic that could indicate network configuration issues.
Implement automated tests that verify the accessibility of the web application after firewall changes.
## Training:
Conduct training sessions for the network team on the importance of double-checking firewall rules.
## Audit Schedule:
Schedule quarterly audits of firewall configurations to ensure they align with best practices and security policies.
By addressing these areas, we aim to prevent similar outages in the future and improve overall system resilience.

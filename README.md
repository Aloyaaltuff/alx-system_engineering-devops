Postmortem Report: Website Outage on August 22, 2024

Issue Summary

Duration:August 22, 2024, 14:00 - 16:30 UTC
Impact: The company’s main website was inaccessible for 2.5 hours. Users experienced 503 Service Unavailable errors. Approximately 60% of users were affected, including customers trying to access the online store and the support portal.
Root Cause: The outage was caused by an unplanned depletion of database connection pool resources due to a misconfigured application deployment.

Timeline

14:00 UTC: Issue detected. Users reported inability to access the website via support channels.
14:05 UTC:Initial detection by monitoring alert, which triggered an automated incident response system.
14:10 UTC: On-call engineer reviewed the incident. Investigated potential issues with the web server and CDN.
14:30 UTC:Engineers identified high connection usage on the database server but initially assumed it was a scaling issue.
14:45 UTC: Escalation to the database team. Misleading debugging paths included investigation into potential network issues and CDN configurations.
15:00 UTC: Database team discovered that the application deployment inadvertently set an excessively low connection pool limit.
15:15 UTC: Increased connection pool limits to restore normal functionality. Issue confirmed resolved.
16:00 UTC: Full functionality restored. Ongoing monitoring to ensure stability.
16:30 UTC: Incident closed after verifying system stability and performance.

Root Cause and Resolution

Cause:The issue stemmed from a misconfigured application deployment that set the database connection pool limit too low. This configuration error caused the connection pool to become exhausted under normal load, leading to the 503 errors.
Resolution  - The connection pool limit was increased to accommodate the expected load. 
  - Application deployment configuration was corrected to prevent such issues in the future.
  - Immediate reconfiguration was followed by thorough testing to ensure stability.

Corrective and Preventative Measures

Improvements

  - Implement automated configuration checks before deployment to catch potential misconfigurations.


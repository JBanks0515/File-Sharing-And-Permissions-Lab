🧪 File Sharing and Permissions Lab (Windows Server)



📌 Overview


This lab demonstrates how to configure secure file sharing in a Windows Server environment using Active Directory and NTFS permissions.



🎯 Objectives
Create department-based shared folders

Configure NTFS permissions (Read, Modify, Full Control)

Assign access using security groups

Test access with different user accounts

Apply the principle of least privilege

Document and troubleshoot access issues

🖥️ Lab Environment
Platform: VirtualBox

Domain Controller: DC Server

File Server: Client Server

Client Machines: WinClient-Lab

🗂️ Folder Structure


Created on the File Server:



C:\CompanyShares

HR

IT

Finance

👥 Active Directory Configuration


Security Groups Created
HR_Users

IT_Users

Finance_Users



Group Settings
Group Scope: Global

Group Type: Security



User Assignment
Users were added to their respective department groups

🔗 Share Configuration


Each folder was shared with the following settings:

Enabled Advanced Sharing

Removed default Everyone group

Assigned access to appropriate department group

🔐 NTFS Permissions


Folder

Group

Permission

HR

HR_Users

Modify

IT

IT_Users

Modify

Finance

 Finance_Users

  Read

Security Improvements
Removed unnecessary permissions

Disabled inheritance where appropriate

Applied least privilege principle

🧪 Access Testing


Tested access from client machines using different user accounts.



Method Used


Used runas command to simulate user access:



runas /user:DOMAIN\HR-User cmd



Test Results
HR user:

✅ Access to HR folder

❌ No access to Finance folder

IT user:

✅ Access to IT folder

❌ No access to HR/Finance folders

Finance user:

✅ Read-only access to Finance folder

❌ Cannot modify files

🛠️ Troubleshooting


Issue: Trust Relationship Error


Error:

“The security database on the server does not have a computer account for this workstation trust relationship”



Cause:

Broken secure channel between client and domain (common in virtual labs)



Solution:

Verified domain connection

Used runas for testing instead of full login

Rejoined machine to domain

🔑 Key Concepts Learned
Difference between Share Permissions vs NTFS Permissions

Importance of Security Groups over individual users

Implementation of Least Privilege Access

Basic Active Directory management

Troubleshooting domain trust issues

✅ Conclusion
This lab demonstrates how to securely manage shared resources in a Windows domain environment. Proper use of Active Directory groups and NTFS permissions ensures controlled access and aligns with real-world IT security practices.

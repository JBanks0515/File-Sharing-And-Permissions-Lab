
# 🧪 File Sharing and Permissions Lab (Windows Server)

## 📌 Overview

* Demonstrates how to configure secure file sharing in a Windows Server environment
* Uses **Active Directory** and **NTFS permissions** to control access

---

## 🎯 Objectives

* Create department-based shared folders
* Configure NTFS permissions:

  * Read
  * Modify
  * Full Control
* Assign access using security groups
* Test access with different user accounts
* Apply the principle of least privilege
* Document and troubleshoot access issues

---

## 🖥️ Lab Environment

* **Platform:** VirtualBox
* **Domain Controller:** DC Server
* **File Server:** Client Server
* **Client Machine:** WinClient-Lab

---

## 🗂️ Folder Structure

Created on the File Server:

```
C:\CompanyShares
├── HR
├── IT
└── Finance
```

---

## 👥 Active Directory Configuration

### Security Groups Created

* `HR_Users`
* `IT_Users`
* `Finance_Users`

### Group Settings

* **Group Scope:** Global
* **Group Type:** Security

### User Assignment

* Users were added to their respective department groups

---

## 🔗 Share Configuration

* Enabled **Advanced Sharing**
* Removed default `Everyone` group
* Assigned access to appropriate department group

---

## 🔐 NTFS Permissions

| Folder  | Group         | Permission |
| ------- | ------------- | ---------- |
| HR      | HR_Users      | Modify     |
| IT      | IT_Users      | Modify     |
| Finance | Finance_Users | Read       |

### Security Improvements

* Removed unnecessary permissions
* Disabled inheritance where appropriate
* Applied the **principle of least privilege**

---

## 🧪 Access Testing

### Method Used

* Used `runas` command to simulate user access:

```
runas /user:DOMAIN\HR-User cmd
```

### Test Results

**HR User**

* ✅ Access to HR folder
* ❌ No access to Finance folder

**IT User**

* ✅ Access to IT folder
* ❌ No access to HR or Finance folders

**Finance User**

* ✅ Read-only access to Finance folder
* ❌ Cannot modify files

---

## 🛠️ Troubleshooting

### Issue: Trust Relationship Error

**Error Message:**

```
“The security database on the server does not have a computer account for this workstation trust relationship”
```

### Cause

* Broken secure channel between client and domain (common in virtual labs)

### Solution

* Verified domain connection
* Used `runas` for testing instead of full login
* Rejoined machine to the domain

---

## 🔑 Key Concepts Learned

* Difference between **Share Permissions vs NTFS Permissions**
* Importance of **Security Groups** over individual users
* Implementation of **Least Privilege Access**
* Basic Active Directory management
* Troubleshooting domain trust issues

---

## ✅ Conclusion

* Demonstrates secure management of shared resources in a Windows domain environment
* Shows how proper use of:

  * Active Directory groups
  * NTFS permissions
* Ensures controlled access aligned with real-world IT security practices



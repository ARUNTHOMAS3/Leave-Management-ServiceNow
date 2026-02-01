# Leave Management Application – ServiceNow

## 📌 Project Overview

This project is a **Leave Management Application** developed using **ServiceNow App Engine Studio**.  
It automates employee leave requests using a **multi-level approval workflow** involving **Manager and HR**.

The application demonstrates practical usage of ServiceNow development concepts such as:

- Custom tables
- Dictionary entries
- Flow Designer approvals
- Automated status updates
- Role-based access control

---

## 🎯 Objective

To design and implement a leave request system where:

1. Employee submits a leave request  
2. Manager reviews and approves or rejects  
3. HR provides final approval  
4. System updates leave status automatically  

---

## 🧩 Application Components

### 🔹 Custom Tables

#### Leave Request Table
**Table name:** `x_1805939_leave_1_u_leave_request`

**Fields:**
- Employee (Reference → User)
- Manager (Reference → User)
- HR Approver (Reference → User)
- Leave Type (Reference → Leave Type)
- From Date
- To Date
- Number of Days
- Status (Choice)

---

### 🔹 Status Lifecycle

| Status | Description |
|------|-------------|
| Requested | Initial leave request |
| Manager Approved | Approved by manager |
| HR Approved | Approved by HR |
| Rejected | Rejected by manager or HR |
| Completed | Final approved state |

---

## 🔁 Flow Designer – Leave Approval Flow

**Flow Name:** Leave Approval Flow  
**Trigger:** Leave Request record created where Status = Requested

### Flow Logic:
Leave Request Created
↓
Manager Approval
↓
IF Approved
↓
Update Status → Manager Approved
↓
HR Approval
↓
IF Approved
↓
Update Status → Completed
ELSE
↓
Update Status → Rejected




---

## 📸 Screenshots Included

All screenshots are stored inside the **Screenshots** folder:

- flow_designer_leave_approval.png
- leave_request_table_columns.png
- update_manager_approval.png
- update_hr_approval.png
- update_final_completion.png
- update_rejected_status.png

---

## 🛠 Tools Used

- ServiceNow
- App Engine Studio
- Flow Designer
- Dictionary Entries
- Access Control Lists (ACLs)

---

## 🎓 Learning Outcomes

- Built custom ServiceNow application
- Implemented approval workflows
- Used Flow Designer logic
- Managed record lifecycle
- Designed enterprise-style automation

---

## ✅ Conclusion

This project demonstrates an end-to-end **Leave Management workflow** using ServiceNow best practices and is suitable for **fresher-level ServiceNow Developer / Administrator roles**.

---

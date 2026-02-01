# Leave Management Application – Documentation

---

## 1. Introduction

The Leave Management Application is a custom ServiceNow application designed to automate employee leave requests through structured approval workflows.

The application follows real-world organizational approval hierarchy:
- Employee → Manager → HR

---

## 2. Application Architecture

### Modules Used
- App Engine Studio
- Custom Tables
- Dictionary Entries
- Flow Designer
- Approval Actions
- Record Updates

---

## 3. Database Design

### Leave Request Table

**Table Name:** `x_1805939_leave_1_u_leave_request`

| Field | Type | Description |
|------|------|-------------|
| Employee | Reference (User) | Requesting employee |
| Manager | Reference (User) | Reporting manager |
| HR Approver | Reference (User) | HR reviewer |
| Leave Type | Reference | Type of leave |
| From Date | Date | Start date |
| To Date | Date | End date |
| Number of Days | Integer | Calculated leave days |
| Status | Choice | Request status |

---

## 4. Status Configuration

Status field is configured as a **Choice list**.

| Label | Value |
|------|------|
| Requested | requested |
| Manager Approved | manager_approved |
| HR Approved | hr_approved |
| Rejected | rejected |
| Completed | completed |

---

## 5. Flow Designer Configuration

### Flow Name
**Leave Approval Flow**

### Trigger
- Record Created
- Table: Leave Request
- Condition: Status = Requested

---

## 6. Flow Logic Explanation

### Step 1: Manager Approval
- Approval request sent to Manager
- If approved → status updated to *Manager Approved*
- If rejected → status updated to *Rejected*

### Step 2: HR Approval
- Triggered only after manager approval
- HR receives approval request
- If approved → status updated to *Completed*
- If rejected → status updated to *Rejected*

---

## 7. Update Record Actions

### Manager Approval Update
- Status = Manager Approved

### HR Approval Update
- Status = Completed

### Rejection Handling
- Status = Rejected

These updates are handled automatically through Flow Designer.

---

## 8. Screenshots Reference

Screenshots captured for documentation:

- Leave Request table columns
- Status dictionary entries
- Flow Designer full workflow
- Manager approval update record
- HR approval update record
- Final completion update
- Rejection update

---

## 9. Security Design

Basic role-based structure used:
- Employee
- Manager
- HR

Access controlled using table-level ACLs for:
- Create
- Read
- Write
- Delete

---

## 10. Conclusion

This documentation explains the complete development lifecycle of the Leave Management Application.

The project demonstrates:
- Custom application creation
- Approval workflow automation
- Data-driven process design
- ServiceNow Flow Designer best practices

This project is suitable for academic submission and entry-level ServiceNow roles.

---

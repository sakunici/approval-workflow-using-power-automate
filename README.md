# Automated Export-Import Approval Workflow

## 📝 Overview
This project automates the internal request and approval process for **Export and Import (EX/IM)** transactions. It leverages **Power Automate** to bridge the gap between request submissions via **Microsoft Forms** and centralized data management in **SharePoint Online**, ensuring a transparent and efficient audit trail for the Finance and Accounting department.

## ✨ Core Features
* **Dynamic Request ID Generation**: Automatically assigns a unique identifier (e.g., `EX202601-008`) to every request for precise tracking and record-keeping.
* **Automated Data & Attachment Handling**: Synchronizes form responses directly to a SharePoint list and manages the transfer of supporting documents from Microsoft Forms to secure SharePoint storage.
* **Multi-Stakeholder Notifications**: Sends automated email alerts to requesters and CC'd team members upon submission to maintain transparency throughout the workflow.
* **Enhanced Approval Interface**: Features a "Start and Wait for Approval" action with **Markdown-optimized** descriptions, providing reviewers with professional, clickable links to all supporting documentation.
* **Automated Status Updates**: Updates SharePoint records in real-time based on the Approver's decision (Approved/Rejected), including timestamps and comments for compliance.

## 🏗️ Workflow Logic
1.  **Trigger**: User submits an Export-Import request via Microsoft Forms.
2.  **Data Processing**: 
    * Generate a custom Request ID using the `EX/IM` prefix and date.
    * Create a new record in the SharePoint `ImExApprovalDB` list.
    * Retrieve and attach supporting documents to the SharePoint item.
3.  **Notification**: Send a notification email to the requester and CC relevant team members.
4.  **Approval**: Trigger an approval request to the manager with a Markdown link to the supporting document.
5.  **Finalization**: Update the SharePoint item status and notify the requester of the final decision.

## 🛠️ Technical Stack
* **Microsoft Forms**: Front-end request submission.
* **Power Automate**: Logic engine and workflow orchestration.
* **SharePoint Online**: Centralized database and document repository.
* **Markdown**: Used for formatting rich-text approval notifications.

---
*Developed to enhance financial internal controls and operational efficiency.*

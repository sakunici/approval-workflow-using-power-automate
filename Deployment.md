## 🚀 How to Deploy

Follow these steps to replicate the automated workflow in your environment:

### 1. SharePoint Environment Setup
* **Site Creation**: Ensure you have access to the target SharePoint site (e.g., `ProcurementTeam`).
* **List Configuration**: Create a SharePoint List named `ImExApprovalDB` with the following columns:
    * `Request ID` (Single line of text)
    * `Status` (Choice: Pending, Approved, Rejected)
    * `Requester Name`, `Transaction Type`, `Total Value`, etc.
* **Folder Structure**: Navigate to `Documents > Apps > Microsoft Forms` and ensure the folder `/Documents partages/Apps/Microsoft Forms/` is ready for document storage.

### 2. Microsoft Forms Preparation
* Create the **Export - Import Approval Request Form** with all required fields.
* **Crucial**: Add a "File Upload" question (limited to 1 file for this logic) to collect supporting documents.
* Ensure the form settings allow capturing the responder's email automatically or include a mandatory email field.

### 3. Power Automate Configuration
* **Trigger**: Set the trigger to "When a new response is submitted" for your specific form.
* **Connection Authentication**: Ensure all actions (SharePoint, Outlook, Approvals) use a valid account. If using a Shared Mailbox for the `From (Send as)` field, verify "Send As" permissions.
* **Variable Update**: Update the **Site Address** and **Folder Path** in all SharePoint actions to match your environment.
* **Markdown Link Setup**: In the "Start and wait for an approval" action, format the attachment link using: `[Click to see the attachment](YOUR_DYNAMIC_URL_HERE)`.

### 4. Testing & Verification
* Run a manual test by submitting a form response.
* Verify that the **Request ID** (e.g., `EX202601-001`) is generated and updated in the SharePoint list.
* Confirm that the notification and approval emails contain **clickable links** to the supporting documentation.

---
> **Note**: If you encounter a `ConversionFailed` error in the email step, ensure the `From` field contains a valid email address, not a display name.

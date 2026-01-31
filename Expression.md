# 📑 Key Expressions Reference

This section documents the specific Power Automate expressions used for data transformation and logic handling throughout the workflow.

### 1. Request ID Generation (`Compose`)
Combines the transaction prefix, year-month (UTC+7), and an incremental counter.

concat(
   outputs('Get_response_details')?['body/r57b...'], // Transaction Type (EX/IM)
   formatDateTime(addHours(utcNow(), 7), 'yyyyMM'), // Current Year/Month
   '-',
   formatNumber(add(length(outputs('Get_items')?['body/value']), 1), '000') // Sequential ID
)

### 2. File Path Transformation (Get file content using path)
Converts the absolute URL from Microsoft Forms into a relative path recognized by SharePoint.

decodeUriComponent(
   replace(
      json(outputs('Get_response_details')?['body/r71e...'])?[0]?['link'], 
      '[https://yourcompany.sharepoint.com/sites/YourSiteName](https://yourcompany.sharepoint.com/sites/YourSiteName)', 
      ''
   )
)

### 3. Attachment Link Extraction
Extracts the direct link of the supporting document from the form's JSON output.

json(outputs('Get_response_details')?['body/r71e...'])?[0]?['link']

### 4. Approval Response Metadata (Condition True)
Used to populate the final notification email with details from the Approver's decision.

#### Data Point	Expression

##### Approver's Email
first(outputs('Start_and_wait_for_an_approval')?['body/responses'])?['responder/email']

##### Approver Date	      
first(outputs('Start_and_wait_for_an_approval')?['body/responses'])?['responseDate']

##### Approver Comments	  
first(outputs('Start_and_wait_for_an_approval')?['body/responses'])?['comments']

##### View Attachment	    
json(outputs('Get_response_details')?['body/r71e...'])?[0]?['link']

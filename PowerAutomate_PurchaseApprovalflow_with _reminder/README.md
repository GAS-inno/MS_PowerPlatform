# Power Automate Purchase Request Approval Flow

## Overview
This Power Automate flow is designed to handle a purchase request approval process. It automates the workflow for approving purchase requests, including handling attachments, sending approval requests, and notifying stakeholders based on the approval outcome.

## Trigger
- **When an item is created**: The flow is triggered when a new item is created in a specific SharePoint list.

## Flow Steps

### 1. Initialize Variables
- **varAttachments**: An array variable to store attachments.
- **var1000**: An integer variable initialized to 1000.
- **varMail-CC**: A string variable containing email addresses for CC.
- **varApproval-Completed**: A boolean variable initialized to false.

### 2. Get Item
- **Get Item**: Retrieves the newly created item from the SharePoint list.

### 3. Get Attachments
- **Get Attachments**: Retrieves attachments associated with the item.

### 4. Process Attachments
- **Apply to each (attachment)**: Iterates over each attachment.
  - **Get Attachment Content**: Retrieves the content of each attachment.
  - **Append to Array Variable**: Appends the attachment content to the `varAttachments` array.

### 5. Compose Total Price
- **Compose Total Price**: Extracts the total price from the item.
- **Compose Total Price Convert to Float**: Converts the total price to a float.

### 6. Approval Process
- **Condition**: Checks if the total price is greater than 1000.
  - **If true**:
    - **Update Item**: Updates the item with "Pending" status and other details.
    - **Start and Wait for an Approval**: Starts an approval process for the manager.
    - **Do Until**: Waits until the approval is completed, sending reminder emails if necessary.
    - **Set Variable (varApproval-Completed)**: Sets `varApproval-Completed` to true once approved.
    - **Compose Complete Date**: Converts the approval completion date to Singapore Standard Time.
    - **Condition**: Checks if the approval outcome is "Approve".
      - **If true**:
        - **Apply to each (approval responses)**: Iterates over approval responses and updates the item with "Approved" status.
        - **Send an Email Notification**: Sends an email notification for approval.
      - **If false**:
        - **Apply to each (approval responses)**: Iterates over approval responses and updates the item with "Rejected" status.
        - **Send an Email Notification (Reject)**: Sends an email notification for rejection.
  - **If false**:
    - **Apply to each (approval responses)**: Iterates over approval responses and updates the item with "Pending" status.
    - **Send an Email Notification (Pending)**: Sends an email notification for pending approval.
    - **Terminate**: Terminates the flow.

### 7. Final Steps
- **Compose (UTC to SST)**: Converts the current UTC time to Singapore Standard Time.
- **Condition**: Checks if the `Approver0` field is null.
  - If true, it proceeds with the approval process as described above.

## Summary
This flow automates the approval process for purchase requests, including handling attachments, sending approval requests, and sending email notifications based on the approval outcome.

## Requirements
- Access to Power Automate
- Access to the specified SharePoint site and list
- Permissions to create and update items in the SharePoint list



# Screenshot detail of the flow
![image](https://github.com/user-attachments/assets/15c97788-2959-49b5-9083-ed24ab0a1258)
![image](https://github.com/user-attachments/assets/212f9cae-cc00-476d-a4d6-ae7502e248e6)

> add Parallel branch for Do until loop for to verify if approver action has done -reminder
![image](https://github.com/user-attachments/assets/e0573349-e090-40b8-8d4e-79d4d362900a)
> ![image](https://github.com/user-attachments/assets/a1260808-aa04-4a13-97c8-f5fcc391e036)

> approve 
![image](https://github.com/user-attachments/assets/f83995e7-9d09-4149-8865-706d282719a1)




![image](https://github.com/user-attachments/assets/a8e266a0-d0f4-466d-a8dc-3b2d8980e048)# 📌 Jira Issue Tracking with Power Automate

## 📖 Overview
This guide explains how to track Jira issue field changes using Power Automate. It covers fetching Jira data via API, storing it in an Excel table, and triggering alerts when specific fields change.

---

## 🚀 Prerequisites
- **Jira API Access** (Ensure you have API tokens and project access)
- **Power Automate License**
- **Excel File (Stored in OneDrive or SharePoint)**
- **Jira Project Key** (Run `/rest/api/3/project` to find it)

---

## 🔗 Jira API Setup
1. **Find Your Jira Cloud Base URL**
   ```plaintext
   https://yourdomain.atlassian.net
   ```
2. **Generate an API Token**
   - Go To `you Jira Account setting > Security > API Token > Create and Manage API tokens` → Copy the token

3. **Check Your Jira Project Key**
   ```plaintext
   GET https://yourdomain.atlassian.net/rest/api/3/search?jql=<replace your jql queries>
   ```  

5. **JQL Query for Issue Tracking**
   ```plaintext
   Status not in (Resolved) AND project = "your Project Name" AND statusCategory != Done AND status = "Waiting for Support" ORDER BY created ASC, resolutionDate DESC
   ```

6. **Fully Encoded API URL**
   ```plaintext
   https://yourdomain.atlassian.net/rest/api/3/search?jql=Status%20not%20in%20(Resolved)%20AND%20project%20=%20%22your%20Project%20Name%22%20AND%20statusCategory%20!=%20Done%20AND%20status%20=%20%22Waiting%20for%20Support%22%20ORDER%20BY%20created%20ASC,%20resolutionDate%20DESC
   ```

---

## ⚡ Power Automate Flow Steps
### **Step 1: Trigger the Flow**
- Use a **Recurrence Trigger** to run the flow periodically.
- but for in my attached file , I use Manualy trigger action.

### **Step 2: Call the Jira API**
- Add an `HTTP` action.
- **Method:** `GET`
- **URI:** `[Your Jira API URL]`
- **Headers:**
  ```json
  {
    "Authorization": "Basic [Your Base64 Encoded API Token]",
    "Content-Type": "application/json"
  }
  ```

### **Step 3: Parse JSON Response**
- Add a `Parse JSON` action.
- Use the response from the HTTP request.

### **Step 4: Store Data in Excel**
- Use `List Rows Present in a Table` to fetch existing data.
- Use `Add a row into a table` to insert new records.

### **Step 5: Compare Fields for Changes**
- Use `Condition` to check if key fields (e.g., `Component`, `Status`, `Labels`) have changed.

### **Step 6: Send an Alert**
- If a change is detected, send an email or Teams notification.

![image](https://github.com/user-attachments/assets/d62e01ae-1a17-4553-9901-8d60ee34b286)


---

## Detail Screenshot Flow and result
![image](https://github.com/user-attachments/assets/e23c7f58-348e-4a4d-ac75-2aa6e9db95a0)
![image](https://github.com/user-attachments/assets/bf4a7690-c52f-4e3f-93e3-65cdffba426d)
![image](https://github.com/user-attachments/assets/869be092-3138-401e-b9fd-e585b035cd74)
![image](https://github.com/user-attachments/assets/6b9d2747-53cc-4a91-9a5e-3b937e4c2c06)

## 📌 Future Improvements
- **Enhance notifications**: Implement email or Teams alerts when an issue changes.
- **Optimize storage**: Use a database instead of Excel for better scalability.
- **Improve tracking**: Log historical changes to track trends in issue updates.

## 📌 Author
[Saw Gwe Aw]


## 📚 References
- [Jira REST API Docs](https://developer.atlassian.com/cloud/jira/platform/rest/v3/)
- [How to Create a Jira Ticket Using Power Automate](https://200oksolutions.com/blog/create-jira-ticket-using-power-automate/)
- [Power Automate Documentation](https://learn.microsoft.com/en-us/power-automate/)






# 1 Sharepoint list setting
sharepoint list name: Wifi Guest Request

![image](https://github.com/user-attachments/assets/92c7ae35-64a9-497f-a329-c44a2c639196)

# 2 Sharepoint list setting
Sharepoint list name: Wifi Guest Password
![image](https://github.com/user-attachments/assets/c523e846-9a7f-44d6-b70b-3c70eddb0e06)

to store the password this is where the Network team to update the generated password in it periodaly and sent reminder with Powerautomate flow


# SharePoint WiFi Password Notification Flow

## Overview
This project automates the process of sending WiFi passwords to external guests and internal staff based on user type. It retrieves necessary images, constructs email content, and sends notifications accordingly. Additionally, it updates SharePoint list items to clear sensitive information after processing.

## Trigger
- **When an item is created**: This trigger initiates the flow when a new item is created in a specific SharePoint list.

## Actions
1. **Get file content using path (logo)**: Retrieves the content of a logo image from a specified path in SharePoint.
2. **Get file content using path (footer)**: Retrieves the content of a footer image from a specified path in SharePoint.
3. **Compose (logo)**: Converts the logo image content to a data URI format.
4. **Compose (footer)**: Converts the footer image content to a data URI format.
5. **Initialize variable (BCC external email)**: Initializes a variable to store the BCC email address.
6. **Get items (password)**: Retrieves items from a SharePoint list based on a date filter.
7. **Condition 2**: Checks if the user type is "External Guest".
   - **If true**:
     - **Apply to each**: Iterates over the retrieved items.
     - **Send an HTTP request to SharePoint**: Sends a GET request to retrieve the QR image for external guests.
     - **Parse JSON (output from HTTP - QRimg-ext)**: Parses the JSON response to extract the QR image URL.
     - **Compose**: Converts the QR image content to a data URI format.
     - **Parse JSON (output from Compose statement)**: Parses the JSON response to extract additional details.
     - **Get file content**: Retrieves the content of the QR image from SharePoint.
     - **Compose (QR-external 2)**: Converts the QR image content to a data URI format.
     - **Condition**: Checks if the BCC email variable contains a specific value.
       - **If true**: Sends an email notification to the external guest without BCC.
       - **Else**: Sends an email notification to the external guest with BCC.
     - **Update item 2**: Updates the SharePoint item to clear the guest password and QR link fields.
   - **Else**:
     - **Apply to each 3**: Iterates over the retrieved items.
     - **Send an HTTP request to SharePoint (int)**: Sends a GET request to retrieve the QR image for internal staff.
     - **Parse JSON (output from HTTP - QRimg-int)**: Parses the JSON response to extract the QR image URL.
     - **Compose 2**: Converts the QR image content to a data URI format.
     - **Parse JSON (output from Compose statement-2)**: Parses the JSON response to extract additional details.
     - **Get file content 2**: Retrieves the content of the QR image from SharePoint.
     - **Compose (QR-int)**: Converts the QR image content to a data URI format.
     - **Send an email notification (V3) - internal staff**: Sends an email notification to the internal staff with the QR image and password.
     - **Update item 3**: Updates the SharePoint item to clear the external password and QR link fields.
8. **Compose (@)**: Composes a value for further use in the flow.
9. **Add to time**: Adds one month to the current date.
10. **Compose 2 (BCC external mail)**: Composes the BCC email address.
11. **Get item (Password)**: Retrieves a specific item from a SharePoint list to get the internal and external passwords.
12. **Update item**: Updates the SharePoint item with the retrieved passwords and QR links.

## Summary
This flow automates the process of sending WiFi passwords to external guests and internal staff based on the user type. It retrieves necessary images, constructs email content, and sends notifications accordingly. Additionally, it updates the SharePoint list items to clear sensitive information after processing.

## Requirements
- Access to SharePoint
- Appropriate permissions to read and write to the SharePoint list
- Email service configured for sending notifications

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing
Contributions are welcome! Please feel free to submit a pull request or open an issue for any suggestions or improvements.

## Contact
For any inquiries, please contact [Your Name](mailto:your.email@example.com).


## 2nd flow

### Screenshot 
![image](https://github.com/user-attachments/assets/38b9aeb8-5aab-4c24-b04f-20d0af33efc8)
  > compose- start of month today > expression > startOfMonth(utcNow())
> ![image](https://github.com/user-attachments/assets/30937c15-4319-4e83-b8a4-0e4972f6e17b)


  > compose - start of mont tomorrow > express > startOfMonth(addDays(utcNow(),1))
> ![image](https://github.com/user-attachments/assets/60fa0956-d98d-4453-91cf-79f6ee08e2bc)

  > today - convert UTC to SST > expression > convertFromUtc(utcNow(),'Singapore Standard Time','dd/MM/yyyy')
> 
  > tomorrow - convert UTC to SST > expression >  convertFromUtc(addDays(utcNow(),1),'Singapore Standard Time','dd/MM/yyyy')
> 

# 3d flow QR code generator

# Intro 
The purpose of this project is to improve the user experience for employees who need to request laptops. Currently, employees have to contact the IT/procurement team to check the laptop specifications and prices, and then get approval from their manager via email or a physical request form. This is a time-consuming and inefficient process. To streamline this process, I am going to create a digital workspace for end-users, where they can easily select and request order laptops, and get approval from their managers online internally


I built this project based on the existing Powerapps Template "Asset Checkout"
![image](https://github.com/SGA-JS/IT-Assets-Order-apps/assets/73696641/3b2cca6a-2a03-427c-932e-c2c32ef0f902)
- the data for this template is based on local excel sheet. I convert the existing excel sheet to Sharepoint list.
- I modify the existing powerapp template to my business needs.. such as multiple Items filter options, manager name , Popup confirmation and integrated them
with Powerautomate for manager approval.


# Setup the Following Sharepoint List

## SPList 1- ITAssets-Products
![image](https://github.com/SGA-JS/IT-Assets-Order-apps/assets/73696641/c063c115-f6b4-4e69-a675-a0ce50d1099a)

## SPList 2- ITAssets-Categories
![image](https://github.com/SGA-JS/IT-Assets-Order-apps/assets/73696641/b6cec334-3aa0-4a96-b455-dae70eed7dfa)

## SPList 3- ITAssets-Assets
![image](https://github.com/SGA-JS/IT-Assets-Order-apps/assets/73696641/f9a17f35-6ae2-4623-8030-edab7c0a62a1)


# App screen

- It has 4 Categories - Laptops, Keyboards, Monitor and Mice
![image](https://github.com/SGA-JS/IT-Assets-Order-apps/assets/73696641/9528d8f2-9ae4-4ad6-9fb2-9a28c59319ec)

- filter button is to filter the laptop[only] items (for this moment)
![image](https://github.com/SGA-JS/IT-Assets-Order-apps/assets/73696641/e4468ade-d069-4dba-81ca-58d0cec59c5d)


- when select an Item > will go to Request form screen
  ![image](https://github.com/SGA-JS/IT-Assets-Order-apps/assets/73696641/32279c75-05cf-43cd-a2c7-f3f75af9dd28)
  - the button -"Request New Laptop" will be activated after user have filled in all form input

- Once the Item is submitted. It will automatically send email alert to the respctive manager for approval.
- One the manager has approved the laptop request will send the email alert to IT and requester.




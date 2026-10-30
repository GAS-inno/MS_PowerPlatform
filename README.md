# MS_PowerPlatform

This repository contains a collection of Microsoft Power Platform solutions built for internal business automation and employee productivity. It includes Power Apps for employee and operational use cases, as well as Power Automate flows for approvals, notifications, reporting, and process automation.

The projects in this repository demonstrate practical scenarios such as room booking, desk reservation, employee services, IT asset requests, probation workflows, guest Wi-Fi management, invoice processing, Jira tracking, and purchase approvals.

## Repository Overview

The repository is organized into multiple project folders, each representing an independent solution or automation implementation.

## Project Structure

```text
MS_PowerPlatform/
├── PowerApp_APAC_Employee_Hub/
├── PowerApp_BookARoom/
├── PowerApp_Desk_Reservation_With_FloorMap/
├── PowerApp_HotDesk/
├── PowerApp_IT_HardwareRequest/
├── PowerApp_ProbationAssessmentForm/
├── PowerApp_Wifi_Guest_request_and_QRcode_Password_generate/
├── PowerAutomate_Desktop/
├── PowerAutomate_Jira_Tickets_Tracking/
├── PowerAutomate_PurchaseApprovalflow_with _reminder/
├── README.md
└── .gitignore (if present in the repo)
```

## Projects Included

| Project | Type | Description |
| --- | --- | --- |
| PowerApp_APAC_Employee_Hub | Power App | Employee-facing hub for APAC users, likely for internal employee access and services. |
| PowerApp_BookARoom | Power App | Meeting room booking solution with country-based filtering, room capacity display, booking confirmation, and meeting cancellation. |
| PowerApp_Desk_Reservation_With_FloorMap | Power App | Desk reservation app with floor map support to help employees reserve workspaces. |
| PowerApp_HotDesk | Power App | Hot desk booking solution for flexible office seating. |
| PowerApp_IT_HardwareRequest | Power App | IT hardware request app for laptops and devices, with manager approval workflow. |
| PowerApp_ProbationAssessmentForm | Power App | Probation assessment process for HR, managers, and employees using a structured review workflow. |
| PowerApp_Wifi_Guest_request_and_QRcode_Password_generate | Power App + Flow | Guest Wi-Fi request and password/QR code delivery automation for both internal and external users. |
| PowerAutomate_Desktop | Power Automate Desktop | Desktop automation to extract invoice data from PDF files and prepare it for Excel processing. |
| PowerAutomate_Jira_Tickets_Tracking | Power Automate | Jira issue monitoring and tracking flow, including change detection and alerting. |
| PowerAutomate_PurchaseApprovalflow_with _reminder | Power Automate | Purchase request approval workflow with reminders, attachment handling, and status notifications. |

## Key Use Cases

This repository covers a range of workplace scenarios:

- Employee self-service applications
- Workplace booking and reservation management
- Meeting room and desk scheduling
- IT asset requests and approvals
- HR and probation management
- Guest Wi-Fi request automation
- PDF-based finance processing
- Jira monitoring for operational tracking
- Purchase request approval automation

## Technology Stack

- Microsoft Power Apps
- Power Automate (Cloud Flows and Desktop Flows)
- SharePoint Lists / Microsoft Lists
- Microsoft 365 / Office 365
- Excel for reporting and data processing
- Jira REST API integration
- QR code generation and email notifications

## Typical Workflow

Most solutions follow a common pattern:

1. Capture request or action in a Power App or SharePoint list.
2. Validate or route the request based on business logic.
3. Trigger a Power Automate workflow.
4. Send approval, reminder, or notification emails.
5. Update records and maintain status tracking.

## Prerequisites

To use or adapt these solutions, you will typically need:

- A Microsoft 365 / Power Platform environment
- Power Apps access
- Power Automate access
- SharePoint or Microsoft Lists permissions
- Relevant connectors and data sources configured in your environment
- Jira API access for the Jira tracking project, if used

## How to Use This Repository

1. Open the folder for the scenario you want to implement.
2. Review the project README in that folder for details and setup instructions.
3. Import the .msapp or flow package into your Power Platform environment.
4. Reconnect the app/flow to your SharePoint lists, Excel files, or APIs.
5. Update any hardcoded values such as email addresses, URLs, IDs, or list names.

## Notes

- Several folders contain exported Power App packages (.msapp) and Power Automate flow exports (.zip).
- Some projects are designed as learning and customization examples rather than production-ready deployments without environment-specific adjustments.
- Review each subfolder README before implementation because setup requirements differ by project.

## License

This repository does not currently declare a specific license in the root project file. Please check each project folder or repository settings for any additional licensing or usage restrictions.

## Summary

MS_PowerPlatform is a practical collection of business process automation projects built on Microsoft Power Platform. It demonstrates how low-code solutions can be used to improve employee experience, automate approvals, track operational work, and simplify common business tasks.

---

For more detailed guidance, open the individual project folders and read their README files.

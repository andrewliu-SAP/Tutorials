---
author_name: Archana Shukla
author_profile: https://github.com/ArchanaShukla/
title: Create and Configure Forms
description: Add forms to start the business process, send tasks for approvals and notify business users
auto_validation: true
time: 25
tags: [ tutorial>beginner, software-product>sap-business-technology-platform, tutorial>free-tier ]
primary_tag: software-product>sap-process-automation
---

## Prerequisites
 - [Subscribe to SAP Process Automation using Booster in SAP BTP Free Tier](spa-subscribe-booster)
 - Complete [Create a Business Process](spa-create-process)

## Details
### You will learn
  - How to add interactive forms in the process
  - How to design the form with layout and input fields using drag-and-drop approach
  - How to configure the forms as the process steps

---
Tasks are a part of any business process. **SAP Process Automation** helps you to create forms that are made available to the business users in their inboxes to take relevant action.

These interactive forms can be created by dragging and dropping the text elements and input fields into the canvas. Once a form has been created, it can then be used as a process trigger to start the process or added as an approval step in the business process.

Let us now explore how these different forms are created. In the steps below, you will create three forms which will be used to:

-	Start the approval process.
- Send a task in the inbox of the business user for approval.
- Notify the requester for approval or rejection.

[ACCORDION-BEGIN [Step 1: ](Create a form to trigger a business process)]

First you will create a trigger form that will start the business process. For that, you have to open your process in the process builder and add a new form.

1. Choose **New Form** in **Trigger Settings**.

    !![Select Starting Node](unit3-00.png)

2. In the pop-up for new form, do the following:
    - Enter the **Name** as **Order Processing Form**.
    - Enter a **Description** as **Form to collect order details**.
    - Choose **Create**.

    > The form **Identifier** field is auto-filled.

    !![Fill Form infos](unit3-01.png)

    The form will be added as the **Start Trigger**.

    !![Fill Form infos](unit3-02.png)

3. Choose the three dots and select **Open Editor**

    !![Open Editor](open-editor.png)

4. You will now design the **Form** with available layout and input fields options. You will drag-and-drop the form fields and enter the given names and field settings as per:

    |  Form Fields    | Field Settings with Label
    |  :------------- | :-------------
    |  Headline 1         | Order Approval Request Form
    |  Paragraph          |Please provide the necessary information of your order and submit for approvals.

    - For all below **Input Fields** enter the labels and select the **Required** checkbox.

    |  Form Fields   |  Field Settings with Label
    |  :------------- | :-------------
    | Text | Customer Name
    | Text | Order Number
    | Number | Order Amount
    | Date | Order Date
    | Text | Shipping Country
    | Date | Expected Delivery Date

    !![Design Form](design-form.png)

4. Save the form using the **Save** button on the top-right corner of the screen.

    Your trigger form is ready!

    !![Trigger Form](unit3-04.png)

5. Add the **Order Processing Form** to start the process.

    !![Add Form](add-form.png)

    Now you will design the process with more activities related to approval of the sales order.

[VALIDATE_1]
[ACCORDION-END]

[ACCORDION-BEGIN [Step 2: ](Create and configure an approval form)]

The approval form will be used to get faster and easier approvals from the business users to take informed decisions and getting rid of sending emails. These approval forms could be about approving or rejecting sales order, invoices, or onboarding, IT requests etc. The forms are then converted into tasks in an automated workflow which will appear in the `MyInbox` of the user.

You can create these different forms using the **Form Builder** embedded in the process builder using different form field options. You can drag-and-drop to design and modify them without any coding.  

1. Add a **New Approval Form** to the process.

    !![New Approval Form](unit3-10a.png)

2. In the **Create Approval** dialog box, do the following:
    - Enter **Approval Form** in the **Name** field.
    - Enter **Form to approve or reject the sales order** in the **Description** field.
    - Choose **Create**.

    !![Approval Form](create-approval.png)

3. Design the **Approval Form** in the form builder by dragging-and-dropping fields into the form editor and configuring respective field settings.

    |  Form Fields    | Field Settings with Label
    |  :------------- | :-------------
    | Headline 1 | Approve Sales Order
    | Paragraph  | A new order has been received. Please review and confirm whether the requirements can be met or not.
    | Paragraph  | Sales Order Details:

    - For all below **Input Fields** enter the labels and select the **Read Only** checkbox.

    |  Form Fields   | Field Settings with Label
    |  :------------- | :-------------
    | Text | Customer Name
    | Text | Order Number
    | Number | Order Amount
    | Date | Order Delivery Date

    !![Approval Form](approval-form.png)

    - For all below **Input Fields** enter **only the labels**.

    |  Form Fields| Field Settings with Label
    |  :------------- | :-------------
    | Paragraph | Supplier Acknowledgment
    | Checkbox | I acknowledge that we have received your order and will process it based on the availability
    | Text Area | Message to buyer:

    !![Approval Form](approval-form2.png)

4.	Save the form using the **Save** button on the top-right corner of the screen.

5.	Go back to the process builder to map the process content with the form input fields, and select the **Approval Form** to configure the **General** information section.

    - In the **Subject** box, enter **Review and approve order**.
    - Then select **Order Number > Order Processing Form** from the Process Content.
    - Enter **from**.
    - Select **Customer Name > Order Processing Form** from the Process Content.
    - Enter **company**.
    - For **Users** in **Recipients**, select **Process Started By > Process Metadata** from the Process Content.

    !![03-027](unit3-13.png)

6.	Similarly, go to the **Inputs** tab and map the different input fields (which were marked as read-only in the approval form) by selecting the respective **Process Content** entry.

    > The process content will highlight the entries with the same data type of the input field. For example: if the input field is of Number type then Process Content will show only number-type entries.

    | Form Input Fields| Process Content Entry
    |  :------------- | :-------------
    | Customer Name | Order Processing Form > Customer Name
    | Order Delivery Date | Order Processing Form > Expected Delivery Date
    | Order Amount | Order Processing Form > Order Amount
    | Order Number | Order Processing Form > Order Number

    !![03-027](unit3-14.png)

7. **Save** the process.

[VALIDATE_2]
[ACCORDION-END]


[ACCORDION-BEGIN [Step 3: ](Create and configure form for notifications)]

After the user approves or rejects the request, the next step is to create notifications. These notifications will inform the requester whether their sales order is approved or rejected, and will be sent either via an email or through the form.
These notifications will appear in the inbox of the requester as a task.

1. Add a **New Form** to the process.

    !![New Approval Form](unit3-20.png)

2. In the **Create Form** dialog box, do the following:
    - Enter **Order Confirmation Form** in the **Name** field.
    - Enter **Notification form to inform whether the sales order is approved by the supplier** in the **Description** field.
    - Choose **Create**.

    !![03-026](unit3-21.png)

3. Double click the form in the process builder to open the form builder. In the form builder, design the form to notify the requester of the order confirmation.

    | Form Fields | Field Settings with Label
    |  :------------- | :-------------
    | Headline 1 | Order Confirmation
    | Paragraph  |Your order has been received and accepted for delivery. We will send you the details as soon as the order is shipped. You can find the details of your order below, please review and verify your request:
    | Text Area  | Message from the supplier:
    | Paragraph  | Your Sale's Order Details:

    - For all below **Input Fields** enter the labels and select the **Read Only** checkbox.

    | Form Fields| Field Settings with Label
    |  :------------- | :-------------
    | Text | Order Number
    | Number | Order Amount
    | Date | Expected Delivery Date

    !![Order Confirmation](order-confirmation.png)

4.	Save the form using the **Save** button on top-right corner of the screen.

5.	Go back to the process builder to map the process content with the form input fields, and select the **Order Confirmation** form to configure the **General** information section.

    - In the **Subject** box, enter **Your order**.
    - Then select **Order Number > Order Processing Form** from the Process Content.
    - Enter **has been successfully received**.
    - For **Users** in **Recipients**, select **Process Started By > Process Metadata** from the Process Content.

    !![03-027](unit3-23.png)

6.	As done before in the approval form, go to the **Inputs** section and map the different input fields (which were marked as read-only) with the respective process content entries.

    > The process content will highlight the entries with same data type of the input field. For example: if the input field is of Number type then Process Content will show only number-type entries.

    | Form Input Fields| Process Content Entry
    |  :------------- | :-------------
    | Order Number | Order Processing Form > Order Number
    | Message from the supplier | Approval Form > Message to buyer
    | Expected Delivery Date | Order Processing Form > Expected Delivery Date
    | Order Amount | Order Processing Form > Order Amount

    !![03-027](unit3-24.png)

7. **Save** the process.

    With this you completed designing and configuring the notification form. You can copy the same form to create another form to send a rejection notification to the requester.

    > If copy is not available then create the form in the same way and modify the texts wherever relevant as shown below.

8. Add the new form to the rejection route of the approval form.

    !![03-027](unit3-30.png)

9. In the **Create Form** dialog box, do the following:
    - Enter **Order Rejection Form** in the **Name** field.
    - Enter **Notification form to inform that the sales order is rejected by the supplier** in the **Description** field.
    - Choose **Create**.

    !![03-026](unit3-31a.png)

10. Design the order rejection form in the form builder.

    - Do not forget the **Save** the form once completed.

    | Form Fields | Field Settings with Label
    |  :------------- | :-------------
    | Headline 1 | Order Rejection
    | Paragraph  |We are sorry to inform you that your order cannot not be accepted. Any inconvenience caused due to refusal of order is regretted. You can find the reason of rejection and the details of your order below, please confirm the request:
    | Text Area  | Message from the supplier:
    | Paragraph  | Your Sale's Order Details:

    - For all below **Input Fields** enter the labels and select the **Read Only** checkbox.

    | Form Fields| Field Settings with Label
    |  :------------- | :-------------
    | Text | Order Number
    | Number | Order Amount
    | Date | Expected Delivery Date
    | Paragraph | Please press the SUBMIT button to acknowledge the order status.

    !![Order Rejection](order-rejection.png)

    - Do not forget the **Save** the form once completed.

    !![Save Order Rejection](save-order-rejection.png)

11.	Go back to the process builder and configure the order rejection form.

    - Configure the **General** section.

    | Property| Value
    |  :------------- | :-------------
    | Subject | Your order, **Order Number > Order Processing Form**, is rejected by the supplier
    | Priority| High
    | Recipients | **Process Started By > Process Metadata**

    !![03-026](unit3-34.png)

    - Configure the **Inputs** section.

    |  Form Input Fields  | Process Content Entry
    |  :------------- | :-------------
    | Expected Delivery Date | Order Processing Form > Expected Delivery Date
    | Message from the supplier | Approval Form > Message to buyer
    | Order Amount | Order Processing Form > Order Amount
    | Order Number | Order Processing Form > Order Number

    !![03-026](unit3-35.png)

12.	Finally, connect the outgoing flow of the order rejection form to the **End** activity.

    !![03-026](unit3-36.png)

    With this you complete the process design of your business process. You have experienced building a process in a completely no-code environment and with no technical know-how. You used our new enhanced process builder to create a one-step approval process with trigger form, approval form and notification forms.

[VALIDATE_3]
[ACCORDION-END]
---

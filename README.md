# RPA-Onboarding-Process

Part 1: Data Retrieval and Prioritization (Part 1 only must be implemented as a lambda function on AWS using Node JS)

Fetch Employee Data:-
---------------------
1. Make an HTTP GET request to the following public API endpoint to retrieve a list of all employees:https://dummy.restapiexample.com/api/v1/employees.
2. Parse the JSON response to extract the employee data (id, employee_name, employee_salary, employee_age).

Prioritize and Queue Employees:-
-------------------------------
1. Add the retrieved employee records to a new UiPath Orchestrator Queue named "New Hires".
2. The priority of each queue item must be set based on the following business rules:
	⦁ High Priority: Employees with a salary greater than $300,000.
	⦁ Normal Priority: Employees with a salary between $100,000 and $300,000.
	⦁ Low Priority: All remaining employees.

Part 2: Web Automation & Data Entry

Process High-Priority Hires:-
-----------------------------
1. For each High Priority item from the queue, perform the following steps.
2. Navigate to the web form at https://rpachallenge.com/.
3. Input the following data for the employee:

	⦁ First Name: The first name of the employee (you will need to parse the employee_name field).
	⦁ Last Name: The last name of the employee.
	⦁ Email: Construct an email address using the format FirstName.LastName@corp.net.
	⦁ Phone Number: Use the employee's id as their phone number for this exercise.
	⦁ Company Name: Use "MegaCorp Inc.".
	⦁ Role in Company: Use "Senior Analyst".
	⦁ Address: Use the employee_salary as the address for this exercise.

4. Click the "Submit" button.

Part 3: QR Generation & File Handling

Generate IT Asset QR Code:-
---------------------------
1. For each High Priority employee processed successfully in Part 2, Navigate to the website at. https://www.the-qrcode-generator.com/
2. Generate a QR code image containing the employee's ID and name as plain txt  (e.g., ID: 21 - Name: Tiger Nixon).
3. Download the resulting QR code image and save it locally in a "QRCodes" folder, naming the file [EmployeeID]_[EmployeeName].png.

Part 4: Reporting and Notification

Create an Excel Report:-
------------------------
1. Generate a new Excel file named Onboarding_Report_[Date].xlsx.
2. The file must contain one sheet:
	⦁ Processed_Onboarding: This sheet should contain the details of all High Priority employees that were successfully entered into the web form. 		  Include columns for Employee ID, Name, Salary, and the file path of their generated QR Code.

Send Email Notification:-
-------------------------
1. Send an email to manager@example.com.
2. The Subject should be "Daily Onboarding Process Report - [Date]".  inargument.dt_sumarry.row.count
3. The Body of the email must contain a brief summary of the robot's work:
	⦁ "The daily onboarding process has been completed. All Employees Processed: [Count]"
	⦁ "High Priority Employees Processed: [Count]"
	⦁ "Normal and Low Employees in Queue: [Count]"
4. Attach the Onboarding_Report_[Date].xlsx file to the email.
5. Compress and Attach "QRCodes" Folder to the mail.

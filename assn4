PHASE 1 — LOGIN TO SALESFORCE
Step 1
Open Salesforce Developer Org.
Login using:
•	Username 
•	Password 
________________________________________
PHASE 2 — CREATE APP
Step 2 — Open App Manager
1.	Click ⚙️ Setup 
2.	Search:
App Manager
3.	Open App Manager 
________________________________________
Step 3 — Create Lightning App
1.	Click:
New Lightning App
________________________________________
Step 4 — Enter App Details
Field	Value
App Name	Hospital Management
Description	Hospital Management System
Click:
Next
________________________________________
Step 5 — Navigation Settings
Select:
Option	Value
Navigation Style	Standard Navigation
Supported Form Factors	Desktop and Phone
Setup Experience	Setup
Click:
Next
________________________________________
Step 6 — Utility Items
Skip this page.
Click:
Next
________________________________________
Step 7 — Navigation Items
Add:
•	Home 
•	Reports 
Click:
Next
________________________________________
Step 8 — Assign Profiles
Move:
System Administrator
to selected profiles.
Click:
Save & Finish
________________________________________
PHASE 3 — CREATE OBJECTS
OBJECT 1 — PATIENTS
Step 9 — Open Object Manager
1.	Setup 
2.	Search:
Object Manager
________________________________________
Step 10 — Create Custom Object
1.	Click:
Create → Custom Object
________________________________________
Step 11 — Enter Details
Field	Value
Label	Patients
Plural Label	Patients
Record Name	Patient Name
Click:
Save
________________________________________
Step 12 — Add Fields to Patients
Open:
Fields & Relationships → New
Create these fields one by one:
Field Label	Type
Age	Number
Gender	Picklist
Phone Number	Phone
Email	Email
Address	Text Area
Disease	Text
Status	Text
Save every field.
________________________________________
OBJECT 2 — DOCTORS
Step 13 — Create Doctors Object
Create another custom object.
Field	Value
Label	Doctors
Record Name	Doctor Name
Save.
________________________________________
Step 14 — Add Doctor Fields
Create:
Field Label	Type
Specialization	Text
Phone Number	Phone
Email	Email
Department	Text
Experience	Number
________________________________________
OBJECT 3 — APPOINTMENT
Step 15 — Create Appointment Object
Field	Value
Label	Appointment
Record Name	Appointment ID
Save.
________________________________________
Step 16 — Add Appointment Fields
Create:
Field Label	Type
Appointment Date	Date
Appointment Time	Time
Symptoms	Text Area
Remarks	Text
________________________________________
PHASE 4 — CREATE RELATIONSHIPS
Step 17 — Patient Lookup Relationship
Inside Appointment object:
1.	Fields & Relationships 
2.	New 
Select:
Lookup Relationship
Click:
Next
Related To:
Patients
Field Label:
Patient
Save.
________________________________________
Step 18 — Doctor Lookup Relationship
Repeat:
Option	Value
Relationship Type	Lookup
Related Object	Doctors
Field Label	Doctor
Save.
________________________________________
OBJECT 4 — BILLING
Step 19 — Create Billing Object
Field	Value
Label	Billing
Record Name	Bill Number
Save.
________________________________________
Step 20 — Add Billing Fields
Create:
Field	Type
Amount	Currency
Payment Status	Picklist
Payment Date	Date
________________________________________
Step 21 — Master Detail Relationship
Inside Billing:
1.	Fields & Relationships 
2.	New 
Choose:
Master-Detail Relationship
Related To:
Patients
Field Label:
Patient
Save.
________________________________________
OBJECT 5 — DEPARTMENTS
Step 22 — Create Departments Object
Field	Value
Label	Departments
Record Name	Department Name
Save.
________________________________________
PHASE 5 — CREATE TABS
Step 23 — Open Tabs Setup
1.	Setup 
2.	Search:
Tabs
________________________________________
Step 24 — Create Custom Object Tabs
Under:
Custom Object Tabs
Click:
New
Create tabs for:
•	Patients 
•	Doctors 
•	Appointment 
•	Billing 
•	Departments 
Choose any icon/style.
Save each.
________________________________________
PHASE 6 — ADD TABS TO APP
Step 25 — Edit App
1.	Setup 
2.	App Manager 
3.	Find:
Hospital Management
4.	Click:
▼ → Edit
________________________________________
Step 26 — Navigation Items
Add:
•	Patients 
•	Doctors 
•	Appointment 
•	Billing 
•	Departments 
Move to Selected Items.
Click:
Save
________________________________________
PHASE 7 — CREATE TRIGGER
Step 27 — Open Trigger Section
1.	Setup 
2.	Object Manager 
3.	Open:
Appointment
4.	Click:
Triggers
________________________________________
Step 28 — New Trigger
Click:
New
Trigger Name:
AppointmentTrigger
________________________________________
Step 29 — Paste Trigger Code
trigger AppointmentTrigger on Appointment__c (before insert) {

    for(Appointment__c app : Trigger.new) {

        app.Remarks__c = 'Appointment Confirmed';
    }
}
Click:
Save
________________________________________
PHASE 8 — TEST PROJECT
Step 30 — Launch App
1.	Click App Launcher (9 dots) 
2.	Open:
Hospital Management
________________________________________
Step 31 — Add Patient Records
Open:
Patients → New
Example:
Field	Value
Name	Rahul Sharma
Age	22
Disease	Fever
Save.
________________________________________
Step 32 — Add Doctor Records
Open:
Doctors → New
Example:
Field	Value
Name	Dr. Mehta
Specialization	Cardiology
Save.
________________________________________
Step 33 — Add Appointment Record
Open:
Appointment → New
Select:
•	Patient 
•	Doctor 
Add:
•	Date 
•	Time 
Save.
________________________________________
Step 34 — Verify Trigger
Open Appointment record.
You should see:
Remarks = Appointment Confirmed
________________________________________
Step 35 — Create Billing Record
Open:
Billing → New
Add:
•	Patient 
•	Amount 
•	Payment Status 
Save.
________________________________________
PHASE 9 — REPORTS
Step 36 — Create Report
1.	Open:
Reports
2.	New Report 
3.	Choose:
Patients
4.	Add fields 
5.	Save report 
________________________________________
FINAL PROJECT STRUCTURE
Hospital Management
│
├── Patients
├── Doctors
├── Appointment
│     ├── Patient Lookup
│     └── Doctor Lookup
├── Billing
│     └── Patient Master-Detail
└── Departments


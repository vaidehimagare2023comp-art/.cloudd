Salesforce Student Management CRUD Application — Complete Step-by-Step Guide
This guide creates a complete CRUD application using:
•	Custom Object 
•	Apex Class 
•	Visualforce Page 
•	Full CRUD UI 
________________________________________
STEP 1 — Create Custom Object
Go to:
Setup → Object Manager → Create → Custom Object
Fill:
Field	Value
Label	Student
Plural Label	Students
Object Name	Student
Record Name	Student Name
Data Type	Text
________________________________________
Enable These Options
✅ Allow Reports
✅ Allow Activities
✅ Allow Search
✅ Allow Bulk API Access
✅ Allow Streaming API Access
✅ Add Notes and Attachments related list
Deployment Status:
✅ Deployed
Click:
Save
________________________________________
STEP 2 — Create Fields
Open:
Student → Fields & Relationships
________________________________________
Field 1 — Roll No
Click:
New
Select:
✅ Number
Click Next.
Fill:
Field	Value
Field Label	Roll No
Length	5
Decimal Places	0
Click:
•	Next 
•	Next 
•	Save 
Final API Name:
Roll_No__c
________________________________________
Field 2 — Department
Click:
New
Select:
✅ Text
Click Next.
Fill:
Field	Value
Field Label	Department
Length	50
Click:
•	Next 
•	Next 
•	Save 
Final API Name:
Department__c
________________________________________
Field 3 — Marks
Click:
New
Select:
✅ Number
Click Next.
Fill:
Field	Value
Field Label	Marks
Length	3
Decimal Places	0
Click:
•	Next 
•	Next 
•	Save 
Final API Name:
Marks__c
________________________________________
STEP 3 — Create Apex Class
Go to:
Setup → Apex Classes → New
Class Name:
StudentManager
Paste this code:
public class StudentManager {

    // Create Student
    public static void addStudent(
        String name,
        Integer roll,
        String dept,
        Integer marks
    ) {

        Student__c s = new Student__c();

        s.Name = name;
        s.Roll_No__c = roll;
        s.Department__c = dept;
        s.Marks__c = marks;

        insert s;
    }

    // Read All Students
    public static List<Student__c> getAllStudents() {

        return [
            SELECT Id,
                   Name,
                   Roll_No__c,
                   Department__c,
                   Marks__c
            FROM Student__c
        ];
    }

    // Update Student Marks
    public static void updateMarks(
        Id studentId,
        Decimal newMarks
    ) {

        Student__c s = [
            SELECT Id, Marks__c
            FROM Student__c
            WHERE Id = :studentId
        ];

        s.Marks__c = newMarks;

        update s;
    }

    // Delete Student
    public static void deleteStudent(Id studentId) {

        Student__c s = [
            SELECT Id
            FROM Student__c
            WHERE Id = :studentId
        ];

        delete s;
    }
}
Click:
Save
________________________________________
STEP 4 — Test Apex Class
Open:
Gear Icon → Developer Console
Then:
Debug → Open Execute Anonymous Window
Paste:
StudentManager.addStudent(
    'Ravi',
    101,
    'CS',
    85
);
Click:
Execute
________________________________________
STEP 5 — Verify Record Inserted
Open Execute Anonymous again.
Paste:
List<Student__c> students =
    StudentManager.getAllStudents();

System.debug(students);
Click Execute.
________________________________________
Check Logs
Inside Developer Console:
1.	Open:
Logs
2.	Double-click latest log. 
3.	Press:
Ctrl + F
4.	Search:
USER_DEBUG
You should see:
(Student__c:{Name=Ravi, Roll_No__c=101, Department__c=CS, Marks__c=85})
________________________________________
STEP 6 — Create Controller Class
Go to:
Setup → Apex Classes → New
Class Name:
StudentController
Paste this code:
public class StudentController {

    public Student__c newStudent { get; set; }

    public List<Student__c> students { get; set; }

    public StudentController() {

        newStudent = new Student__c();

        loadStudents();
    }

    // Load Students
    public void loadStudents() {

        students = [
            SELECT Id,
                   Name,
                   Roll_No__c,
                   Department__c,
                   Marks__c
            FROM Student__c
        ];
    }

    // Insert Student
    public void addStudent() {

        insert newStudent;

        newStudent = new Student__c();

        loadStudents();
    }

    // Update Students
    public void updateStudent() {

        update students;
    }

    // Delete Student
    public void deleteStudent() {

        String studentId =
            ApexPages.currentPage()
                     .getParameters()
                     .get('delId');

        Student__c s = [
            SELECT Id
            FROM Student__c
            WHERE Id = :studentId
        ];

        delete s;

        loadStudents();
    }
}
Click:
Save
________________________________________
STEP 7 — Create Visualforce Page
Go to:
Setup → Visualforce Pages → New
Page Name:
StudentPage
Paste this code:
<apex:page controller="StudentController">

    <apex:form>

        <!-- Add Student -->

        <apex:pageBlock title="Add Student">

            <apex:pageBlockSection columns="2">

                <apex:inputField
                    value="{!newStudent.Name}" />

                <apex:inputField
                    value="{!newStudent.Roll_No__c}" />

                <apex:inputField
                    value="{!newStudent.Department__c}" />

                <apex:inputField
                    value="{!newStudent.Marks__c}" />

            </apex:pageBlockSection>

            <apex:commandButton
                value="Insert Student"
                action="{!addStudent}"
                rerender="studentTable"/>

        </apex:pageBlock>

        <!-- Student List -->

        <apex:pageBlock
            title="Student List"
            id="studentTable">

            <apex:pageBlockTable
                value="{!students}"
                var="s">

                <!-- Editable Columns -->

                <apex:column headerValue="Name">

                    <apex:inputField
                        value="{!s.Name}" />

                </apex:column>

                <apex:column headerValue="Roll No">

                    <apex:inputField
                        value="{!s.Roll_No__c}" />

                </apex:column>

                <apex:column headerValue="Department">

                    <apex:inputField
                        value="{!s.Department__c}" />

                </apex:column>

                <apex:column headerValue="Marks">

                    <apex:inputField
                        value="{!s.Marks__c}" />

                </apex:column>

                <!-- Delete Button -->

                <apex:column headerValue="Delete">

                    <apex:commandButton
                        value="Delete"
                        action="{!deleteStudent}"
                        rerender="studentTable">

                        <apex:param
                            name="delId"
                            value="{!s.Id}"
                            assignTo=
                            "{!$CurrentPage.parameters.delId}"/>

                    </apex:commandButton>

                </apex:column>

            </apex:pageBlockTable>

            <!-- Update Button -->

            <apex:commandButton
                value="Update All"
                action="{!updateStudent}"
                rerender="studentTable"/>

        </apex:pageBlock>

    </apex:form>

</apex:page>
Click:
Save
________________________________________
STEP 8 — Preview Application
Click:
Preview
OR open:
https://YOURDOMAIN.visualforce.com/apex/StudentPage
Example:
https://mydomain-dev-ed.visualforce.com/apex/StudentPage


# Script-Controlled-ACL-Restrict-Record-Access-Based-on-Field-Value
Script-Controlled ACL – Restrict Record Access Based on Field Value 📌 Project Overview This project implements secure record-level access control in the ServiceNow platform using Access Control Lists (ACLs). The project creates a custom Institution Details table and controls access to its records based on: User roles Branch field value Read, Create, Write, and Delete permissions The main security requirement is that users with the bb1 role can view only EEE branch records, while administrators retain full access. Additional roles control record creation, editing, and deletion.
🏫 Academic Details Details Information College Name Sri Sankara Bhagavathi Arts and Science College, Kommadikottai College Code MSU220 Department BCA Year 3rd Year Semester 5 Project Title Script-Controlled ACL – Restrict Record Access Based on Field Value Team Size 3 Members
👥 Team Members Team Leader Name: Jancyrani M Register No: 24082200500112102 NM ID: C15FB6F2EBD7AA7B15E4AB79B9C24944 Email: jancy.rani2817@gmail.com Team Member 2 Name: Harishma S Register No: 24082200500112101 NM ID: DD3905B7E48D98187B44E6FD1EAB1090 Email: Karishmakaris069@gmail.com Team Member 3 Name: Vijayalakshmi C Register No: 24082200500112106 NM ID: 93A9397B000B72AAC754D95AC2289660 Email: viji08082@gmail.com
🎯 Problem Statement In an organization, all users should not have permission to view, create, edit, or delete every record. Without proper access control: Unauthorized users may view confidential records. Users may modify records without permission. Important information may be deleted. Data privacy and security may be affected. This project solves the problem by combining Role-Based Access Control (RBAC) with Script-Controlled ACLs.
💡 Project Idea The project creates a custom ServiceNow table called: Institution Details Table name: u_institution_details The table contains student-related information such as: Student Roll Number Student Name Faculty Name Branch Email Phone Number Description The system contains sample records from: EEE ECE CSE Access is controlled according to the user's role.
🎯 Objectives Create a test user in ServiceNow. Create custom roles bb1, bb2, bb3, and bb4. Create the Institution Details custom table. Add student-related fields. Create sample records for different branches. Configure a Script-Controlled Read ACL. Configure Create, Write, and Delete ACLs. Test access using ServiceNow impersonation. Verify that unauthorized users cannot access restricted records.
🏗️ System Architecture The project contains four main components: Users Admin EEE User Roles bb1 bb2 bb3 bb4 Institution Details Table Stores student and institution-related records. Access Control Lists Read ACL Create ACL Write ACL Delete ACL Access Structure User / Role Permission Admin Full access bb1 View EEE records bb2 Create records bb3 Edit records bb4 Delete records
🗃️ Custom Table Table Name u_institution_details Table Label Institution Details Fields Field Data Type Purpose Student Roll Number Auto Number Unique student ID Student Name Reference (User) Student details Faculty Name Reference (User) Faculty details Branch Choice ECE, EEE, CSE Email String Contact information Phone Number String Contact information Description Multi-line String Additional details
🔐 ACL Implementation

Read ACL Type: Record Operation: Read Table: u_institution_details Role: bb1 Condition: Branch = EEE The Read ACL controls which records the user can view. Script Used
(function () {
    if (gs.hasRole('admin')) {
        return true;
    }

    if (gs.hasRole('bb1')) {
        return true;
    }

    return false;
})();
Note: The Branch = EEE condition is configured as part of the ACL/data condition in the project.

Create ACL Type: Record Operation: Create Table: u_institution_details Role: bb2 Users with bb2 can create new records.
Write ACL Type: Record Operation: Write Table: u_institution_details Role: bb3 Users with bb3 can edit records.
Delete ACL Type: Record Operation: Delete Table: u_institution_details Role: bb4 Users with bb4 can delete records.
👤 Test User A test user named EEE User was created. Field Value User ID EEE User First Name EEE Last Name User Email eeeuser@gmail.com The following roles were assigned: bb1 bb2 bb3 bb4
🧪 Sample Records The project uses sample records with different branch values: Student Branch Student 1 EEE Student 2 ECE Student 3 CSE These records are used to verify ACL behavior.
🔄 Development Workflow The project was implemented using the following steps: Created the EEE User. Created four custom roles. Assigned roles to the user. Created the Institution Details table. Added all required fields. Inserted sample records. Configured the Read ACL with JavaScript. Created Create, Write, and Delete ACLs. Tested permissions using impersonation. Documented the results.
🧪 Testing Testing was performed using Impersonate User in ServiceNow. Test Results Test Case Expected Result Status Read ACL Only EEE records visible Pass User without role No records visible Pass Admin All records visible Pass Create ACL New button visible Pass Write ACL EEE records editable Pass Delete ACL EEE records deletable Pass Final Permission Summary bb1 → View EEE branch records bb2 → Create new records bb3 → Edit EEE records bb4 → Delete EEE records admin → Full access
🛠️ Technologies Used Technology Purpose ServiceNow Application development JavaScript Script-Controlled ACL Access Control Lists Record-level security Role-Based Access Control Permission management GitHub Project version control Google Drive Demo video / project files
📋 Project Phases Phase 1 – Brainstorming & Ideation Identified the need to protect institution and student records using role-based access control. Phase 2 – Requirement Analysis Defined functional, non-functional, user, system, table, and security requirements. Phase 3 – Project Design Designed the system architecture, table structure, roles, and ACL workflow. Phase 4 – Project Planning Planned tasks, responsibilities, resources, timeline, risks, and deliverables. Phase 5 – Project Development Implemented users, roles, custom table, fields, sample records, and ACLs. Phase 6 – Project Testing Tested Read, Create, Write, and Delete permissions using impersonation. Phase 7 – Project Documentation Documented technologies, features, security implementation, advantages, limitations, and future enhancements. Phase 8 – Project Demonstration Demonstrated user creation, role creation, table creation, ACL configuration, testing, and final verification.
📸 Project Screenshots Add the project screenshots in this repository, for example: 01_user_creation.png 02_role_creation.png 03_institution_details_table.png 04_sample_records.png 05_read_acl.png 06_eee_user_view.png 07_admin_view.png 08_create_acl.png 09_write_acl.png 10_delete_acl.png 11_final_verification.png
📂 Suggested Repository Structure

Script-Controlled-ACL/
│
├── README.md
├── documentation/
│   └── Project_Report.pdf
│
├── screenshots/
│   ├── 01_user_creation.png
│   ├── 02_role_creation.png
│   ├── 03_institution_details_table.png
│   ├── 04_sample_records.png
│   ├── 05_read_acl.png
│   ├── 06_eee_user_view.png
│   ├── 07_admin_view.png
│   ├── 08_create_acl.png
│   ├── 09_write_acl.png
│   ├── 10_delete_acl.png
│   └── 11_final_verification.png
│
└── demo/
    └── demo_link.txt
🔗 Project Links Google Drive Project Report / Demo Video: https://drive.google.com/file/d/15EInXNTFXllGKS9aN2j7APTyIfUx72_r/view?usp=sharing

▶️ How to Demonstrate the Project Login to the ServiceNow Developer Instance with Admin access. Open User Administration → Users. Create or open the EEE User. Verify the roles bb1, bb2, bb3, and bb4. Open the Institution Details table. Verify the EEE, ECE, and CSE sample records. Open System Security → Access Control (ACL). Verify the Read, Create, Write, and Delete ACLs. Use Impersonate User. Login as EEE User. Verify the permitted records and operations. Impersonate Admin. Verify that Admin can access all records.
🔒 Security Benefits The project provides: Protection of confidential student records. Role-based access control. Record-level security. Prevention of unauthorized access. Controlled Create, Read, Write, and Delete operations. Practical ServiceNow security implementation.
⚠️ Limitations The current Read access is focused on the EEE branch condition. Correct role assignment is required. The system depends on ServiceNow permissions. Additional branch or department conditions may require additional scripting.
🚀 Future Enhancements Future versions can include: Department-wise dynamic permissions. Automatic role assignment. Email notifications. Audit logging. Approval workflows. More advanced dynamic security conditions.
✅ Conclusion The Script-Controlled ACL – Restrict Record Access Based on Field Value project demonstrates how ServiceNow Access Control Lists can secure records by combining user roles with a Branch field condition. A custom Institution Details table was created with student-related fields. Custom roles were configured for Read, Create, Write, and Delete operations. Testing through impersonation verified the configured permissions, while administrators retained full access. This project provides practical experience in: ServiceNow application development Access Control Lists Role-Based Access Control JavaScript ACL scripting Record-level security Security testing and documentation
👩‍💻 Team Team Leader: Jancyrani M
Team Member: Harishma S
Team Member: Vijayalakshmi C Department: BCA
College: Sri Sankara Bhagavathi Arts and Science College, Kommadikottai
College Code: MSU220

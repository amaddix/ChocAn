# mycode

The ChocAn Simulator
Requirements Document

Table of Contents
Introduction	3
1.1 Purpose and Scope	3
1.2 Target Audience	3
1.3 Terms and Definitions	4
2 Product Overview	4
2.1 Users and Stakeholders	5
2.1.1 ICNH	5
2.1.2 ChocAn	5
2.1.3 Acme Accounting Services	5
2.1.4 Service Providers (End User)	5
2.1.4 Managers (End User)	6
2.2 Use cases	6
2.2.1 Provider checking ChocAn member’s membership validity	6
2.2.2 Provider logs healthcare services provided to a ChocAn member	7
2.2.3 Produce Weekly Manager Report	9
3. Functional Requirements	10
3.1 Member ID Validation	10
3.2 Recording Services Provided	10
3.2.1 Service Code Verification	11
3.2.2 Saving Service Transaction	11
3.2.3 Service Fee Retrieval	11
3.3 Services Database	12
3.4 Accounting Reports	12
3.4.1 Member Accounting Report	12
3.4.2 Provider Accounting Report	12
3.4.3 Manager Accounting Report	13
4 Nonfunctional Requirements	14
4.1 Database Interaction	14
4.1.1 Database Data Retrieval	14
4.1.2 Database Data Storage	14
4.2 Hardware	14
4.3 Acme Accounting Services Integration	14
4.4 ChocAn Member Card Implementation	15
5 Milestones and Deliverables	16
5.1 Design Document	16
5.2 Test Plan	17
5.3 Final Deliverables	17
5.3.1 System Implementation	17
5.3.2 System Verification	18
5.4 Project Report	18

# Introduction
Chocolate addiction is one of the leading health crises in the world today and Chocoholics Anonymous is dedicated to helping the many cope with the far reaching effects of this crisis. Many people misunderstand and misconstrue the difficulties and challenges of chocolate addiction which often leads to shame, further substance abuse and at its worst “la Mort au Choclat”, death by chocolate.  In order to face these concerns, ICNH is dedicated to contributing to problem resolution and addiction management. Chocoholics Anonymous, or ChocAn has tasked our company with developing software to help the organization work with health providers who help treat and manage chocolate addiction. The battle will not be an easy one, but having identified the problem, we have isolated the requirements and demands of developing a system for all parties to manage aspects of healthcare for chocolate addiction. Such aspects include managing records of health services provided, maintaining members history of treatment, and tracking billing services for ChocAn to reimburse.  The following will introduce such demands, specific case situations and evaluate all considerations being made in the development of our software solution. 
# 1.1 Purpose and Scope
This document lists the requirements for the data processing software contracted by Chocoholics Anonymous. It covers all the details concerning the purpose and functionality of the software, as well as information about stakeholders, users, and their relationships with the software. The system specifications listed in this document have been agreed upon by both parties involved, Chocoholic Anonymous and ICNH.  The system is developed to satisfy these specifications.
# 1.2 Target Audience
This document is made available to Chocoholics Anonymous, ICNH, and Acme Accounting Services.  Chocoholics Anonymous may distribute this document internally as needed. Inside ICNH, this document will be limited to system developers, testers, UI developers, as well as their respective managers and project leads.  Acme Accounting Services may distribute this document internally as needed.
# 1.3 Terms and Definitions
- ChocAn - Chocoholics Anonymous: The contractor for this system.
- ICNH - Insert Company Name Here LLC.:The developer of the data processing software for this system.
- Provider/Service Provider: Employees of a party that provides medical services to ChocAn members, and accepts payment for the provided service from ChocAn.
- Service: Consultations and treatments with health care professionals offered by Providers.
- Terminal: The ChocAn terminal designed by a third-party that the data processing software developed by ICNH will be run on.
- Manager: A manager at ChocAn responsible for gathering reports on the services provided throughout the week.
- Summary report: Report containing information of all service transactions performed between the current time and the previous Friday at 11:59 pm. Summary reports are made for specific providers or members.
- Member: A ChocAn member who pays ChocAn monthly for access to ChocAn services.
- Suspended Member: A member that has not paid membership fees for at least a month.
-Validated/Invalid Number: A validated number belongs to a current member that is not a suspended member. An invalid number does not belong to any member.

# 2 Product Overview
The project and subject of this document is the ChocAn data processing software, which is used in conjunction with communication software, accounting software, and terminals provided by one or more separate parties. The data processing software handles data regarding specific members and their accounts, providers and the services they provide, and weekly transaction information compiled into summary reports. Specifics of different use cases for this software are provided in the second part of this section.
Stakeholders are individuals or organizations who are affected by the development process.  A user is an individual or organization that uses the data processing software. Use cases describe interactions between users and the system.
# 2.1 Users and Stakeholders
This section provides a list of people or parties invested in the software in some way. Information about each stakeholder’s involvement in the software is also provided.
# 2.1.1 ICNH
ICNH is responsible for the planning and development of the data processing software.  They maintain communication with the contractor, ChocAn, throughout the development process to ensure that progress is being made towards the desired end product.  ICNH is responsible for system deployment and maintenance of the deployed system.
# 2.1.2 ChocAn
ChocAn is the contractor and is responsible for facilitating the use of the software, including distributing it to their partners and providers for direct use. 
# 2.1.3 Acme Accounting Services
Acme Accounting Services is responsible for financial procedures related to the data processing software.  This includes recording payments of membership feeds, suspending members whose fees are overdue, and reinstating suspended members who have paid what was owed.  Acme is responsible for updating the ChocAn Data Center membership records each evening at 9 P.M through the data processing software created by ICNH.
# 2.1.4 Service Providers (End User)
Providers of services covered by ChocAn will use or will have employees use the data processing software developed by ICNH. They will be using the software in provider mode. The functionality available to providers is described in detail in the following sections.
# 2.1.4 Managers (End User)
ChocAn managers will make use of the data processing software developed by ICNH to perform their weekly duties. They will be using the software in manager mode. The functionality available to the managers is described in detail in the following sections.
# 2.2 Use cases
Use cases defines user-system interactions from the actor’s point of view.  This outlines what the user can expect when interacting with the system.
# 2.2.1 Provider checking ChocAn member’s membership validity
Goal
Provider wishes to check validity of ChocAn member’s membership.
Primary Actor
Healthcare service provider (Provider)
Scope
ChocAn Data Center
Level
User
Precondition
Healthcare service provider is at user terminal with a member’s card or membership number.
Success end condition
ChocAn member’s membership is valid.
Failure end condition
ChocAn member’s membership is invalid or suspended.
Trigger
ChocAn member requests services from Healthcare service provider.
Main Success Scenario
ChocAn member gives Provider their membership card.
Provider slides card through card reader at terminal.
Terminal sends the member number to the ChocAn Data Center.
ChocAn Data Center data processing system checks validity of member number.
System finds a match.
Match is flagged as valid.
System returns success to terminal.
Terminal displays “Validated.”
Extensions
      5a.  No match is found.
             5a.1.  System returns failure to the terminal.
             5a.2.  Terminal displays “Invalid Number”
      6a.  Match is flagged suspended.
             6a.1.  System returns suspended to terminal.
             6a.2.  Terminal displays “Member suspended” and that member has
                       unpaid fees.


# 2.2.2 Provider logs healthcare services provided to a ChocAn member.
Goal
Provider wishes to log healthcare services provided to a ChocAn member.
Primary Actor
Healthcare service provider (Provider)
Scope
ChocAn Data Center
Level
User
Precondition
Provider is at user terminal.
Success end condition
Healthcare service used is saved to the database.
Failure end condition
Provider aborts process or membership is not validated.
Trigger
Member receives healthcare service from a ChocAn provider.
Main Success Scenario
Provider checks validity of ChocAn member’s membership (see Use Case 2.2.1). Returns “Validated.”
Provider enters the date of the services in the format MM-DD-YYYY.
Provider uses Provider Directory to look-up the six-digit service code corresponding to the service provided.
Provider enters the code in the terminal.
Terminal displays the name of the service corresponding to the code entered.
Provider confirms the code/service is correct.
(Optional) Provider enters comments about the service.
Data processing software records the following information to disk:
Current date and time (MM-DD-YYYY  HH:MM:SS).
Date service was provided (MM-DD-YYYY).
Provider number (9 digits).
Member number (9 digits).
Service code (6 digits).
Comments (100 characters) (optional).
Data processing software looks up fees attached to service.
Terminal displays fees to Provider.
Provider fills out form containing the following information:
Current date and time (MM-DD-YYYY  HH:MM:SS).
Date service was provided (MM-DD-YYYY).
Member name (25 chars).
Member number (9 digits).
Service code (6 digits).
Fees to be paid (up to $999.99).
Information is verified to match the record on disk and new information is added to the record. 
Member name (25 chars).
Fees to be paid( up to $999.99).
Extensions
      1a.  Terminal displays “Invalid Number” or “Member suspended.”
             1a.1.  Provider aborts process.
      6a.  Provider does not confirm code/service is correct.
             6a.1.  Provider re-enters code.
             6a.2.  Terminal displays the name of the service corresponding to the
                       code entered.
             6a.3.  This cycles until either Provider confirms the code/service is
                       correct or Provider aborts the process.
      9a.  Data processing software cannot find fee information associated with
             the service.
             9a.1.  Terminal displays “Fee Error” to the Provider.
             9a.2.  Provider fills out form containing the following information:
Current date and time (MM-DD-YYY  HH:MM:SS).
Date service was provided (MM-DD-YYYY).
Provider number (9 digits).
Member number (9 digits).
Service code (6 digits).
Note that system could not find fee information.
      12a. Information entered by the provider does not match information
              previously entered.
              12a.1. Terminal displays mismatched information to screen
              12a.2. Provider re-enters mismatched information
              12a.3. Terminal echos the information and asks if it is correct
              12a.4. If provider verifies the information, update the record, if not,
                         cycle steps 12a.2 through 12a.4.



# 2.2.3 Produce Weekly Manager Report
Goal
Compile a report for the services provided during the week for a specific service provider or member.
Primary Actor
Manager / Scheduled system operation
Scope
ChocAn Data Center
Level
User
Precondition
Provided services have been entered into the system.
Success end condition
There are services to be compiled into a report.
Failure end condition
There were no services provided by any provider for the week.
Trigger
ChocAn manager puts in a request at the terminal.
Main Success Scenario
A request is made to the system for the list of provided services from the specified provider or to the specified member.
The member or provider’s record is found in the database.
All services logged in the record between the previous Friday at 11:59 pm and the current time are gathered from the database.
The data is then output as a text file containing the summary report.
Extensions
      2a.  The member or provider’s record is not found in the database.
# 2a.1. A message appears on the screen saying that the provider or          
         member could not be found.
# 2a.2. The terminal returns to the manager menu.
      3a. There are no services logged within the specified time.
            3a.1.  A message appears on the screen saying that no services were
                      provided this week, the terminal returns to the manager menu.

# 3. Functional Requirements
Here we discuss the primary functionality of this software. Over all, this software was built in order to help properly manage ChocAn’s member data, provider data, and keeping track of the general and daily activities. In addition to this, it must also act as a friendly interface that will assist the members of ChocAn and their Providers with making and receiving payments, as well as finding helpful information about their history with ChocAn.
 
# 3.1 Member ID Validation
Every member subscribed to ChocAn is provided an ID card with a corresponding ID key. They need one of these two items in order to verify their coverage when getting their treatment. For the provider to verify the member status, they would either swipe the ID card or enter the member key. Once doing this, the provider should be notified of whether the member is indeed covered for that service or not. 

In order to be able to relay this information back to the provider, we have to organize and store all the ChocAn member data into a data structure that would be efficient and easy to access. Once the program receives the member key ID from the provider, the program would use that key and search through the data structure until a confirmed match was found, or until we hit the bottom of the list. If the matching key was found and they’re payments were up to date, the program would display ‘VALIDATED’. Otherwise, it would display the reason the member key was unvalid, such as ‘NO MATCHING KEY’ or ‘SERVICE SUSPENDED’ (in the case that they were late on their monthly payments).

# 3.2 Recording Services Provided
After a ChocAn member has been provided treatment, the provider would again swipe their member ID card or enter the member ID key in order to charge the ChocAn account. Once the key returns ‘VALIDATED’,  and the provider has correctly entered all the necessary information, they should be able to charge the account. While doing this they also have the option of inputting some comments on the consultation, like on any recommended follow-ups or treatments.

# 3.2.1 Service Code Verification
In order to successfully charge ChocAn for a service, the provider should be able to give information on the date the service was provided. Following this, they're expected to input the six-digit service code, which indicates what type of service was done for said member. They should be able to find the service code by looking up the provided service in the Provider Directory. If the service code successfully matches with a service, then that service will be displayed and a prompt will be sent to the provider to confirm if this is indeed the service that was done. If no service matches the code provided, then an error message will appear. 

# 3.2.2 Saving Service transaction 
Once confirming the service done, the programs saves all the treatment information as well as the  member data into a record. It stores information such as the current date/time, date service was provided, the provider number, the member number, the service code, and any additional comments the provider may have included. 

# 3.2.3 Service Fee Retrieval
Once the program has recorded the service transaction, it then searches to find the amount owed for that service type. The service fee would then be displayed back to the provider. In order to verify all the service information, the provider is given a form and asked to input the current date/time, service date, member’s name and ID number, the service code and the amount owed. 

# 3.3 Services Database
Another functionality of this software is to allow the provider to easily view the information stored within the provider directory.  This includes an alphabetical list of all the services provided through ChocAn, along with the corresponding service codes and fees. When requested from the provider, the provider directory would then be sent to them through an email attachment. 

# 3.4 Accounting Reports
Every Friday at midnight, the main accounting procedure is run. As this happens, all the services provided throughout the week are totaled up and displayed in a few reports. These reports are then sent out to any and all the ChocAn members, providers and managers, that these reports may concern. All these reports should also be accessible individually anytime during the week, when requested by a ChocAn manager.

# 3.4.1 Member Accounting Report
One report that is sent out goes specifically to any ChocAn member who had received services that week. In this report, the member is provided their name, member ID number, their address (including city, state, and zip). Along with this general member information, the report also informs the member on every consultation they had that week along with information about that service. This information includes the service date, providers name, and the service type. To allow the ChocAn member to easily look through their treatment history, the services listed in this report are sorted by their date.

# 3.4.2 Provider Accounting Report
A report is also sent out to every provider who billed ChocAn within the last week. It gives the provider an overview showing a list of all the consultations they provided ChocAn's members that week. With each consultation it shows the general provider information, such as the name, provider number, and address. It also displays all the information that was filled out on the providers form. This form included information such as the service date, the date/time service was billed to ChocAn, member name, member ID, service code, and the fee owed for the service. The report summarizes all this information by giving the total number of consultations that provider had with ChocAn members throughout the week, as well as the total fee owed to them.

# 3.4.3 Manager Accounting Report
There is also a report given to ChocAn managers for accounts payable. This report displays every provider that needs to be paid for that week, the number of consultations they took, and their total fee owed. In the end it summarizes the total number of providers who helped provide service to ChocAn members, the total number of consultations, and the total amount owed for that week.



# 4 Nonfunctional Requirements
In addition to the aforementioned functional requirements, there are a variety of nonfunctional requirements. A nonfunctional requirement is a feature the software must have, but that isn’t a function of the software. The ChocAn software must interface with an existing ecosystem of software, and here we discuss those nonfunctional requirements.
# 4.1 Database Interaction
The ChocAn software is required to be able to connect to a central ChocAn database. This database will be the primary location where records surrounding ChocAn members will be stored. Each instance of the software will be connected to the ChocAn database to facilitate the consolidation and distribution of data.
# 4.1.1 Database Data Retrieval
Retrieving data from the ChocAn database is essential for generating reports and validating ChocAn membership. Data from the ChocAn database must be easily retrievable and infallible. Data should not ever be received in error.
# 4.1.2 Database Data Storage
Storing data is another requirement for the ChocAn database. Data must be able to flow from each ChocAn terminal to the central database. This process must not be subject to interference or fallibility. 
# 4.2 Hardware
The ChocAn software must run on the ChocAn terminals provided by a third-party company. The software must either be multiplatform or be specifically designed to run on the terminal provider’s machines.
# 4.3 Acme Accounting Services Integration
ChocAn software does not manage financial aspects of the system. ChocAn’s software will interface with Acme Accounting Services’ accounting software. The software is required to be implemented with Acme’s accounting services in mind.
# 4.4 ChocAn Member Card Implementation
The ChocAn software will use ChocAn member cards as identification for ChocAn members. A ChocAn user must be able to use their ChocAn card at a terminal and be identified correctly for services to be charged to their account. 

# 5 Milestones and Deliverables
This section outlines the milestones and deliverables that ICNH will meet and provide while developing the data processing software.  Milestones are expected dates for major steps in the development process, such as beginning the implementation of a plan.  Deliverables are products created in the development process, such as a functional database.
The first milestone is the design document, which will be completed by February 10th, 2020.  This document outlines the architecture of the data processing software.  The second is the test plan, which will be completed by February 24th, 2020.  The test plan describes the scope of the system and the methods that will be employed to test the system and verify its functionality.  On March 13th, 2020, the final deliverable will be completed along with a project report.  The final deliverable is the data processing software, fully implemented and tested.  The project report consists of a reflection on how the development processes went, and a slideshow presentation of the system developed.
# 5.1 Design Document
The design document task consists of two sub-tasks: planning and documentation.  The planning sub-task involves deciding on the architecture of the system. Sub-systems and the interactions between these subsystems will be defined.  The documentation sub-task involves writing a design document to describe the architecture decided on during the planning sub-task.  The deliverable this task produces is the design document.  The task will conclude before February 10th, 2020.
# 5.2 Test Plan
The test plan task consists of three sub-tasks: planning, documenting, and reviewing.  The planning sub-task will require performing a review of this requirements document and any further agreements made between stakeholders in order to form a preliminary set of tests to demonstrate that each sub-system works and interacts as described either in this document or by the stakeholder. The documentation sub-task involves formally describing the tests decided on in the planning phase. Each test will need to include an addendum describing why that test adequately demonstrates that the object of the test achieves the required functionality. The reviewing sub-task will be the final chance to make formal changes to the sub-system being tested. If a test highlights some fault in the design or implementation of the system, this is the stage where stakeholders will decide whether the test, the requirements, or the implementation needs to be changed before moving on to the next step of the development process. The final portion of the reviewing stage is to compile the results of the tests into a system verification document that demonstrates the validity of the software.
# 5.3 Final Deliverables
The final product from this contract is a piece of data processing software that meets the requirements described in this document. Changes in the requirements may affect the form the final product takes, and as such must be agreed upon and documented as they occur. To demonstrate that the requirements have been met, the final product will be delivered in two parts; the implemented system and the system verification.
# 5.3.1 System Implementation
The system implementation is the piece of software that meets the requirements outlined in this document, developed according to the design document, and tested according to the test plan. The product will be delivered in the form of the source code for the software. Additional instruction on how to run or install the software may be provided upon request if necessary.
# 5.3.2 System Verification
The system verification document contains the results of the testing stage. Once all tests outlined in the test document have been completed and passed, the results are recorded in this document, along with an explanation of why the test shows that the system meets the requirements outlined in this document.
# 5.4 Project Report
The project report is the second deliverable for this project.  This report includes retrospective of the development process and a powerpoint presentation of the completed product.  The retrospective covers any changes or difficulties faced during development, and methods to avoid these happening again.  The primary purpose of this report is to serve as a tool for reflection for the stakeholders to facilitate more efficient cooperation in future projects.

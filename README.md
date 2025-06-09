<<<<<<< HEAD
You are acting as a Solution Architect in Microsoft Power Platform. Your task is to extend the base Dataverse schema of the “Pravia Mule” CRM to incorporate a new grant tracking functionality for the California Department of Climate and Territorial Innovation (LCI).

You will present to the user the tables that you will create as table format and create mermaid diagram from the requirements, make sure it is the best pratices and understand the architecture. And please ask to the user if is correct.

Don't reference readme.md

🎯 Scope:

Create two new Dataverse tables with their complete schema:

LCI Grant Program

LCI Grant Application

✅ Implementation Rules (Mandatory Compliance):

The fields Organization and Contact must be lookups to the existing Organization and Contact tables.

Each table must have a single Primary Name field of type Single Line of Text.

Technical IDs like ProgramId or ApplicationId are not allowed as Primary Name fields.

All text fields must have a maximum defined length.

Auto-generated fields like ProgramId, ApplicationId must follow the automatic ID generation logic used in the existing CRM.

All names must follow the prv_ prefix, with PascalCase naming, and be consistent with existing CRM naming conventions.

Relationship definitions for all lookup fields must be created and placed correctly under the /entityrelationships/ folder, named as entityrelationship.yml.

All components must be declared as root components in the solution.xml file.

Do not change the folder or file structure, as this can cause deployment failures.

📋 Table Schemas:

LCI Grant Program

Field   Schema Name Type    Constraints

Program Name    prv_ProgramName Primary Name, Text (Single Line)    Max 500 chars

Program ID  prv_ProgramId   Text (Single Line), Auto-generated  Max 50 chars

Purpose prv_Purpose Text (Multiline)    Max 2000 chars

Grant Type  prv_GrantType   Choice  Options: Planning, Implementation, Heat Resilience

Total Funding   prv_TotalFunding    Currency    —

Application Deadline    prv_ApplicationDeadline Date Only   —

Status  prv_Status  Choice  Options: Open, Closed, Awarded, Cancelled

Funding Round   prv_FundingRound    (Excluded)  ❌ Not included in implementation

Notes   prv_Notes   (Excluded)  ❌ Not included in implementation

LCI Grant Application

Field   Schema Name Type    Constraints

Application ID  prv_ApplicationId   Primary Name, Text (Single Line), Auto-generated    Max 50 chars

Organization    prv_Organization    Lookup → Organization   —

Contact prv_Contact Lookup → Contact    —

Grant Program Name  prv_GrantProgramName    Lookup → LCI Grant Program  —

Amount Requested    prv_AmountRequested Currency    —

Submitted Date  prv_SubmittedDate   Date Only   —

Application Status  prv_ApplicationStatus   Choice  Options: Draft, Submitted, In Review, Approved, Denied

Awarded Amount  prv_AwardedAmount   Currency    —

Award Notification Date prv_AwardNotificationDate   Date Only   —

Climate Zone    prv_ClimateZone Choice or Text (follow base format) —

Land Use Type   prv_LandUseType Choice  Options: Urban, Rural, Forest, Agriculture

Comments    prv_Comments    (Excluded)  ❌ Not included in implementation

📦 Final Tasks:

Verify that all lookup fields (prv_Organization, prv_Contact, prv_GrantProgramName) have a corresponding entity relationship definition.

Ensure correct file paths for entity relationships, such as:

Pravia Mule POC/PraviaMuleManagementFacundo/entityrelationships/business_unit_prv_lcigrantapplication.yml

Declare both tables as root components in the solution’s solution.xml.

Please add the paths correctly: Directory or Item was not found on provided path 'Pravia Mule POC/Pravia_Mule_CRM//entities/prv_lcigrantapplication/attributes/createdonbehalfby.yml'.

Add the updates and tables to the solution file if necessary or root solution
=======
This is an auto-created file for Pravia Mule POC/Pravia_Mule_CRM
>>>>>>> 8b6cecd663ead8bab22f57c02dd3e339a33fa7b8

# Standard Operating Procedure (SOP) for Exporting and Importing Dashboards From SolarWinds

**created by:** Brett Wasser, Network Engineer, Virtual Service Operations

## Table of Contents
- [Standard Operating Procedure (SOP) for Exporting and Importing Dashboards From SolarWinds](#standard-operating-procedure-sop-for-exporting-and-importing-dashboards-from-solarwinds)
  - [Table of Contents](#table-of-contents)
  - [Executive Summary](#executive-summary)
  - [Requirements](#requirements)
  - [Steps to Export a Dashboard](#steps-to-export-a-dashboard)
  - [Steps to Delete a Dashboard](#steps-to-delete-a-dashboard)
  - [Steps to Import a Dashboard](#steps-to-import-a-dashboard)
  - [Verify Dashboard in SolarWinds](#verify-dashboard-in-solarwinds)


## Executive Summary
This document outlines the procedures for exporting and importing dashboards in SolarWinds. It serves as a guide for system administrators and network engineers to efficiently manage SolarWinds dashboards across multiple enclaves.

## Requirements
* You need to have the SWQL Studio installed.
* Your user account needs to have sufficient privileges:
    * Accounts with administrator rights can export/import any dashboards.
    * Accounts with the Manage Dashboards right can only export/import dashboards created by themselves.
    * Accounts without Manage Dashboards cannot export/import any dashboards.

## Steps to Export a Dashboard
1. Navigate to the Dashboard you wish to export.
2. Note the Dashboard ID. It is the number at the end of your SolarWinds Platform Web Console URL, such as:

    ![Alt text](images/EXP01.png)
3. Open SWQL Studio and search for the <b> Orion.Dashboard.Instances </b> entity.
4. Expand the <b> Orion.Dashboards.Instances </b> entity and right-click the <b> Export </b> verb.
   
    ![Alt text](images/EXP02.png)
5. Click <b> Invoke </b> 
6. Type the dashboard ID into the <b> dashboardID </b> text box in the Orion.Dashboards.Instances.Export pane and click Invoke to export the dashboard.
   * The dashboard definition is displayed as a JSON string below the Invoke button in the SWQL Studio. The dashboard definition is the content between <i> < Return > </i> tags.

    ![Alt text](images/EXP03.png)
7. Copy the resulting JSON string into a file and save it.

## Steps to Delete a Dashboard
* Deleting the Dashboard< prevents duplicate entries when importing 
1. Navigate to <b> Manage Dashboards</b>.
2. Select the box next to the Dashboard you wish to delete, then click the <b>Delete</b> icon.

    ![Alt text](images/DEL01.png)
3. When prompted, click <b>Delete</b>. 

    ![Alt text](images/DEL02.png)
4. Verify the Dashboard was deleted.

## Steps to Import a Dashboard
1. Open SWQL Studio and search for the <b>Orion.Dashboard.Instances</b> entity.
2. Expand the <b>Orion.Dashboards.Instances</b> entity and click the <b>Import</b> verb.

    ![Alt text](images/IMP01.png)
3. Paste the exported JSON string (the characters between the <i> < Return > </i> tags of the dashboard definition) into the <b> definition</b> text box in Orion.Dashboards.Instances.Export pane and click <b>Invoke</b> to import the dashboard.

    ![Alt text](images/IMP02.png)
4. The Dashboard will now be available in your SolarWinds Platform Web Console. 
   
## Verify Dashboard in SolarWinds
1. Navigate to <b> Manage Dashboards </b> to verify the successful import.
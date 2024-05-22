---
layout: post
title: How to add links to Dataverse records in Power Automate
---
Working with Power Automate opens up a lot of possibilities to automate business processes. One of the common requirements is to send emails with links to records in Dataverse. This requirement could include sending an HTML table with links to records in Dataverse. This post will show you how to create links to records in Dataverse and add them to an HTML table in Power Automate.

## Creating links to Dataverse records in Power Automate
Adding links to Dataverse records in Power Automate is a little bit tricky. In Dynamics 365 Workflows we have a `Dynamic URL` of a record as a field while working with workflow UI. In Cloud flow, we simply have to recreate links from scratch. Follow the steps below to create a link:
1. Add Initialize variable action to create a variable of type string. Name it `UriHost`.
2. Add an expression to set the value of the variable. The expression should be like below:
    `uriHost(items('Get_caseby_id')?['@odata.id'])`
3. Add a compose action to create a link. The expression should be like below:
    `concat('<a href="https://',variables('UriHost'),'/main.aspx?etn=incident&pagetype=entityrecord&id=',item()?['incidentid'],'">',item()?['case_title'],'</a>')`
4. The above expression will create a link to the record in Dataverse. You can replace `incident` with the entity name you are working with.

The above steps will create a link to the record in Dataverse. You can use this link in email or any other action where you want to show the link to the record.

## Adding links to HTML table in Power Automate
Adding this link to an HTML table is another story. Simply adding this link to the HTML table will not work as the link will be HTML encoded. You will have to replace the HTML-encoded link with the actual link in the HTML table. You can use the below expression to replace the HTML encoded link with the actual link: 
`replace(replace(replace(body('Create_HTML_table'),'&lt;a href=&quot;','<a href="'),'&quot;&gt;','">'),'&lt;/a&gt;','</a>')`

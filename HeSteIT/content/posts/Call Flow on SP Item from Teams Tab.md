---
author: "Stefan Hefele"
date: 2019-03-08
linktitle: call-custom-flow-SP-TeamsTab
title: Adding a button to call a custom Flow on a SharePoint Online list item or document from a Teams tab
categories: [ "Microsoft 365", "Power Automate"]
tags: ["customizing", "Microsoft Teams", "Flow", "Flow Button", "Teams Tab", "column formatting", "SharePoint", "SharePoint Online"]
weight: 10
---

![](/FlowButton-1.png "SharePoint Library in MS Teams with Flow Button")


This week, I overheard some complaints about Microsoft Teams not having full support for the list and library commands that are available directly within the SharePoint Online site that the list or library lives in. While these features might be coming in the future or are already available if you choose to display the list or library as a "website" tab in Teams, you cannot start a flow on a specific item with this workaround – the flow command is missing from the options:

![Document library in a "document library" tab in Teams](/FlowButton-2.png "SharePoint Library as Website in Teams, missing the Flow Button")
*Document library in a "document library" tab in Teams*

![The same document library shown in the "Files" tab in Teams](/FlowButton-3.png "SharePoint Library in the Files Tab of Teams, also missing Flow Button")
*The same document library shown in the "Files" tab in Teams*

So, how can we start a flow on an item or a document without having to go to the list or library on SharePoint Online? The answer is: column formatting!

But let’s quickly talk through the steps necessary:

### 1. Create a flow with the "for a selected item" trigger

Create the flow you want to run on selected items of the list/library. Use the SharePoint trigger "For a selected item" or "for a selected file" to get the context of the item or file you selected in your Teams tab.

![The "for a selected file" SharePoint Flow Trigger](/FlowButton-4.png "Flow Trigger 'for a selected file'")
*The "for a selected file" SharePoint Flow Trigger*

### 2. Apply column formatting to create a flow button

Use column formatting on a column in the list/library to create a flow button. I created a column "Start Flow" as Single Line of Text, but you can use any column that supports column formatting. You can find a pretty good example here: https://docs.microsoft.com/en-us/sharepoint/dev/declarative-customization/column-formatting#create-a-button-to-launch-a-flow. All you need to do is to adjust the text you want to be displayed on the "button" and replace the ID in the last line of content of the sample with the ID of the flow you just created (use the URL when in editing mode to get it).

To apply the column formatting, click on the column header, hover over column settings, select "format this column" and paste you adjusted JSON-snippet in there.

![Edit column formatting](/FlowButton-5.png "Edit column formatting")

![JSON column formatting](/FlowButton-6.png "JSON column formatting")

### 3. Add the column to the list or library view

Select the view you want to show within your Teams tab later and add you new column to it. Click "Add column", "Show/hide columns" and select your newly created and formatted column. Don’t forget to save!

![Edit view columns](/FlowButton-7.png "Edit view columns")

### 4. Add the list or library view to a new Teams tab

Copy the URL of you list or library view from your browser and switch to Teams. There, add a new tab inside a Channel. Do NOT pick "SharePoint" or "Document library", as this does not show a specific view but default fields. Instead, pick "Website". In the dialogue, paste in your URL and give your tab a name.

![Add library as Website in Teams](/FlowButton-8.png "Add library as Website in Teams")

Voilà, you "Start Flow" column is now visible in Teams! Whenever you want to manually start a flow on your item or document, just click on your button, fill in the required information, and start the flow.

![The document library as a tab in Teams – with Flow button!](/FlowButton-9.png "SharePoint Document Library in Teams with Flow Button")
*The document library as a tab in Teams – with Flow button!*

![The panel is displayed just like in SharePoint Online](/FlowButton-10.png "Flow Start panel shown inside Teams Tab")
*The panel is displayed just like in SharePoint Online*

Have fun!
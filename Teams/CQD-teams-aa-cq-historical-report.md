What are the Requirements? Power BI Desktop You need to have Power BI Desktop installed. You can install it from the Windows Store using this link https://aka.ms/pbidesktopstore

You can use the free version of Power BI Desktop. Minimum compatible version is 2.85.681.0 (September 2020)

Permissions to access the CQD pipeline The account you use to view the AA & CQ Analytics report need to have permissions to access the CQD data pipeline. How to assign these permissions is described here: https://docs.microsoft.com/en-us/microsoftteams/turning-on-and-using-call-quality-dashboard#assign-roles-for-accessing-cqd

Installation The following steps assume you have already installed Power BI Desktop on the computer and that your account has the necessary permissions to access the CQD data pipeline.

Please perform these steps:  Download the template from https://aka.ms/TAPAACQAnalytics and save it to a directory on your computer  Double-click on the template and Power BI Desktop should launch  You will be prompted to select the CQD data pipeline region. Select the region where your tenant is located.

 You can see the region using the Skype for Business Online PS cmdlet (Get-CsTenant).ServiceInstance output. The region will be displayed after the / like in this example microsoftcommunicationsonline/noam-4a-s7 where the region is noam  The report will launch with sample data  To see your own data please click Refresh in the Home tab under Queries in Power BI Desktop

 You will then be prompted to sign in. Select Organization account and click Sign in

 Click Connect and watch the data refresh

Data latency Any AA & CQ analytics data will be available in the CQD data pipeline within 30 minutes.

You will have to refresh the data to see the new analytics data. Customization You are able to customize certain visualization aspects of the reports, i.e. adding or removing fields to be shown in the various visualizations, changing chart type etc.

You cannot add additional data fields other than the ones provided in the report.

Change color schema The following steps assume you have already completed Installation steps.

Please perform these steps: • Select on ribbon View tab

• Select color schema from drop down list

CQD Fields Description

PowerBI data model Dimensions

Measures

PowerBI graph description Auto Attendant

Call Queue

Agent Timeline

Known Issues
Please observe the following Known Issues:  Currently CQ and AA shows Resource accounts Id instead of CQ/AA names. Add explanation (multiple RA accounts (select all RA associated with CQ  Currently we showing on 28 days in dashboard because CQ/AA data is End User Identifiable Information data and is subject to data privacy retention policies

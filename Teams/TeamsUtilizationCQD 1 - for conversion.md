# "How do my users actually use Microsoft Teams, and how much? How do I track this for my organization?" 

This new Teams Utilization reports lets you see how (and how much) your users are using Microsoft Teams. These reports are intended to be a centralized location that both administrators and business leaders can quickly go to for this data.

The Teams Utilization Power BI report consists of two primary reports: [**Call Count Summary**](https://docs.microsoft.com/en-us/MicrosoftTeams/cqd-teams-utilization-report#call-count-summary-report) and [**Audio Minutes Summary**](https://docs.microsoft.com/en-us/MicrosoftTeams/cqd-teams-utilization-report#audio-minutes-summary-report). The [Daily Usage](https://docs.microsoft.com/en-us/MicrosoftTeams/cqd-teams-utilization-report#daily-usage), [Regional Audio Details](https://docs.microsoft.com/en-us/MicrosoftTeams/cqd-teams-utilization-report#regional-audio-details), [Conference Details](#_Conference_Details) and [User List](#_Conference_Details) reports come into play when a user takes advantage of the drill-down reports, noted in the descriptions below.

*\*Note that building and subnet data must be populated to provide regional and network filtering capabilities.*

# Call Count Summary Report

The main page (Call Count Summary) immediately provides the number of audio, video and screen sharing sessions over the last 30 and 90 days as noted in the section title. The data initially displayed is for the organization as a whole and can be filtered using the slicer dropdown options on the left side of the page.

REPLACE GRAPHIC

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image1.png)

To the right of the slicer dropdowns, the number of calls by media type is broken down to an internal/external view over the past thirty days. We can see through the above screenshot that there are more calls happening from outside organizational locations, which makes sense considering the current global environment.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image2.png)(3) To the right of the media type count box, we have the Monthly Call Count by Media Type for the last 90 days. Each column and media type can be hovered over to display the count for a previous month or the current month to date, providing usage trend information. REPLACE GRAPHIC

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image3.png)(4) The middle graph functions as the 90-day graph does, however it provides a daily usage view for the past 30 days and allows a user to right click and drill down into details for a specific day.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image4.png)

On the bottom left section of the page, you'll find a table providing total values for each media type over the past year.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image5.png)![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image6.png)

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image7.png)To the right of the table, a bar chart shows clients with the most use (calls/streams) for the past 30 days.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image8.png)The last set of charts for this page show each media type individually, with a breakdown showing conference and P2P usage. The charts below show that there is significantly higher conference usage as compared to P2P. 

# Audio Minutes Summary Report

On the Audio Minutes usage report, the total minute usage is provided through a few different views.

We have the thirty-day usage summary shown next to the slicers as easy to consume text boxes. The top number shows the thirty-day total, with internal and external breakdowns below that. REPLACE GRAPHIC

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image9.png)

The top right bar graph provides a yearlong view of audio usage. Hover over the month to show the total audio minutes consumed for the month in question.

To show the difference in P2P and conference audio, the bottom left chart takes all audio for the past year and breaks it up between the two types. Should a need arise for internal/external or P2P/Conference breakdowns, utilize the slicers to provide the view necessary.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image10.png)The last chart for the Audio minutes page shows audio minute usage on a global map overlay. This chart will only work if building and subnet data is uploaded to the tenant. The pie chart overlay on the map can be drilled into, subsequently providing regional audio usage. REPLACE GRAPHIC - \#11

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image11.png)

# Drill- through capabilities

As previously noted, users can drill into the daily and regional usage reports.

## Daily Usage

The Daily Usage report allows an administrator to see details for that day and provides access to two additional drill down reports (Conference Details and User List). To get to the Daily Usage report, go to the Call Count Summary page, right click on a day and select the drill-through option. REPLACE GRAPHIC

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image12.png)

The Daily usage report displays the number of Audio, Video and Screen shares for the selected day with the added ability to differentiate between internal and external connectivity. A Conference and Peer to Peer breakdown is to the immediate right of the modality total box. The top right of the report provides a list of conferences with their associated ID and participants for the day. The conference list provides an additional drill down to the Conference Details report as well. REPLACE GRAPHIC

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image13.png)

The bar graph in the center area allows the user to identify peak consumption periods through the course of a day. Users may drill down into the hour represented on the graph which will present the User List report for the hour.

To the right of the bar graph, User Feedback is presented in a visual format. While user sentiment can be subjective, it does provide insight that can be used to identify potential issues.

The bottom table provides a range of metrics for the day. Poor percentages along with failure rates can provide an administrator with potential areas of improvement. Each hour can also be selected individually as shown below.

1.  Click on the column for that day to display metrics for that hour. ![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image14.png)
    
    1.  The table below the chart will display the metrics for that hour. This can be sorted by any column header; however, we would be interested in finding problematic areas.  
        ![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image15.png)
    
    2.  We see that the IND region is experiencing poor video performance in conferences during this time frame. Subsequently, the CQD QER Microsoft reports can be used to narrow down the problematic location as the region and time frame has been identified.

### User List

The User List drill down provides, as one might expect, user specific information for a specific hour selected by the person viewing the report. The User List report is accessible through a drill down in the Hourly Trends graph on the Daily Usage report. Right click on the hour additional information is needed for and select Drill through and User List, as shown below.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image19.png)

The User List report shows internal/external connectivity through the doughnut chart in the top center of the page. We can see that there is a large amount of participation from Outside the corporate network in the below image.

The top right of the graph shows the number of calls made by each user within that hour.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image20.png)

The bottom table provides detailed information for the sessions each user participated in during that hour. The Failure Type column is useful in determining what caused a call to drop. The Capture and Render Device columns are useful in identifying why a call was reported having poor quality.


### Conference Details

The Conference Details report provides additional insight for meetings, from an attendee list, to the media types used during the session.

Right click a conference the participant bar in the conference ID chart on the Daily usage page to drill down into the conference details.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image16.png) ![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image17.png)

We can see the participants in the conference as well as all the pertinent information down to packet loss and jitter to assist with potential troubleshooting efforts in the bottom table.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image18.png)


## Regional Audio Details

The Regional Audio Details drill down specifically shows the audio minute usage for the selected region. Users with access to CQD can see usage trends for both P2P and conference audio within the selected region.

1.  On the Call Count Summary page, drill-through to as specific region through the table.

> ![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image21.png)

2.  Select the row with the region additional information is needed for.

> ![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image22.png)

3.  The data trends show a significant number of minutes being used on the internal network, with conferencing far surpassing P2P use.

![](c:\\Users\\lolaj\\OfficeDocs-SkypeForBusiness-pr\\Teams/media/image23.png)

The regional audio trend can be used to show how users are impacted by external influences in the world. Specifically, right now, we would expect to see the external usage for the EMEA and APAC regions to increase with people being asked to work remotely.

<span id="_Conference_Details" class="anchor"></span>

*Copyright 2020 Microsoft Corporation*

*Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:*

*The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.*

*THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.*

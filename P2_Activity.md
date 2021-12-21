# Solution Guide: Part 2 - Defend Your SOC
Windows Server Logs
Report Analysis for Severity
Did you detect any suspicious changes in severity?

Yes. The percentages changed from:

 High: 6.91%
 Informational: 93.09%
 
 ![image](https://user-images.githubusercontent.com/93474690/146818374-538a02b6-84b8-47c6-af65-7db5aca14e7e.png)

to:

 High: 20.22%
 Informational: 79.78%
 
 ![image](https://user-images.githubusercontent.com/93474690/146818446-d8f508e9-5a22-48d7-8c14-1829c81575dd.png)

This indicates an increase in the high severity cases.

Report Analysis for Failed Activities
Did you detect any suspicious changes in failed activities?

Yes. The percentages changed from:

 success: 97.02%
 failure: 2.98%
 
 ![image](https://user-images.githubusercontent.com/93474690/146818527-c19ef73d-a89d-4f50-bcd8-569de321f898.png)

to:

 success: 98.44%
 failure: 1.56%
 
 ![image](https://user-images.githubusercontent.com/93474690/146818607-0e229827-6e76-4ea3-abc9-6cf513e558d4.png)
 
 This indicates that there is not a major change in the cumulative failure of events.

Alert Analysis for Failed Windows Activity

![image](https://user-images.githubusercontent.com/93474690/146950180-9f10b7c7-c444-4888-98e4-0909af7b5be5.png)

There is some potential suspicious activity for failed activity between 8 a.m. and 9 a.m. on Weds, March 25th.

![image](https://user-images.githubusercontent.com/93474690/146950295-4f22cffd-0a5a-46a5-9162-0700bf185acd.png)

The count of activity is 35 events during this hour, "A privileged service was called, where the user account was deleted, Domain Policies were changed, A user account was created, An attempt was made to reset an accounts password, and A computer account was deleted."
Alert Analysis for Successful Logons

![image](https://user-images.githubusercontent.com/93474690/146950407-774b769b-e63f-4828-b62b-1f8f5f6889e8.png)

There is some potential suspicious activity for failed activity at 11 a.m and 12 p.m. on Weds, March 25th

![image](https://user-images.githubusercontent.com/93474690/146950530-444b0a93-b568-4f95-ad74-019a730d5939.png)

The count of activity is 196 at 11 a.m. and 77 at 12 p.m.

The primary user logging in is user j.

![image](https://user-images.githubusercontent.com/93474690/146950634-16047c02-de4f-4bdb-862a-f983815642cc.png)

Yes, it would have alerted the SOC Analyst of the suspicious logons.
No, it is set appropriately for the hourly settings, it would have also triggered an alert for the activity for the second hour from 12 p.m. to 1 p.m. on the same day.
Alert Analysis for Deleted Accounts
Did you detect a suspicious volume of deleted accounts?

![image](https://user-images.githubusercontent.com/93474690/146950728-46512c59-1775-418e-82dc-3fe5535147bd.png)

There was no suspicious activity of deleted accounts. 

![image](https://user-images.githubusercontent.com/93474690/146950816-d3210903-df75-45ff-ae15-7329fa58de2f.png)

Dashboard Analysis for Time Chart of Signatures
Does anything stand out as suspicious? What signatures stand out?
Yes, the signatures that have suspicious activity are: An attempt was made to reset a users password (39.955%), A user account was locked out (34.003%), and An account was successfully logged on (8.111%).
Before Windows Server Attack Dashboard

![image](https://user-images.githubusercontent.com/93474690/146950899-d98c7e9e-ecfb-466b-89f2-f69dc94606f6.png)

![image](https://user-images.githubusercontent.com/93474690/146950935-77a22509-096e-464c-aafa-9722942ad8df.png)

Dashboad after the Windows Server Attack

![image](https://user-images.githubusercontent.com/93474690/146951025-84d0f736-d2c2-47f1-96c4-63a7ab36a4b8.png)

![image](https://user-images.githubusercontent.com/93474690/146951087-805b68c6-010c-401b-a253-07bc973e5b58.png)

What time did it start and stop for each signature? What is the peak count of the different signatures?

A user account was locked out: Started around 1 a.m. and ended at 3 a.m. on March 25th. The peak count was 896, and the total for the two hours was (805 + 896 = 1701).
An attempt was made to reset a users password: Started around 9 a.m. and ended at 11 a.m. on March 25th. The peak count was 1,258, and the total for the two hours was (1258 + 761 = 2019).
The account was successfully logged on: Started around 11 a.m. and ended at 1 p.m. on March 25th. The peak count was 196, and the total for the two hours was (196 + 77 = 273).

![image](https://user-images.githubusercontent.com/93474690/146951193-42637927-f213-4e9a-9728-46b89414da81.png)

Dashboard Analysis for Users
Does anything stand out as suspicious? Which users stand out?

Yes, the users that have suspicious activity are users A, K, and J.
What time did it begin and stop for each user? What is the peak count of the different user?

User A: Started around 1 a.m. and ended at 3 a.m. on March 25th. Peak count was 984, and the total for the two hours was (799 + 984 = 1783).
User K: Started around 9 a.m. and ended at 11 AM on March 25th. Peak count was 1,256, and the total for the two hours was (1256 + 761 = 2017).
User J: Started around 11 a.m. and ended at 1 p.m. on March 25th. Peak count was 196, and the total for the two hours was (196 + 82 = 278).

![image](https://user-images.githubusercontent.com/93474690/146951313-d760e546-28ea-401c-a626-614694026932.png)

Dashboard Analysis for Signatures with Bar, Graph, Pie Charts
Does anything stand out as suspicious?
No
Do the results match your findings in your time chart for signatures?
All Charts are showing the same information as above for the Signatures.
Dashboard Analysis for Users with Bar, Graph, Pie Charts
Does anything stand out as suspicious?
No
Do the results match your findings in your time chart for users?
All Charts are showing the same information as above for the Users.
Dashboard Analysis for Users with Statistical Chart
What would be the advantage/disadvantage of using this report, compared to the other user panels you created?

There is only one advantage of the stats chart, as it will only give the total count of the users activity or the percentage of the activity. However, the disadvantage of the stats chart compared to a chart will show a cumulative perspective, while a time chart shows the suspicious activity over a more specific, and shorter time frame.
Apache WebServer Logs
Report Analysis for Methods
Did you detect any suspicious changes in HTTP methods? If so, which one?
Yes, there was a suspicious change in the HTTP POST method, which was raised from 1% to 29%or the count jumped from 106 to 1324.

![image](https://user-images.githubusercontent.com/93474690/146951524-bd8b43a4-20db-4b58-9aa9-97bd58adde49.png)

![image](https://user-images.githubusercontent.com/93474690/146951574-55276069-a8a9-484e-920a-b1a67b19b72c.png)

What is that method used for?

POST is used to submit or update information to a web server.
Report Analysis for Referrer Domains
Did you detect any suspicious changes in referrer domains?

There were no major suspicious referrers during the attack. Only minor changes to the first two domains by a couple of percentages.

![image](https://user-images.githubusercontent.com/93474690/146951661-d145d912-e2ea-41a5-9e4f-2b1415619eb6.png)

![image](https://user-images.githubusercontent.com/93474690/146951769-42ecb552-eb3d-4578-a267-63c6f2f59c15.png)

Report Analysis for HTTP Response Codes
Did you detect any suspicious changes in HTTP response codes?

There are several small changes, but the most prominent is the 404 response code, which increased from 2% to 15%. The 200 response code went down from 91% to 83%.

![image](https://user-images.githubusercontent.com/93474690/146951877-3704f796-e4af-4117-a16c-e89a93534fb9.png)

![image](https://user-images.githubusercontent.com/93474690/146951916-c66024b5-bca8-459e-b674-ad03fe8370f4.png)

Alert Analysis for International Activity
Did you detect any suspicious volume of international activity? If so what was the count of the hour it occurred in?

There was activity in Ukraine between 8 p.m. and 9 p.m. on Weds, March 25th, and had a count of 935 events.
Yes, as the threshold was set at 200, so this activity would be triggered as part of the alert.
No, as it’s above the activity set threshold.

![image](https://user-images.githubusercontent.com/93474690/146952005-b36dc8b3-16b5-4a76-8a0e-4f20608522a1.png)

![image](https://user-images.githubusercontent.com/93474690/146952040-e20a48dc-4d82-4d02-b2f5-38ad54f3541a.png)

Alert Analysis for HTTP POST Activity
Did you detect any suspicious volume of HTTP POST activity? If so, what was the count of the hour it occurred in and when did it occur?

There was a spike in POST method activity between 8 p.m. and 9 p.m. on Weds, March 25th, and had a count of 1,296 events.
No, the threshold set is at 15 counts, this would have been triggered.

![image](https://user-images.githubusercontent.com/93474690/146952149-5e74ebfa-c075-4a81-b79b-4ba38a9bb424.png)

Dashboard Analysis for Time Chart of HTTP Methods
Does anything stand out as suspicious?

Yes, there were suspicious activities of the POST and GET method.
What was the method that seems to be used in the attack? What time did it begin and end, and what was the peak count?

The POST method was used, starting at 8 p.m. and ending at 9 p.m. The peak count was 1,296.
**_The GET method was used, starting at 6 p.m. and ending at 7 p.m. The peak count was 729.

![image](https://user-images.githubusercontent.com/93474690/146952363-44bca81e-4693-4dd1-8917-843cb724cc35.png)

Dashboard Analysis for Cluster Map
Does anything stand out as suspicious? What new country, city on the map has a high volume of activity?
Yes, there is suspicious activity in Ukraine.

![image](https://user-images.githubusercontent.com/93474690/146952466-57c1e185-a92b-415d-9cb7-31b2769e7f2c.png)

What is the count of that country, city?
When zoomed in, we can see the cities in Ukraine are:
Kiev: Count of 439
Kharkiv: Count of 433
Lvov: Count of 5

![image](https://user-images.githubusercontent.com/93474690/146952574-9b06a3ae-c2f3-43b1-a6b1-54f3307095bf.png)

Dashboard Analysis for URI Data
Does anything stand out as suspicious? What URI is being hit the most?
Yes, there is suspicious activity against the main VSI logon page: /VSI_Account_logon.php.

![image](https://user-images.githubusercontent.com/93474690/146952657-8c3763d5-0273-4deb-b2c0-82dc44b023bd.png)

Based on the URI being accessed, what could the attacker potentially be doing?
The attacker may be trying to brute force the VSI logon page.
Before Apache WebServer Logs Attack Dashboard

![image](https://user-images.githubusercontent.com/93474690/146952728-19a9226e-38b3-4ba6-8393-ae0a4047bf6f.png)

![image](https://user-images.githubusercontent.com/93474690/146952777-06bcdc77-2f40-4c48-95a4-31aa96be1c4a.png)

![image](https://user-images.githubusercontent.com/93474690/146952816-6a550ba4-d19d-473b-913c-8ef4901457a9.png)

Dashboad after the Apache WebServer Logs Attack

![image](https://user-images.githubusercontent.com/93474690/146952915-5028fbe9-f7a0-45bd-955a-809ac5ab60b5.png)

![image](https://user-images.githubusercontent.com/93474690/146952949-5e57ff19-85f0-4168-9d3d-21b3fd3530c5.png)

![image](https://user-images.githubusercontent.com/93474690/146952991-c93cbad0-fe49-42f1-98d7-d4d75fa38cbc.png)

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

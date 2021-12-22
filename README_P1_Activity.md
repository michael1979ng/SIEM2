# Solution Guide: Part 1 - Master of the SOC
Windows Server Logs
Reports: Design the following reports to assist VSI with quickly identifying specific information.

A report with a table of signatures with associated SignatureID.

source="windows_server_logs.csv" | table signature signature_id | dedup signature

![image](https://user-images.githubusercontent.com/93474690/146960978-17c0c69f-54cc-48ee-a490-637382b14de8.png)

![image](https://user-images.githubusercontent.com/93474690/146961005-3fbc56c3-e4db-495d-b463-ddb5db3b1bfc.png)

A report that provides the count and percent of the severity.

source="windows_server_logs.csv" | top severity

![image](https://user-images.githubusercontent.com/93474690/146961064-87d98d2a-51a9-43f2-9af6-36eaa8addafe.png)

![image](https://user-images.githubusercontent.com/93474690/146961104-2d6e8a7c-d576-4340-8373-192574f20264.png)

A report that provides a comparison between the success and failure of Windows activities.

source="windows_server_logs.csv" | top status

![image](https://user-images.githubusercontent.com/93474690/146966396-4ffcec7b-5efe-489b-9db5-9baa0cb11060.png)

![image](https://user-images.githubusercontent.com/93474690/146966433-ab3ea901-2bc0-4989-a783-e72011bc4f89.png)

Alerts: Design the following alerts to notify VSI of suspicious activity.

Determine an appropriate baseline and threshold for hourly level of failed Windows activity. Create an alert to trigger when the threshold has been reached. The alert should trigger an email to SOC@VSI-company.com.

source="windows_server_logs.csv" status=failure

![image](https://user-images.githubusercontent.com/93474690/146966511-3fe42734-a10c-48be-b921-b0574a8398a2.png)

The average activity per hour is approximately six events. Therefore the threshold is set at 20 to avoid false positives.

To create alert, change the search to one hour and click

Set to run every hour.

Set alert to trigger when count is greater than chosen threshold of (20).

Add action Send email to SOC@VSI-company.com.

![image](https://user-images.githubusercontent.com/93474690/146966584-6bb6b4f5-7517-44ed-a13c-0b621d73daba.png)

Determine a baseline and threshold for hourly count of the signature an account was successfully logged on. Create an alert to trigger when the threshold has been reached. The alert should trigger an email to SOC@VSI-company.com.

source="windows_server_logs.csv" signature="An account was successfully logged on"

![image](https://user-images.githubusercontent.com/93474690/146966745-b04d728d-520b-4f86-b7cb-4d52efce0831.png)

The average activity per hour is approximately 12 events. Therefore the threshold is set at 30.

To create alert, change the search to one hour

Set to run every hour.

Set alert to trigger when count is greater than chosen threshold of (30).

Add action Send email to SOC@VSI-company.com.

![image](https://user-images.githubusercontent.com/93474690/146966840-829b2701-8d2b-4ad0-9cc1-7c03c6c3e07b.png)

Determine a baseline and threshold for hourly count of the signature a user account was deleted. Design the alert based on the corresponding SignatureID. Create an alert to trigger when the threshold has been reached. The alert should trigger an email to SOC@VSI-company.com.

source="windows_server_logs.csv" signature_id=4726

![image](https://user-images.githubusercontent.com/93474690/146966957-fcd3767b-01ed-48b7-ad15-3b968d3d370b.png)

The average activity per hour is approximately 13 events.

The threshold range should be between 30-50.

To create alert, change the search to one hour

Set to run every hour.

Set alert to trigger when count is greater than chosen threshold of (30).

Add action Send email to SOC@VSI-company.com.

![image](https://user-images.githubusercontent.com/93474690/146967053-998f0b4a-9ff9-4913-aab6-d819213ffecb.png)

Visualizations and Dashboards: Design the following visualizations and add them to a dashboard called Windows Server Monitoring:

A line chart that displays the different signature field values over time.

source="windows_server_logs.csv" | timechart span=1h count by signature

![image](https://user-images.githubusercontent.com/93474690/146967153-8efa5a2a-c949-405d-a4a0-4107c306294d.png)

Select Visualizations > Line Chart.

![image](https://user-images.githubusercontent.com/93474690/146967258-23ef9843-7688-41e0-89c7-a3524c11e620.png)

A line chart that displays the different user field values over time.

source="windows_server_logs.csv" | timechart span=1h count by user

![image](https://user-images.githubusercontent.com/93474690/146967345-283f06f1-5d8b-477d-a14b-65e8fd9e13cb.png)

Select Visualizations > Line Chart.

![image](https://user-images.githubusercontent.com/93474690/146967420-32ed6159-b675-4c33-85c2-f0e2a655fdcc.png)
A bar, column, or pie chart that illustrates the count of different signatures.

source="windows_server_logs.csv" | top limit=10 signature

![image](https://user-images.githubusercontent.com/93474690/146967510-2a8e557e-9245-4bb8-a0a1-3e2202a73442.png)

Select Visualizations > Bar/Column/Pie Chart.

source="windows_server_logs.csv" | top limit=10 user 

![image](https://user-images.githubusercontent.com/93474690/147129115-b0d770d8-e599-429d-9593-4ad800cfc941.png)

Select Visualizations > Bar/Column/Pie Chart.

![image](https://user-images.githubusercontent.com/93474690/147129203-4465b42b-f73e-4c01-bfc4-629e8ef3fd9c.png)

A statistical chart that illustrates the count of different users.

source="windows_server_logs.csv" | top limit=10 user 

![image](https://user-images.githubusercontent.com/93474690/147129258-fb26714f-b32d-4fa3-a4d3-f4b056218fc1.png)

One single value visualization of your choice: radial gauge, marker gauge, etc.

![image](https://user-images.githubusercontent.com/93474690/147129345-41d09a60-9e44-4bf2-aa4c-5a74b0048b53.png)

![image](https://user-images.githubusercontent.com/93474690/147129381-443f0a60-2749-474f-be49-8f300796aed1.png)

On your dashboard, add the ability to change the time range for all your visualizations.

![image](https://user-images.githubusercontent.com/93474690/147129437-961c96e7-eabe-4c29-b663-d88f4739a8ec.png)

![image](https://user-images.githubusercontent.com/93474690/147129480-80696df5-2c35-4930-a576-1cb2c6205b1a.png)

Apache Web Server Logs
Reports: Design the following reports to assist VSI with quickly identifying specific information.

A report that shows a table of the different HTTP methods (GET, POST, HEAD, etc).

source="apache_logs.txt" | top method

![image](https://user-images.githubusercontent.com/93474690/147129560-4dd93e11-5689-43c1-a072-0118b72487d3.png)

![image](https://user-images.githubusercontent.com/93474690/147129592-4a397d7a-7874-4b82-aaa0-0defd092ac82.png)

A report that shows the top 10 domains that referred to VSI's website.

source="apache_logs.txt" | top limit=10 referer_domain 

![image](https://user-images.githubusercontent.com/93474690/147129699-ea76bc43-e74b-4f7e-b48d-77553c20b7c6.png)

![image](https://user-images.githubusercontent.com/93474690/147129721-9ec579e0-3b99-467a-a974-ae11e3657b07.png)

A report that shows the count of the HTTP response codes.

source="apache_logs.txt" | top status

![image](https://user-images.githubusercontent.com/93474690/147129781-5f299cc3-4e07-4dcb-bbd8-8f98f1591ef8.png)

![image](https://user-images.githubusercontent.com/93474690/147129826-954d80c0-7b42-49d4-b922-3b02347a665e.png)

Alerts: Design the following alerts:

Determine a baseline and threshold for hourly count of activity from a country other than the United States. Create an alert to trigger when the threshold has been reached. The alert should trigger an email to SOC@VSI-company.com.

source="apache_logs.txt" | iplocation clientip | where Country!="United States"

![image](https://user-images.githubusercontent.com/93474690/147129889-3ad85cda-8cd2-4067-9466-de6bef35fe28.png)

The average activity per hour is approximately 80.

Therefore the threshold is set for 200.

To create an alert, change the search to one hour.

Set to run every hour.

Set alert to trigger when count is greater than chosen threshold of (200).

Add action Send email to SOC@VSI-company.com.

![image](https://user-images.githubusercontent.com/93474690/147129968-7e8f1040-7228-4a0a-94ff-a92e494e5eb4.png)
Determine a baseline and threshold for hourly count of the HTTP POST method. Create an alert to trigger when the threshold has been reached. The alert should trigger an email to SOC@VSI-company.com.

source="apache_logs.txt" method=POST


![image](https://user-images.githubusercontent.com/93474690/147130057-6cf3a17e-ea74-48df-a431-d08f14e65002.png)

The average activity per hour is approximately two.

Therefore the threshold is set for 15.

To create an alert, change the search to one hour.

Set to run every hour.

Set alert to trigger when count is greater than chosen threshold of (15).

Add action Send email to SOC@VSI-company.com.

![image](https://user-images.githubusercontent.com/93474690/147130136-35e0b349-b0e8-41cf-bebf-c17234f4a6a4.png)

Visualizations and Dashboards: Design the following visualization and add them to a dashboard called Apache WebServer Monitoring.

A line chart that displays the different HTTP methods field over time.

source="apache_logs.txt" | timechart span=1h count by method

![image](https://user-images.githubusercontent.com/93474690/147130229-454bc2e0-d2e2-42e1-ae47-ddefdb0c7535.png)

Select Visualizations > Line Chart.

![image](https://user-images.githubusercontent.com/93474690/147130301-e9b5f15d-f74d-4f27-93ed-0cb1cc36ee1f.png)

A geographical map showing the location based on the clientip field.

source="apache_logs.txt" | iplocation clientip | geostats count

![image](https://user-images.githubusercontent.com/93474690/147130364-5a1f204e-0a43-43a9-bf69-fada67ea1708.png)

Select Visualizations > Geostats.

![image](https://user-images.githubusercontent.com/93474690/147130437-95b76c85-cc56-408b-bfc0-932b2f0ac387.png)

A bar, column, or pie chart that displays the count of different URIs.

source="apache_logs.txt" | top limit=10 uri

![image](https://user-images.githubusercontent.com/93474690/147130502-cb0cc7c2-986d-4a0f-b026-cccc04c16f00.png)

Select Visualizations > Bar/Column/Pie Chart

![image](https://user-images.githubusercontent.com/93474690/147130587-b76f16d6-ead5-4568-b9e1-1d13cf32f2d3.png)

A bar, column, or pie chart that displays the counts of the top 10 countries.

source="apache_logs.txt" | iplocation clientip | top limit=10 Country

![image](https://user-images.githubusercontent.com/93474690/147130647-aec4ce62-bd2b-40f4-98a8-006929cf5b7b.png)

A statistical chart that illustrates the count of different user agents.

source="apache_logs.txt" | top limit=10 useragent

![image](https://user-images.githubusercontent.com/93474690/147130838-7462e089-5f3d-41a7-be3a-f92ca731d8a0.png)

![image](https://user-images.githubusercontent.com/93474690/147130871-031de7fc-fa26-407d-a738-0b69cf01915d.png)

One single value visualization of your choice: radial gauge, marker gauge, etc.

![image](https://user-images.githubusercontent.com/93474690/147130947-b6896bb1-3156-486f-99bf-e3a89858e84c.png)

![image](https://user-images.githubusercontent.com/93474690/147130978-23c61fdf-449e-4199-ab92-d8b5e3916fb9.png)

![image](https://user-images.githubusercontent.com/93474690/147131039-58805587-16c2-4844-ab1c-95dd5b89761e.png)

![image](https://user-images.githubusercontent.com/93474690/147131076-75ead5d3-109a-40be-9e18-ffadfb1f74d5.png)

On your dashboard, add the ability to change the time range for all your visualizations.

![image](https://user-images.githubusercontent.com/93474690/147131135-178bdb7c-4a95-4d51-9883-bc2e725d7ed5.png)

![image](https://user-images.githubusercontent.com/93474690/147131159-431548dc-4127-4c3e-952c-f5154f849226.png)

![image](https://user-images.githubusercontent.com/93474690/147131226-7167b965-8f0e-4bec-b018-9cec778ffaa9.png)

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

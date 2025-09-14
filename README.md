# SOC-Lab-Splunk
Threat hunting using Splunk with Apache logs (404 errors, suspicious IPs, alerts, dashboard).

## Project Overview
This lab was based on Splunk Enterprise and involved uploading Apache web server logs, search, alerts, and development of SOC dashboard. It was intended to train on the log analysis, threat hunting, and alerting, which are valuable skills of a Security Operations Center (SOC) analyst.

## Project Execution
**1. Setup Splunk & Add Data**

- Logged into my local Splunk instance (localhost:8000).
  
  <img width="957" height="510" alt="Splunk 1" src="https://github.com/user-attachments/assets/34973241-6a3d-4c03-9ea7-2c12027c5a18" />
- Uploaded the file apachelogs.txt.
- Selected the source type as access_combined so Splunk could understand the log format.
  
  <img width="949" height="461" alt="Splunk2" src="https://github.com/user-attachments/assets/8f6972c5-e313-466f-ac6c-2802615e6526" />
  
   **2. Search & Analyze Logs**
  - I started by searching for 404 errors to see how often they appeared over time.
  **sourcetype=access_combined status=404 | timechart count by host**
- This provided me with a bar/line chart with spikes in 404 errors.
  
  <img width="943" height="510" alt="Splunk3" src="https://github.com/user-attachments/assets/14da8716-3eee-44f0-867c-a985d9b4f767" />
  
- Then I looked for top IPs making requests:
  **sourcetype=access_combined | stats count by clientip | sort -count**
 - This showed which IP addresses were hitting the server most.

   <img width="954" height="511" alt="splunk4" src="https://github.com/user-attachments/assets/0ad02c91-79f0-4c3b-af81-d19fd531131e" />

- Next, I filtered out only suspicious IPs with more than 100 requests: **sourcetype=access_combined | stats count by clientip | where count > 100**

<img width="960" height="537" alt="Splunk8" src="https://github.com/user-attachments/assets/cef8b714-ab07-41c0-8167-daeed2dfe1cc" />


**3. Create an Alert**
- Turned one of the searches into an alert called Excessive 404 Errors by IP.

- Configured it to trigger if the search result went above 10.

- Set it to run on a schedule (every 5 minutes).

  <img width="956" height="513" alt="splunk5" src="https://github.com/user-attachments/assets/5c133bcb-1ead-4488-a0e2-4a320add8b4f" />

  

  <img width="958" height="508" alt="splunk6" src="https://github.com/user-attachments/assets/059cb9ad-078e-4646-958f-b58cd2a77ab9" />

 **4. Investigate a Suspicious IP**
 - Picked an IP (66.249.73.135) and drilled down into its events:
   **sourcetype=access_combined clientip="66.249.73.135"**
 - Splunk displayed all logs for that IP, including timestamps and requests.

   <img width="956" height="511" alt="Splunk7" src="https://github.com/user-attachments/assets/2fd68a47-9964-4a44-893f-9cbeba388eb6" />
   
 **5. Build a SOC Dashboard**
 - Finally, I created a SOC Dashboard – Apache Logs with panels:

    - 404 Errors Over Time (line chart)

    - Top IPs by Request Count (table)

    - Top 404 Generators (table)

<img width="957" height="512" alt="Splunk10" src="https://github.com/user-attachments/assets/cb049f66-a223-436a-8dd5-eb985a327d0c" />

**Skills Shown in this Lab**

- Using Splunk to upload and parse logs

- Writing SPL (Search Processing Language) queries

- Visualizing logs with charts and tables

- Creating scheduled alerts

- Investigating suspicious IPs

- Building a SOC dashboard for monitoring

**Conclusion**
  This Splunk project gave me hands-on practice with log analysis and threat hunting. I learned how to go from raw logs to meaningful insights, set alerts for potential issues, and build a dashboard for monitoring activity.




  









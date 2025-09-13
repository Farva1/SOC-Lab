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
  - To find out what frequency occurred over time, I began by searching 404 errors to understand the frequency of 404.
  **sourcetype=access_combined status=404 | timechart count by host**
- This provided me with a bar/line chart with spikes in 404 errors.
  
  <img width="943" height="510" alt="Splunk3" src="https://github.com/user-attachments/assets/14da8716-3eee-44f0-867c-a985d9b4f767" />
  
- After that I searched best IPs that made requests:
  **sourcetype=access_combined | stats count by clientip | sort -count**
 - This displayed the IP addresses that had the highest hits to the server.

   <img width="954" height="511" alt="splunk4" src="https://github.com/user-attachments/assets/0ad02c91-79f0-4c3b-af81-d19fd531131e" />

- Then I narrowed down to suspicious IPs that had over 100 requests:
    **sourcetype=access_combined | stats count by clientip | where count > 100**

<img width="960" height="537" alt="Splunk8" src="https://github.com/user-attachments/assets/cef8b714-ab07-41c0-8167-daeed2dfe1cc" />







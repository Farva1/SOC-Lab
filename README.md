# SOC-Lab-Splunk
Threat hunting using Splunk with Apache logs (404 errors, suspicious IPs, alerts, dashboard).

## Project Overview
This lab was based on Splunk Enterprise and involved uploading Apache web server logs, search, alerts, and development of SOC dashboard. It was intended to train on the log analysis, threat hunting, and alerting, which are valuable skills of a Security Operations Center (SOC) analyst.

## Steps I Did
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




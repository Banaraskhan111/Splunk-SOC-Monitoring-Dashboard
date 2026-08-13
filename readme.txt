🛡️Splunk Windows Security Operations Center (SOC) Dashboard

An interactive Security Information and Event Management (SIEM) dashboard built in Splunk Enterprise (Dashboard Studio) to monitor, analyze, and visualize Windows Security Event Logs in real-time.

📊 Dashboard Preview
      Splunk-SOC-Monitoring-Dashboard(docs/dashboard_preview.png)

📌 Project Overview

This project demonstrates a Tier-1 SOC Analyst workflow focused on monitoring system logons, user authentication patterns, and security-relevant Windows event activity. By ingesting and analyzing Windows Security Event Logs, this dashboard provides high-level single-value threat KPIs, time-series anomaly detection, and categorical event breakdowns to streamline threat detection and triage.


🎯 Key Metrics & Visualizations
     Total Security Events KPI: Single-value metric tracking overall log ingestion (Monitored 148,222 Total Security Events).
     Authentication Indicators: Real-time visibility into Successful Logins (9,833) and Failed Logins (30) for authentication anomaly tracking.
     Security Events Over Time: Time-series line chart identifying volume peaks and potential spikes in security activity.
     Top 10 Security Event IDs: Horizontal bar chart highlighting high-frequency Windows Event Codes, including:
        5379 (User Account Credentials Read)
        4798 (User Local Group Membership Enumerated)
        4624 (Successful Logon)
        4672 (Special Privileges Assigned)
        5058 / 5061 (Cryptographic Operations)
    Top Logged-in Users & Hosts: Bar and pie chart distribution tracking active identities (SYSTEM, local user accounts) and target host systems (Banaras-Khan).
    Logon Types Analysis: Categorical breakdown of authentication vectors (e.g., Logon_Type 5 for Service Accounts, Type 2 for Interactive Logons).
    Logon Activity Trend: Timechart tracking successful logon frequency across active user accounts over time.

🔍 Key SPL (Search Processing Language) Queries Used

   1. Total Security Events Counter
      index=* EventCode=* | stats count

  2. Successful vs. Failed Logins Count
      index=* EventCode=4624 | stats count
      index=* EventCode=4625 | stats count

 3. Top 10 Security Event IDs Breakdown
      index=* EventCode=* | top limit=10 EventCode

 4. Logon Types Distribution
      index=* EventCode=4624 | stats count by Logon_Type

 5. Logon Activity Trend Over Time
      index=* EventCode=4624 | timechart count by TargetUserName

📁 Repository Structure

Splunk-SOC-Monitoring-Dashboard/
│
├── dashboards/
│   └── soc_monitoring_dashboard.json    # Splunk Dashboard Studio source code (JSON)
├── queries/
│   └── spl_queries.spl                  # List of SPL queries used in the dashboard
├── docs/
│   └── dashboard_preview.png            # High-resolution screenshot of the dashboard
└── README.md                            # Comprehensive project documentation


🚀 How to Import into Splunk

1. Open your Splunk Enterprise instance.
2. Navigate to Dashboards -> Click Create New Dashboard.
3. Select Dashboard Studio as the layout option.
4. In the top toolbar, click on Source Code ({}).
5. Copy the code from dashboards/soc_monitoring_dashboard.json and paste it into the editor.
6. Click Save and view the interactive dashboard!

👤 Author & Contact

   Banaras Khan
   Role: Aspiring Cybersecurity Analyst / Blue Team Specialist
   Education: BS Computer Science, Iqra University
   LinkedIn: www.linkedin.com/in/banaras-khan-8a9300326
   Email: kbanaras6666@gmail.com

<div align="middle">
<img height="200" src="https://i.postimg.cc/g0Jm8rsp/Copy-of-s-Block.png" />
</div>

<div align="left"><h3>Description</h3></div>

This project sets up a Splunk lab environment on Windows to collect, index, and analyze log data for security and operational insights. The lab is designed for learning, testing, and simulating real-world use cases such as:<br>
⦁ Centralized log management<br>
⦁ Security monitoring `DNS, Firewall, Authentication logs, etc.`<br>
⦁ Custom dashboards and alerts<br>
⦁ Basic threat hunting exercises<br>

*The project is lightweight and runs on a Windows machine with at least `8 GB RAM`, making it suitable for students, researchers, and professionals who want hands-on experience with Splunk.*<br>

<div align="left"> <h3>Objectives</h3></div>

⦁ Successfully installed Splunk on Windows<br>
⦁ Collecting and indexing Windows Event Logs & DNS logs<br>
⦁ Ability to create custom dashboards and alerts<br>
⦁ Hands-on experience with **log analysis and security monitoring**<br>

<div align="left"> <h3>Tools & Technologies</h3></div>

| Tool / Technology        | Purpose / Usage                                                                 |
|---------------------------|---------------------------------------------------------------------------------|
| **Splunk Enterprise**     | Core SIEM platform for log collection, indexing, searching, dashboards, and alerts |
| **Windows Event Forwarding (WEF)** | Collects Security, System, and Application logs from Windows host        |
| **PowerShell**            | Automates log generation and system event simulation                             |
| **Custom DNS Log Sources**| Provides DNS query/response data for security analysis and anomaly detection     |
| **Browsers / Network Utilities** | Generate network traffic to create realistic log data for Splunk          |
| **Windows 10/11 (8 GB RAM)** | Host operating system for running Splunk and lab environment                  |
| **Sysmon (Optional)**     | Enhances visibility into process creation, registry changes, and network connections |

<div align="left"> <h3>Lab Archietecture</h3></div>

```bash
+----------------------+
|  Windows Host (8GB+) |
|  Splunk Enterprise   |
| Splunk Web Interface |
+-----------+----------+
            |
+-----------v----------+
|     Data Sources     |
|----------------------|
| - Windows Event Logs |
| - DNS Logs           |
| - Sysmon Logs (opt.) |
| - Custom Scripts     |
+----------+-----------+
           |
+----------v-----------+
|    Splunk Indexer    |
|   (local instance)   |
+----------+-----------+
           |
+----------v-----------+
|  Splunk Search Head  |
|  Dashboards / Alerts |
+----------------------+
```

<div align="left"> <h3>Installation Steps on Windows</h3></div>

1. Download Splunk Enterprise<br>
⦁ Visit Splunk [**Downloads**](https://www.splunk.com/en_us/download/splunk-enterprise.html)<br>
⦁ Choose Splunk Enterprise for Windows `64-bit`<br>

<img width="" height="323" alt="Screenshot 2025-09-02 122417" src="https://github.com/user-attachments/assets/85b2bbfa-3b88-4c71-a1a0-cbc7519344a8" /><br>

2. Install Splunk<br>
⦁ Run the installer as Administrator<br>
⦁ Accept license agreement and follow setup wizard<br>
⦁ Set Splunk Admin credentials *default web port:* `8000`<br>

3. Start Splunk<br>
⦁ Open Splunk Enterprise from Start Menu<br>
⦁ Access Splunk Web at: `http://localhost:8000`<br>

<img width="" height="40" alt="Screenshot 2025-09-02 122612" src="https://github.com/user-attachments/assets/620e0895-baea-4ca0-84de-25b53d61c416" /><br>

<img width="" height="323" alt="Screenshot 2025-09-02 174442" src="https://github.com/user-attachments/assets/53d01ad6-0139-4ee9-91f5-714a05320222" /><br>

*Log in with your **Splunk Admin** credentials*
#
<img width="" height="323" alt="Screenshot 2025-08-31 112102" src="https://github.com/user-attachments/assets/1e9dbb4d-6d6b-40b9-b23f-ef4b92adcf59" /><br>

*Dashboard of Splunk Enterprise*

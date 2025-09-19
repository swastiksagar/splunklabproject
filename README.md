<div align="middle">
<img height="200" src="https://i.postimg.cc/g0Jm8rsp/Copy-of-s-Block.png" />
</div>

<div align="left"><h3>Description</h3></div>

![Splunk](https://img.shields.io/badge/Splunk-000000.svg?style=for-the-badge&logo=Splunk&logoColor=white)<br>
This project sets up a Splunk lab environment on Windows to collect, index, and analyze log data for security and operational insights. The lab is designed for learning, testing, and simulating real-world use cases such as:<br>
⦁ Centralized log management<br>
⦁ Security monitoring `DNS, Firewall, Authentication logs, etc.`<br>
⦁ Custom dashboards and alerts<br>
⦁ Basic threat hunting exercises<br>

*The project is lightweight and runs on a Windows machine with at least `8 GB RAM`, making it suitable for students, researchers, and professionals who want hands-on experience with Splunk.*<br>

<div align="left"> <h3>Objectives</h3></div>

⦁ Successfully installed Splunk on Windows.<br>
⦁ Collecting and indexing Windows Event *Logs & DNS logs*.<br>
⦁ Ability to create custom dashboards and alerts.<br>
⦁ Hands-on experience with **log analysis and security monitoring**.<br>

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
⦁ Visit Splunk [**Downloads**](https://www.splunk.com/en_us/download/splunk-enterprise.html) section<br>
⦁ Choose Splunk Enterprise for Windows `64-bit`<br>

<img width="" height="323" alt="Screenshot 2025-09-02 122417" src="https://github.com/user-attachments/assets/85b2bbfa-3b88-4c71-a1a0-cbc7519344a8" /><br>

2. Install Splunk<br>
⦁ Run the installer as Administrator<br>
⦁ Accept license agreement and follow setup wizard<br>
⦁ Set Splunk Admin credentials *default web port:* `8000`<br>

3. Start Splunk<br>
⦁ Open Splunk Enterprise from Start Menu<br>
⦁ Access Splunk Web at: <br>
```
http://localhost:8000
```

<img width="" height="45" alt="Screenshot 2025-09-02 122612" src="https://github.com/user-attachments/assets/620e0895-baea-4ca0-84de-25b53d61c416" /><br>

<img width="" height="323" alt="Screenshot 2025-09-02 174442" src="https://github.com/user-attachments/assets/53d01ad6-0139-4ee9-91f5-714a05320222" /><br>

4. Log in with your **Splunk Admin** credentials<br>

> [!TIP]
> **The one we set during installation.**

`Username:`
```
swastiksagar
```
`Password:`
```
*************
```
#
<img width="" height="323" alt="Screenshot 2025-08-31 112102" src="https://github.com/user-attachments/assets/1e9dbb4d-6d6b-40b9-b23f-ef4b92adcf59" /><br>

Dashboard of Splunk Enterprise

<div align="left"> <h3>Log's Analysis</h3></div>

⦁ Downloaded `logs` from my personal [***NextDNS***](nextdns.io) profile and want to analyze them in **Splunk,** here's a structured approach to help you ingest, parse, and extract meaningful insights:<br>

> [!NOTE]
> To generate `DNS` and network activity logs for analysis. Surf the internet across a variety of domains for minimum `15–30 minutes` of active browsing recommended to ensure sufficient log volume.


<img width="" height="323" alt="Screenshot 2025-09-04 175123" src="https://github.com/user-attachments/assets/c9369a88-9ee7-4a50-933c-9a1d29e36cb7" /><br>

Log in to your  [***NextDNS***](nextdns.io). and navigate to the appropriate configuration.
#

<img width="" height="323" alt="Screenshot 2025-09-04 175148" src="https://github.com/user-attachments/assets/6c43abaa-a466-40d0-a84c-de9e304ddffc" /><br>

Go to the *Settings* tab. Scroll to the Logs section and Click *Download Logs* button. This will export your DNS logs as a **.csv** file, which includes fields like:
`timestamp,` `domain,` `query_type,` `protocol,` `client_ip (if enabled),`  `status (blocked/allowed),` `reason,` `device_name,` `device_model (if client identification is enabled).`
#

<img width="" height="323" alt="Screenshot 2025-09-04 175207" src="https://github.com/user-attachments/assets/1748304c-1f71-4b2e-a969-0517a749c14b" /><br>

The file will be downloaded to your system - ready for analysis in **Splunk** or any other `tool.`<br>

*You can download and unzip the log file for analysis either from the repositories section or directly from here:* [*nextdns.zip*](https://github.com/swastiksagar/splunklabproject/raw/refs/heads/main/NextDNS/nextdns.zip)

#

<img width="" height="323" alt="Screenshot 2025-09-06 233337" src="https://github.com/user-attachments/assets/725bfbbe-0ec6-41f4-ba0c-672ef508a285" /><br>

Go to `Settings` button. Then click on **Add Data**.

#

<img width="" height="323" alt="Screenshot 2025-09-06 233405" src="https://github.com/user-attachments/assets/c954206e-d6f1-4548-9db0-d4d9e2f4ea48" /><br>

<img width="" height="323" alt="Screenshot 2025-09-06 233448" src="https://github.com/user-attachments/assets/44e85968-7561-416f-bd67-cd15336c3f08" /><br>

After selecting the source and specifying the type of data, Splunk provides three input options: **Upload, Monitor, or Forward.** In this example, we selected Upload and added a `.csv` file. Once the file is successfully uploaded, a green check mark appears on the screen confirming the upload.

#

<img width="" height="323" alt="Screenshot 2025-09-06 233538" src="https://github.com/user-attachments/assets/f72970f1-661e-4003-958e-398173721849" /><br>

Set the source type data.<br>

#

<img width="" height="323" alt="Screenshot 2025-09-06 233611" src="https://github.com/user-attachments/assets/bb846544-9fe5-455e-ab4c-c6e020ae7485" /><br>

Name the *index* file as you want.<br>

#

<img width="" height="323" alt="Screenshot 2025-09-06 233625" src="https://github.com/user-attachments/assets/ca66adae-2d8c-442a-ba1a-f2415e8bc2fd" /><br>

Review the data.<br>

#

<img width="" height="323" alt="Screenshot 2025-09-06 233637" src="https://github.com/user-attachments/assets/0a14a9df-76bb-45a3-a547-5369251029e2" /><br>

<img width="" height="323" alt="Screenshot 2025-09-06 234008" src="https://github.com/user-attachments/assets/d32b541a-4885-4db8-a634-b5f31aac9e7a" /><br>

Confirming **Data Ingestion** in Splunk. The **csv** file `nextdns.io.csv` was uploaded into *Splunk* with the following configuration: `Host: MSI`, `Index: index_nextdns`, `Sourcetype: csv`<br>

⦁ After running the search query:<br>

```console
source="nextdns.io.csv" index="index_nextdns" sourcetype="csv"
```

⦁ Splunk successfully returned **271,757** events, confirming that the data was fully ingested.<br>
⦁ The event timeline *{ green bar chart }* displays activity distribution over time, and sample events show that fields like `host`, `source`, and `sourcetype` were correctly extracted.<br>

#

<img width="" height="323" alt="Screenshot 2025-09-06 235524" src="https://github.com/user-attachments/assets/df77cf19-8812-43e0-b65e-69baa8675692" /><br>

Confirming **Block Reasons** in NextDNS Logs. The event timeline confirms consistent log entries across the time range, proving that *Splunk* correctly parsed and indexed the reasons field from the **csv** file.<br>

⦁ Query executed:<br>

```console
index="index_nextdns" sourcetype="csv" reasons =*
```

⦁ Splunk returned **40,008** events where a `reasons` field was present.<br>
⦁ Example event output shows blocked domains such as:<br>
`w3-reporting.reddit.com, blocked, "blocklist:hblock"` indicating that traffic was blocked due to the *`hblock blocklist.`*<br>

> [!TIP]
> The visualized file of blocked events has been uploaded under **Report** folder of *splunklabproject* repositories.

#

> [!NOTE]
> This step validates that NextDNS block reasons are searchable in Splunk, enabling further analysis like most-blocked domains, top blocklists triggered, and trends over time.

<div align=left"><h3>Installation of Splunk Universal Forwarder</h3>

<img width="" height="323" alt="Screenshot 2025-09-08 114229" src="https://github.com/user-attachments/assets/2ec048b5-b45b-490c-9733-8ad4db00e4c9" /><br>

Go the [***Download***](https://www.splunk.com/en_us/download/universal-forwarder.html) page of *Splunk*.

#

<img width="" height="323" alt="Screenshot 2025-09-08 114246" src="https://github.com/user-attachments/assets/1b9a6a08-2a91-43de-850c-400134277d8e" /><br>

Download the **Splunk Universal Forwarder** for Windows.

#

<img width="" height="323" alt="Screenshot 2025-09-08 114345" src="https://github.com/user-attachments/assets/ab44bf4b-c68b-47f9-8dde-60397ee254ab" /><br>

Click on **.msi** installer and click on the Accept License after that select the *An on-premises Splunk Enterprise instance.*

#

<img width="" height="323" alt="Screenshot 2025-09-08 114408" src="https://github.com/user-attachments/assets/b8501c65-6748-46cf-8c1a-3cccb55b727d" /><br>

Create the `Username` and `Password` for the Forwarder.

#

<img width="" height="323" alt="Screenshot 2025-09-08 115901" src="https://github.com/user-attachments/assets/56c14196-9b40-4605-8d2f-7191de06dee3" /><br>

In the **Deployment Server** either you can leave it blank or use the <ins>Local Host</ins> IP Address for it ending with it's default Port number `8089`.

#

<img width="" height="323" alt="Screenshot 2025-09-08 115922" src="https://github.com/user-attachments/assets/808a3c6c-99ef-4c9f-9287-dc4c5331039e" /><br>

In the **Receiving Indexer** use the <ins>Local Host</ins> IP Address same as *Deployment* server address it's default Port number `9997`.

#

<img width="" height="323" alt="Screenshot 2025-09-08 114514" src="https://github.com/user-attachments/assets/ca009e57-16f7-4280-8ebd-f7f9e9d9e225" /><br>

After doing every mentioned steps above we are ready to Install *Splunk Universal Forwarder.*

#

<img width="" height="323" alt="Screenshot 2025-09-08 120438" src="https://github.com/user-attachments/assets/1bb08bfa-1944-45eb-bc90-f6a2fdfa8c9d" /><br>

Configure Splunk to receive data from forwarders by enabling port **`9997`** under *Settings -> Forwarding and Receiving -> Receive data -> Add new*.

#

<img width="" height="323" alt="Screenshot 2025-09-08 123502" src="https://github.com/user-attachments/assets/f8507a2e-6e86-4149-82e0-efa1e2ad312c" /><br>

Splunk is now successfully listening on port **`9997`** for receiving data from forwarders.

#

<img width="" height="323" alt="Screenshot 2025-09-08 132306" src="https://github.com/user-attachments/assets/f4e41cc1-954d-46be-b5c4-63768145ae33" /><br>

Verified the **Health of Local Splunk Deployment**, all indicators are green and functioning properly.

#

<img width="" height="323" alt="Screenshot 2025-09-08 155911" src="https://github.com/user-attachments/assets/a9b26615-1a0b-4618-8227-deb2246c28a7" /><br>

Restart the *Splunk Enterprise.*

#

<img width="" height="323" alt="Screenshot 2025-09-08 160800" src="https://github.com/user-attachments/assets/51b9a07f-def5-489b-8c98-cc0347bbb75e" /><br>

The forwarder successfully detected the system **Windows MSI** and was assigned to a new server class named *Windows 11*.

<div align="left"><h3>Windows Logs and Event Analysis</h3></div>

<img width="" height="323" alt="Screenshot 2025-09-16 043055" src="https://github.com/user-attachments/assets/8cdd3788-fc23-4d98-8bcb-2e2bb285a5ba" /><br>

Under *Settings -> Add data*.

#

<img width="" height="323" alt="Screenshot 2025-09-16 043322" src="https://github.com/user-attachments/assets/8425959b-87d1-4aa1-b763-6e90577dc715" /><br>

Click on **Monitor** to add data from local computer.

#

<img width="" height="323" alt="Screenshot 2025-09-16 043511" src="https://github.com/user-attachments/assets/607990aa-82dd-46b0-a938-9ca033f5f16b" /><br>

In select source option click on **Local Event Logs** to add Event Logs from local computer. Select the desired *Event Data* you want. I have choosen Application, Security, Setup and System.

#

<img width="" height="323" alt="Screenshot 2025-09-16 043548" src="https://github.com/user-attachments/assets/3e9529e9-0178-4c08-af8e-9e53008b873e" /><br>

<img width="" height="323" alt="Screenshot 2025-09-16 043655" src="https://github.com/user-attachments/assets/bec4793b-3661-4726-9402-29594473c542" /><br>

Clicking on next reviewing the the all the selection correctly. **Submit** and click on **Done** button to proceed further.

#

<img width="" height="323" alt="Screenshot 2025-09-16 043723" src="https://github.com/user-attachments/assets/36162a89-6837-426b-bc7e-e2f391bcd331" /><br>

```console
source="WinEventLog :* " host="MSI"
```
**Splunk** successfully ingested Windows Event Logs from host `MSI`, enabling real-time search and analysis across all log channels.

#

<img width="" height="323" alt="Screenshot 2025-09-16 050346" src="https://github.com/user-attachments/assets/51150671-f67f-4d8b-8993-354e9ca8902b" /><br>

<img width="" height="45" alt="Screenshot 2025-09-16 050439" src="https://github.com/user-attachments/assets/ff4c60ad-0a18-4dc0-b948-fb21ed32b831" /><br>

<img width="" height="323" alt="Screenshot (2)" src="https://github.com/user-attachments/assets/1e0e9415-ac97-4962-bd43-556101157d60" /><br>

<img width="" height="45" alt="Screenshot (2 5)" src="https://github.com/user-attachments/assets/00ffcf3d-4b25-403f-872f-51e55e19f2cd" /><br>

**Splunk** successfully ingested Windows Event Logs and accurately matched system-level events *Event ID 7040*
with native Event Viewer entries, confirming end-to-end log integrity.

#

<img width="" height="323" alt="Screenshot 2025-09-16 045046" src="https://github.com/user-attachments/assets/dbb99f4f-7325-4d40-a27c-c4a5a00d3b0d" /><br>

Enabling visualization and analysis through Pivot, Quick Reports, and Search Commands.<br>

<img width="" height="323" alt="Screenshot 2025-09-16 045101" src="https://github.com/user-attachments/assets/9565eb12-76a6-433f-8ab2-32b1386465f2" /><br>

**Splunk** successfully loaded `89` selected fields from the Windows Event Log data model, allowing focused analysis and efficient visualization across key event attributes.

#

<img width="" height="323" alt="Screenshot 2025-09-16 045314" src="https://github.com/user-attachments/assets/55961074-ae3e-4faa-9227-2447ea5c0099" /><br>

**Splunk** successfully visualized **4,883** system log events from the last `24` hours using a pivot pie chart, highlighting source type distribution with dominant activity from WinEventLog:System. Shortlisting the field type to *source* and *sourcetype*.

#

<img width="" height="323" alt="Screenshot 2025-09-16 045412" src="https://github.com/user-attachments/assets/77b8f046-c7ee-44c8-bb9b-d1856e102f97" /><br>

<img width="" height="323" alt="Screenshot 2025-09-16 045421" src="https://github.com/user-attachments/assets/63adbdc0-ef05-4e6d-a383-8a56b014e6fb" /><br>

<img width="" height="323" alt="Screenshot 2025-09-16 045432" src="https://github.com/user-attachments/assets/398254f9-d795-4537-90c8-46817ad9bce1" /><br>

**Splunk** visualized the distribution of Windows Event Log sourcetypes—showing that `WinEventLog:Security` dominates the dataset, while `System` and `Application` logs make up smaller portions.


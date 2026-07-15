#  Splunk-Enterprise-Setup-and-Data-Ingestion

## Installing Splunk Enterprise Free Trial

### Step 1: Download Splunk Enterprise

1.  Open your browser and go to  [Splunk.com](https://www.splunk.com/).
    
2.  Click on  **Products**  and select  **Free Trials & Downloads**.
<img width="1128" height="653" alt="Screenshot 2026-07-15 103435" src="https://github.com/user-attachments/assets/6af7aac7-b92d-4dbc-86ee-ea12908d67f2" />

3.  You will see two platform options:

    -   **Splunk Cloud**: 5GB/day for 14 days.
    -   **Splunk Enterprise**  (will be using): 500MB/day for 60 days.
    
4.  Under  **Splunk Enterprise**, click  **Get My Free Trial**.
   <img width="1918" height="1026" alt="Screenshot 2026-07-14 215026" src="https://github.com/user-attachments/assets/44bfbadc-7e02-44c5-850b-9eacda57ac5b" />

5. Fill out the registration form.
    
    -   Use your college email ID (or preferred email).
6.  Click  **Create My Account**  and verify your email via the link sent by Splunk.
    

### Step 2: Install Splunk Enterprise

1. After verification, you will receive a download link.
2. Sign in and download Splunk Enterprise for your OS (Windows/Linux/macOS).
3.  Click  **Download Now**  to begin downloading.
    
4.  Once downloaded, start the installation process.
    
5.  Accept the license agreement.
 <img width="774" height="601" alt="image" src="https://github.com/user-attachments/assets/8f9e8d58-d01e-4b72-bca0-6ba1edf1b6a5" />

6. Enter your **username and password**, then proceed with installation.
<img width="576" height="447" alt="Screenshot 2026-07-14 215528" src="https://github.com/user-attachments/assets/5bf155a4-f453-42db-aae3-aba07c500e4e" />

### Step 3: Logging into Splunk Enterprise

[](https://github.com/syedme18/Splunk-Enterprise-Setup-and-Data-Ingestion-Guide#step-3-logging-into-splunk-enterprise)

1.  Open Splunk by visiting  `http://localhost:8000`.
    
2.  Login using your credentials.
<img width="1917" height="1012" alt="Screenshot 2026-07-14 220345" src="https://github.com/user-attachments/assets/d9bc72b7-2dfa-44b7-a3df-93ecc82a4be6" />

3. You will now see the **Splunk Dashboard**.
<img width="1918" height="1025" alt="Screenshot 2026-07-14 220521" src="https://github.com/user-attachments/assets/c39ce9d9-6a41-4105-bbd7-c4a83a4b738b" />

## Ingesting Data into Splunk

### Method 1: Uploading a ZIP File
(Note: You can upload various file types including CSV, ZIP, LOG, JSON, XML, TXT, and TSV files up to 500 MB)

1. Go to **Settings → Add Data**.
 <img width="1917" height="1025" alt="Screenshot 2026-07-14 224529" src="https://github.com/user-attachments/assets/2f78b406-d13d-4b6a-adfa-620c248662fc" />

2. Click on **Upload**.
<img width="1918" height="1020" alt="Screenshot 2026-07-14 224559" src="https://github.com/user-attachments/assets/0660971b-cf96-49e4-9307-9043fe7a3778" />

3.   Select your  **ZIP file**  and upload.
<img width="1918" height="1022" alt="Screenshot 2026-07-14 225338" src="https://github.com/user-attachments/assets/3ad08b02-0ae8-4e64-8f07-4f00ed2c85e7" />

4.  Click  **Next**, and Splunk will show a preview of the data.

5. Click  **Next**, then configure the index:
<img width="1236" height="492" alt="Screenshot 2026-07-14 225830" src="https://github.com/user-attachments/assets/d5391e30-f8aa-4fbb-b7b9-ba283f13691c" />

   -   Create a **new index** (e.g., `tutioraldata` for Windows Event Logs).
   
   -   Leave the event type as  **Event**.
   
   -   Click  **Save**.
    <img width="1002" height="730" alt="Screenshot 2026-07-14 230016" src="https://github.com/user-attachments/assets/522e1b55-49a1-457e-b645-a356068fa6b7" />

6. Click **Review and Submit** to complete data ingestion.
<img width="1912" height="717" alt="Screenshot 2026-07-14 230115" src="https://github.com/user-attachments/assets/002f58ea-dc12-4fa0-acc7-ce3bb4284632" />

### Searching the Ingested Data


1.  Go to the  **Dashboard**  and enter the search query:
```
index="tutorialdata"
```
<img width="1798" height="818" alt="Screenshot 2026-07-14 230751" src="https://github.com/user-attachments/assets/61dfd556-f07c-4252-81bb-66791afababa" />

2. Click **Search** to display results

3. Filter data using fields like:
   -   **Event ID**
   - **Date, Month, Minute** (from the left panel)
<img width="343" height="781" alt="Screenshot 2026-07-14 231031" src="https://github.com/user-attachments/assets/edbb8879-8e62-4139-b354-c75d59e8358e" />

4. Use the **time filter** (top-right) to view logs in **Real-time, Last 24 hours, All time**, etc.
<img width="810" height="572" alt="Screenshot 2026-07-14 231226" src="https://github.com/user-attachments/assets/5b26b1a6-c080-46a1-aa8f-76504e77b1f7" />

5.   Go to the **Search & Reporting** app and enter the search query:
```
index="tutorialdata" | stats count by source
```
<img width="1806" height="791" alt="Screenshot 2026-07-14 232432" src="https://github.com/user-attachments/assets/537e66bd-d44d-4bde-9fed-5569b2e625d0" />

  -    Click **Search** to display results
   
  6. To find top client IPs, use the search and  Switch to **Visualization** tab to see results as a **Column Chart**
  ```
  index="tutorialdata" | top limit=10 clientip
  ```
  <img width="1775" height="677" alt="Screenshot 2026-07-14 233136" src="https://github.com/user-attachments/assets/04bb8f91-2656-490e-9d4d-22d806ebc46d" />

  ### Method 2: Ingesting Data Using Universal Forwarder

The  **Universal Forwarder**  is a lightweight Splunk agent that collects and sends logs from remote machines to the Splunk indexer.

#### Step 1: Download Splunk Universal Forwarder
   -   Download it from  [Splunk Forwarder]

#### Step 2: Configure Receiving in Splunk Enterprise

1.  In  **Splunk Enterprise**, go to  **Search**.
<img width="1918" height="1020" alt="Screenshot 2026-07-14 233447" src="https://github.com/user-attachments/assets/ba3fb319-aaf4-4b3f-981e-1da34e6c3b57" />

2.  Search  **Forwarding and Receiving**.
<img width="1918" height="1011" alt="Screenshot 2026-07-14 235101" src="https://github.com/user-attachments/assets/0f7cf39c-c35f-4b36-ba5b-fd66f886551f" />

3. Under **Receiving Data**, click **Configure Receiving**.
<img width="1908" height="833" alt="Screenshot 2026-07-14 235129" src="https://github.com/user-attachments/assets/627765e8-8e33-4cc8-9fcc-77cc198d98cd" />

4.  Click  **New Receiving Port**  and enter  `9997`.
<img width="1907" height="685" alt="Screenshot 2026-07-14 235152" src="https://github.com/user-attachments/assets/14329848-ed2d-4e5b-88af-a98f397d181f" />

5. Configure the **Receiving port** to `9997` and ensure it is enabled.
<img width="1913" height="466" alt="Screenshot 2026-07-14 235805" src="https://github.com/user-attachments/assets/98c45546-3b45-40d0-a1bd-3fa9cf77c2ff" />

#### Step 3: Install and Configure the Forwarder on Windows

1.  Run the Universal Forwarder installer and select  **Customize**.

2.  Choose  **Local System**, then click  **Next**.
    <img width="581" height="452" alt="Screenshot 2026-07-14 234021" src="https://github.com/user-attachments/assets/1b01b82e-a164-4530-92cd-a8e100065548" />

3.  Select the events you want to ingest.
<img width="578" height="453" alt="Screenshot 2026-07-14 234213" src="https://github.com/user-attachments/assets/e1e18364-7209-4078-9d47-39ec1bd7e363" />

4.  Enter your  **username and password**, then click  **Next**.
    
5.  Enter the  **Splunk host IP**  and the  **Receiving Port (`9997`)**.
<img width="577" height="452" alt="Screenshot 2026-07-14 234325" src="https://github.com/user-attachments/assets/b7631ff2-a819-41cc-a89b-0d7e3c1b8177" />

6.  Click  **Install**.

### Step 4: Verify Data in Splunk Enterprise
1.  Go to **Settings** → **Forwarding and receiving**.
    
2.  Verify the receiving port is set to `9997` and enabled.
    
3.  Check if the forwarder is sending data:
    
    -   Go to **Search & Reporting**
        
    -   Run this search:
  ```
   index=*
```
4.  Check if logs from the forwarder are appearing in the search results.

## ### Conclusion


This guide covered the complete setup of Splunk Enterprise, including:

-   Installing Splunk Enterprise Free Trial
-   Ingesting data via CSV/File Upload
-   Searching and analyzing ingested data
-   Setting up Universal Forwarder for remote log collection
-   Configuring forwarding and receiving between Splunk instances
    

Now you can explore Splunk for searching, monitoring, and analyzing data efficiently!
  

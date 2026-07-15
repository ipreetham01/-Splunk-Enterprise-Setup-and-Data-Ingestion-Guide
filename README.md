#  Splunk-Enterprise-Setup-and-Data-Ingestion

## Installing Splunk Enterprise Free Trial

### Step 1: Download Splunk Enterprise

1.  Open your browser and go to  [Splunk.com](https://www.splunk.com/).
    
2.  Click on  **Products**  and select  **Free Trials & Downloads**.

3.  You will see two platform options:

    -   **Splunk Cloud**: 5GB/day for 14 days.
    -   **Splunk Enterprise**  (will be using): 500MB/day for 60 days.
    
4.  Under  **Splunk Enterprise**, click  **Get My Free Trial**. 
5. Fill out the registration form.
    
    -   Use your college email ID (or preferred email).
2.  Click  **Create My Account**  and verify your email via the link sent by Splunk.
    

### Step 2: Install Splunk Enterprise

1. After verification, you will receive a download link.
2. Sign in and download Splunk Enterprise for your OS (Windows/Linux/macOS).
3.  Click  **Download Now**  to begin downloading.
    
4.  Once downloaded, start the installation process.
    
5.  Accept the license agreement.
6. Enter your **username and password**, then proceed with installation.

### Step 3: Logging into Splunk Enterprise

[](https://github.com/syedme18/Splunk-Enterprise-Setup-and-Data-Ingestion-Guide#step-3-logging-into-splunk-enterprise)

1.  Open Splunk by visiting  `http://localhost:8000`.
    
2.  Login using your credentials.

3. You will now see the **Splunk Dashboard**.

## Ingesting Data into Splunk

### Method 1: Uploading a ZIP File
(Note: You can upload various file types including CSV, ZIP, LOG, JSON, XML, TXT, and TSV files up to 500 MB)

1. Go to **Settings → Add Data**.
 
2. Click on **Upload**.

3.   Select your  **ZIP file**  and upload.

4.  Click  **Next**, and Splunk will show a preview of the data.

5. Click  **Next**, then configure the index:

   -   Create a **new index** (e.g., `apps` for Windows Event Logs).
   
   -   Leave the event type as  **Event**.
   
   -   Click  **Save**.
    
6. Click **Review and Submit** to complete data ingestion.

### Searching the Ingested Data

[](https://github.com/syedme18/Splunk-Enterprise-Setup-and-Data-Ingestion-Guide#searching-the-ingested-data)

1.  Go to the  **Dashboard**  and enter the search query:
```
index="tutorialdata"
```
2. Click **Search** to display results

3. Filter data using fields like:
   -   **Event ID**
   - **Date, Month, Minute** (from the left panel)

4. Use the **time filter** (top-right) to view logs in **Real-time, Last 24 hours, All time**, etc.

5.   Go to the **Search & Reporting** app and enter the search query:
```
index="tutorialdata" | stats count by source
```
  -    Click **Search** to display results
   
  6. To find top client IPs, use the search and  Switch to **Visualization** tab to see results as a **Column Chart**
  ```
  index="tutorialdata" | top limit=10 clientip
  ```
  
  ### Method 2: Ingesting Data Using Universal Forwarder

The  **Universal Forwarder**  is a lightweight Splunk agent that collects and sends logs from remote machines to the Splunk indexer.

#### Step 1: Download Splunk Universal Forwarder
   -   Download it from  [Splunk Forwarder]

#### Step 2: Configure Receiving in Splunk Enterprise

1.  In  **Splunk Enterprise**, go to  **Search**.
    
2.  Search  **Forwarding and Receiving**.

3. Under **Receiving Data**, click **Configure Receiving**.

4.  Click  **New Receiving Port**  and enter  `9997`.

6. Configure the **Receiving port** to `9997` and ensure it is enabled.

#### Step 3: Install and Configure the Forwarder on Windows

1.  Run the Universal Forwarder installer and select  **Customize**.

2.  Choose  **Local System**, then click  **Next**.
    
3.  Select the events you want to ingest.

4.  Enter your  **username and password**, then click  **Next**.
    
5.  Enter the  **Splunk host IP**  and the  **Receiving Port (`9997`)**.

1.  Click  **Install**.

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
  

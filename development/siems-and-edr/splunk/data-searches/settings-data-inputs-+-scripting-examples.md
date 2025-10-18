# (Settings) Data Inputs + Scripting Examples



<figure><img src="../../../../.gitbook/assets/image (421).png" alt=""><figcaption></figcaption></figure>

In the Splunk web-app you access this by going to the settings menu in the top right corner and selecting Data Inputs it will give you the image above

### Servers

#### TCP: This will open the port you specify on the Splunk server and listen for connections

**UDP**: **This will open the port you specify on the Splunk server and listen for connections**&#x20;

On windows you can check if Splunk is listening to selected port by (also works for UDP):

```
netstat -an | Select-String -Pattern ':1234\b' | ForEach-Object { $_.Line 
```

#### ========================================================================

### Scripts&#x20;

used to programmatically gather or generate data that is ingested into Splunk for indexing and analysis. These scripts can be custom scripts written in languages like Python, Bash, or PowerShell

Location of scripts: _**Splunk\bin\scripts**_&#x20;



**Script Creation**:

* Write a script that collects or generates the data. The script outputs the data to standard output (stdout).
* The script can be in any language supported by the operating system (e.g., Python, Bash, etc.).

**Configuration in Splunk**:

* Define the script as a data input in the Splunk platform.
* This is done via Splunk Web or by editing configuration files (e.g., `inputs.conf`).

```
[script://.\bin\Get-APIData.ps1]
interval = 60
sourcetype = api_data
index = main
disabled = 0
```

* **`script://`** specifies the script to run.
* **`interval`** defines how often (in seconds) the script should run.
* **`index`** determines where the data is stored in Splunk.
* **`sourcetype`** assigns a sourcetype to the data for parsing.

**Execution**:

* Splunk executes the script on a defined schedule or continuously, depending on the configuration.
* The script’s output is sent to Splunk’s indexing pipeline.

**Indexing and Analysis**:

* The data collected by the script is indexed in Splunk, making it searchable and analyzable using Splunk’s Search Processing Language (SPL)

```
index=main sourcetype=api_data
```

### Scripting Example

```
# API Endpoint
$apiUrl = "https://api.example.com/data"

# Headers (if needed for authentication)
$headers = @{
    "Authorization" = "Bearer YOUR_API_TOKEN"
    "Content-Type"  = "application/json"
}

# Fetch data from the API
try {
    $response = Invoke-RestMethod -Uri $apiUrl -Headers $headers -Method Get
    $jsonData = $response | ConvertTo-Json -Depth 10
    # Output data to stdout for Splunk
    Write-Output $jsonData
} catch {
    # Handle errors and output to stderr (optional for troubleshooting)
    Write-Error "Failed to retrieve data: $_"
}

```

#### **Tips for Handling API Data in Splunk**

1. **Data Format**:
   * Use JSON for structured data as Splunk parses it automatically.
   * You can customize parsing by creating a custom sourcetype with field extractions.
2. **Error Handling**:
   * Ensure your script handles API errors gracefully and logs useful error messages.
3. **Scheduling**:
   * Adjust the `interval` in `inputs.conf` to avoid overloading the API or Splunk.
4. **Authentication**:
   * Store sensitive data like tokens securely. Consider using environment variables or secure credential storage.
5. **Debugging**:
   * Test the script locally with real-time monitoring to ensure it runs correctly before integrating it into Splunk.

# Errors in shared files servers / NAS

To find what user has a file open preventing another user from opening a needed file. Here are a few ways to check:

* Someone has a file inside open (Excel, PDF, etc.)
* Antivirus scanning it
* Backup software
* Indexing service
* Your own File Explorer preview pane

### ✅ **Method 1 — From the NAS (Best way)**

If your NAS is Windows-based or joined to AD:

#### On the NAS server:

1. Open **Computer Management**
2. Go to:\
   **System Tools → Shared Folders → Open Files**
3.  Look for:

    ```
    Wright, Kiara - Centerpoint Bill
    ```
4. You’ll see:
   * Username
   * Computer name
   * Open mode (Read/Write)

👉 You can right-click → **Close Open File** (be careful, it can interrupt users)

### ✅ **Method 2 — Using PowerShell (from your machine)**

If you have admin rights on the NAS:

```
Get-SmbOpenFile -CimSession NASNAME | 
Where-Object {$_.Path -like "*Centerpoint Bill*"} |
Select-Object ClientUserName, ClientComputerName, Path
```

👉 Replace `NASNAME` with your server name

### ✅ **Method 3 — Using Command Prompt**

```
openfiles /query /s NASNAME /v
```

⚠️ Note:

* Requires **admin rights**
*   May need this enabled on the NAS:

    ```
    openfiles /local on
    ```

### ✅ **Method 4 — Check Active Sessions**

Sometimes the folder isn’t “open,” but a user session is holding it:

In **Computer Management → Shared Folders → Sessions**

You’ll see:

* Who is connected
* From what computer

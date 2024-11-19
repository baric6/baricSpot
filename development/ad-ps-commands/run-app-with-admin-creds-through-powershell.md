# Run app with Admin creds through powershell

The below Powershell script that takes a string and encrypts it then saves it to a file

```
# SavePassword.ps1
# Replace "AdminPassword" with your actual password
$password = "AdminPassword" | ConvertTo-SecureString -AsPlainText -Force

# Save the encrypted password to a file
$password | ConvertFrom-SecureString | Out-File "C:\Path\To\EncryptedPassword.txt"

Write-Host "Password encrypted and saved to C:\Path\To\EncryptedPassword.txt"
```



The next script is takes the Username and encrypted password  calls the program.exe and runs it with admin privileges&#x20;

```
# RunApp.ps1
# Admin username
$adminUser = "AdminUsername"  # Replace with your admin username

# Read the encrypted password from the file
$securePassword = Get-Content "C:\Path\To\EncryptedPassword.txt" | ConvertTo-SecureString

# Create a credential object
$credential = New-Object System.Management.Automation.PSCredential($adminUser, $securePassword)

# Path to the application
$appPath = "C:\Path\To\YourApp.exe"  # Replace with the application's path

# Run the application as admin
Start-Process -FilePath $appPath -Credential $credential -ArgumentList @()

Write-Host "Application started successfully!"
```

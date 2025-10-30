# GPO and Enable-BitLocker Commands

{% embed url="https://www.pdq.com/powershell/enable-bitlocker/" %}

#### Create the GPO :

Dont worry about the powershell in this link just how to create a GPO

{% embed url="https://www.techhelpfornonprofits.org/2024/12/07/enable-bitlocker-automatically-using-group-policy-object/" %}

#### Create power-shell:

```
# Check if BitLocker is already enabled
$checkBitLocker = Get-BitLockerVolume -MountPoint "C"
if ($checkBitLocker.ProtectionStatus -eq "On") {
    Write-Output "⚠️ BitLocker is already enabled on C:. Exiting script."
    Exit
}

Start-Sleep -Seconds 8

# Enable BitLocker without creating a new key
Enable-BitLocker -MountPoint C: -SkipHardwareTest -RecoveryPasswordProtector

Write-Output "✅ BitLocker has been enabled. GPO will handle key backup to AD."
```

#### How it works

1. Add device to the group you linked the GPO since this is a computer policy not a user policy
2. Make sure the device sees the GPO, may need to restart the machine if filtered&#x20;

```
gpresult /r
```

3. run script (just enables bit-locker, the GPO can not)
   1. Check if bit-locker is already installed
   2. sleeps for 8 sec&#x20;
   3. Enable bit-locker without creating a new key, the GPO&#x20;
4. When bit-locker is turned on it looks for the device in active directory and sends the key to the device object to save.&#x20;

#### To find the key

1. Log in to your Domain Controller and click on Users and Computers
2. Search for Computers then the name&#x20;
3. You will see a bitlocker tab, if not go to the main user and computers page and click on view then advanced view

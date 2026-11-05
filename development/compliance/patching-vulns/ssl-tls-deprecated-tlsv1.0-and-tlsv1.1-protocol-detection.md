# SSL/TLS: Deprecated TLSv1.0 and TLSv1.1 Protocol Detection

#### \[Medium] TLS 1.0 / 1.1 enabled: fix this one

**Windows hosts (IIS, RDP, PDQ, etc.)**

* **GUI:** Download **IIS Crypto** (Nartac). Click **Best Practices**, uncheck TLS 1.0 and 1.1 under both _Server_ and _Client_ protocols, click **Apply**, then reboot.
* **Registry, or push with PDQ:**

```powershell
 foreach ($v in 'TLS 1.0','TLS 1.1') { foreach ($r in 'Server','Client') {
    $k = "HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\$v\$r"
    New-Item $k -Force | Out-Null
    Set-ItemProperty $k Enabled 0 -Type DWord
    Set-ItemProperty $k DisabledByDefault 1 -Type DWord }}
  # Make .NET apps use TLS 1.2
  'HKLM:\SOFTWARE\Microsoft\.NETFramework\v4.0.30319','HKLM:\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319' |
    % { Set-ItemProperty $_ SchUseStrongCrypto 1 -Type DWord; Set-ItemProperty $_ SystemDefaultTlsVersions 1 -Type DWord }
```

**Verify the fix:**&#x20;

```powershell
nmap --script ssl-enum-ciphers -p 443,3389 <host>
```

Device is patched results

<figure><img src="../../../.gitbook/assets/image (484).png" alt=""><figcaption></figcaption></figure>

Device is not patched results&#x20;

<figure><img src="../../../.gitbook/assets/image (483).png" alt=""><figcaption></figcaption></figure>


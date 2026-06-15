# Bitlocker attacks

A list of public attacks on BitLocker. Any public attack with the potential to attack BitLocker but where the exact method is still not public (like baton drop) is out of scope.

Most of the attacks are for where the VMK is sealed by TPM only, which is the default setting, and is what automatic BitLocker uses alongside recovery key escrow to a Microsoft account.

By default, starting from Windows 8, Secure Boot integrity validation is used if Secure Boot is enabled.

If you must seal the VMK by TPM only, the most secure configuration for this is to use legacy integrity validation with PCRs 0, 2, 4, 7, 11 (and also to keep your system fully updated). Please note that this will only protect against software attacks.

Download&#x20;

{% embed url="https://github.com/Wack0/bitlocker-attacks" %}

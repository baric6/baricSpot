# Wireshark rdp traffic scanning

Many applications, including browsers, support the SSLKEYFILEFILE environment variable with a path to a text file where TLS pre-master secrets are dumped. This format is supported by Wireshark and does not require exporting server private keys.

To configure Wireshark to use a specific TLS key log file, open the Preferences dialog (Edit -> Preferences), navigate to the TLS section under Protocols, and then change the (Pre)-Master-Secret log filename field:

<figure><img src="../../.gitbook/assets/image (168).png" alt=""><figcaption></figcaption></figure>

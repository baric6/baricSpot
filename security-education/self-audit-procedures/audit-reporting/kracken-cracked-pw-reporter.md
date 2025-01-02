# Kracken cracked PW reporter

our assessments, it's common to get our hands on some hashed passwords, often related to an Active Directory (AD) domain. A password dump is usually obtained after compromising a domain controller and it contains the password hash of every account configured in the domain. In the Windows AD case, this hash is usually an NTLM hash, which doesn't offer strong protection against brute force and dictionary attacks.

At this stage, we usually start a password cracking attack on the dumped hashes to assess the strength of the passwords used to access the domain's accounts. And guess what? Users' passwords are usually weak!

This step allows us to get an overview of both the effectiveness of the password policies implemented in the domain and the awareness on the importance of strong passwords. We believe that this information is crucial to assess the security of an organization and, if presented correctly, it can have a significant impact on improving its security posture. However, the critical point is to present the results of this analysis in the best way possible.

<figure><img src="../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

{% embed url="https://github.com/hnsecurity/kraken" %}

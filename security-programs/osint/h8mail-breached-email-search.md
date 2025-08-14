# H8mail - breached email search

**h8mail** is an email OSINT and breach hunting tool using different breach and reconnaissance services, or local breaches such as Troy Hunt's "Collection1" and the infamous "Breach Compilation" torrent.

#### Github

{% embed url="https://github.com/khast3x/h8mail?tab=readme-ov-file" %}

#### Wiki

{% embed url="https://github.com/khast3x/h8mail/wiki?ref=readmebutton" %}

***

**APIs**

| Service                                                                | Functions                                                                           | Status |
| ---------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ------ |
| [HaveIBeenPwned(v3)](https://haveibeenpwned.com/)                      | Number of email breaches                                                            | ✅ 🔑   |
| [HaveIBeenPwned Pastes(v3)](https://haveibeenpwned.com/Pastes)         | URLs of text files mentioning targets                                               | ✅ 🔑   |
| [Hunter.io](https://hunter.io/) - Public                               | Number of related emails                                                            | ✅      |
| [Hunter.io](https://hunter.io/) - Service (free tier)                  | Cleartext related emails, Chasing                                                   | ✅ 🔑   |
| [Snusbase](https://api.snusbase.com/admin/purchase) - Service          | Cleartext passwords, hashs and salts, usernames, IPs - Fast ⚡                       | ✅ 🔑   |
| [Leak-Lookup](https://leak-lookup.com/) - Public                       | Number of search-able breach results                                                | ✅ (🔑) |
| [Leak-Lookup](https://leak-lookup.com/) - Service                      | Cleartext passwords, hashs and salts, usernames, IPs, domain                        | ✅ 🔑   |
| [Emailrep.io](https://emailrep.io/) - Service (free)                   | Last seen in breaches, social media profiles                                        | ✅ 🔑   |
| [scylla.so](https://scylla.so/) - Service (free)                       | Cleartext passwords, hashs and salts, usernames, IPs, domain                        | 🚧     |
| [Dehashed.com](https://dehashed.com/) - Service                        | Cleartext passwords, hashs and salts, usernames, IPs, domain                        | ✅ 🔑   |
| [IntelX.io](https://intelx.io/signup) - Service (free trial)           | Cleartext passwords, hashs and salts, usernames, IPs, domain, Bitcoin Wallets, IBAN | ✅ 🔑   |
| 🆕 [Breachdirectory.org](https://breachdirectory.org) - Service (free) | Cleartext passwords, hashs and salts, usernames, domain                             | 🚧 🔑  |

_🔑 - API key required_




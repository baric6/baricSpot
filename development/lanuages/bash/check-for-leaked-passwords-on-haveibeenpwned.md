# Check for Leaked Passwords on HaveIBeenPwned

```bash
password="yourpassword"; hash=$(echo -n "$password" | sha1sum | awk '{print $1}'); prefix=${hash:0:5}; suffix=${hash:5}; curl -s "https://api.pwnedpasswords.com/range/$prefix" | grep -i "$suffix"
```

Summary of SHA-1 Password Hash Check with Pwned Passwords API Purpose

```
Check if a password has been compromised by querying the Have I Been Pwned (HIBP) API using SHA-1 hashing.
```

Key Steps

```
Define Password and Hash:
    password="yourpassword": Sets the password to check.
    hash=$(echo -n "$password" | sha1sum | awk '{print $1}'): Creates a SHA-1 hash of the password.

Extract Prefix and Suffix:
    prefix=${hash:0:5}: Takes the first 5 characters of the SHA-1 hash (prefix).
    suffix=${hash:5}: Takes the rest of the hash (suffix).

Query the Pwned Passwords API:
    curl -s "https://api.pwnedpasswords.com/range/$prefix": Retrieves hashed password data matching the prefix.
    grep -i "$suffix": Checks if the suffix appears in the retrieved data, indicating if the password has been pwned.
```

Outcome

```
If the suffix is found, the password has likely been compromised.
If not found, the password has not been detected in known data breaches.
```

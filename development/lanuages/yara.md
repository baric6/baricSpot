# YARA

```bash
rule yara_rule
{
    meta:
        author = "baric"
        date = "12/12/2025"
        description = "yara rule"
        
    string: 
        $s1 = "rundll32.exe" fullword ascii
        $s2 = "msvcrt.dll" wide
        $url1 = /http:\/\/.*malhare.*/ nocase
        $hidden = "Malhare" xor
        $b64 = "SOC-mas" base64
        $cmd = /powershell.*-enc\s+[A-Za-z0-9+/=]+/ nocase
        $hex_string = { E3 41 ?? C8 G? VB }

        
    condition:
        all of them

}
```

#### Breakdown

```
rule yara_rule
```

* rule has to start it but the name can be anything

```
meta:
        author = "baric"
        date = "12/12/2025"
        description = "yara rule"
```

* meta has to start it&#x20;
  * author = "any string"
  * date = "any string"
  * description = "any string"

```
string: 
        $s1 = "rundll32.exe" fullword ascii
        $s2 = "msvcrt.dll" wide
        $url1 = /http:\/\/.*malhare.*/ nocase
        $hidden = "Malhare" xor
        $b64 = "SOC-mas" base64
        $cmd = /powershell.*-enc\s+[A-Za-z0-9+/=]+/ nocase
        $hex_string = { E3 41 ?? C8 G? VB }
```

* string has to start it
  * $s1 can be any string but has to start with $
    * that goes for all values below
  * What the values except after the = and between ""
    * strings
    * numbers
    * regex&#x20;
    * hex
    * There is more but that is all I have needed
  * After the "" there are key words
    * fullword - looks for whole word not just contains
    * ascii - single byte or char search
    * wide - look for the selected format
    * nocase - don't matter upper or lower case
    * xor - checks all possible single-byte XOR variations
    * base64 - if string is encoded to base 64 it decrypts and tries to match
    * There is more

```
condition:
        all of them
```

* What to match to under strings
  * any of them - any one that triggers (single) then return
  * all of them - return all that matches (multi)



#### How to run YARA on your machine

* Windows:
  * Download `yara-x.x.x-win64.zip` (or 32-bit) from the YARA GitHub Releases page.
  * Extract `yara.exe` and `yarac.exe` to a folder (e.g., `C:\Tools\YARA`).
  * Add this folder to your system's `PATH` environment variable.
  * Install the Visual C++ Redistributable if needed.
* Linux:
  * Use your package manager: `sudo apt install yara` (Debian/Ubuntu) or `sudo yum install yara` (RHEL/CentOS).
  * For the latest version, compile from source or use YARA-X.
* Mac:
  * Use Homebrew: `brew install yara`.
  * YARA-X can also be installed via Homebrew: `brew install yara-x`.&#x20;

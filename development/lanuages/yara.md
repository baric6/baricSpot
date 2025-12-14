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
        $s2 = "the" wide
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



#### How to Install YARA to your machine

* Windows:
  * Download [`yara-x.x.x-win64.zip`](https://github.com/VirusTotal/yara/releases) (or 32-bit) from the YARA GitHub Releases page.
  * Extract `yara.exe`
  * Add this folder to your system's `PATH` environment variable or make a folder with the extracted exe and run it from that folder using yara64.exe
  * Install the Visual C++ Redistributable if needed, I didn't need to
* Linux:
  * Use your package manager: `sudo apt install yara` (Debian/Ubuntu) or `sudo yum install yara` (RHEL/CentOS).
  * For the latest version, compile from source or use YARA-X.
* Mac:
  * Use Homebrew: `brew install yara`.
  * YARA-X can also be installed via Homebrew: `brew install yara-x`.&#x20;

#### Running YARA on your machine

Windows

* I will be running the executable vs putting it in sys-vars
* It is good to find some yara rules on the net or create your own you need something to run with it. I will be using the one we created above
* navigate to the folder you put the yara exe in for ease of use put the rules in the same directory, in the root of the file is OK for the time being

```
yara64.exe -r -w /path/to/file.yar /path/to/scan/location/
```

* when you run it something should populate from the second string var in the file.
  * if it looks like it is just hanging it is scanning if it finds something it will populate
* -r&#x20;
  * means recursive good for scanning folders
* -w&#x20;
  * disable warnings, it will gunk up the results&#x20;

#### Example of output

```
WarpStrings D:\3dsHacksBackup8-29-23\\3dsbackup\Nintendo 3DS\66f8577af89050f1fa8c86bd581bd4b1\4d5c00cc478040655355333200035344\title\00040000\001bc600\content\00000000.app

Warp D:\3dsHacksBackup8-29-23\\3dsbackup\Nintendo 3DS\66f8577af89050f1fa8c86bd581bd4b1\4d5c00cc478040655355333200035344\title\00040000\001bc600\content\00000000.app

Cobalt_functions D:\3dsHacksBackup8-29-23\\3dsbackup\Nintendo 3DS\66f8577af89050f1fa8c86bd581bd4b1\4d5c00cc478040655355333200035344\title\00040000\000cce00\content\00000004.app

Cobalt_functions D:\3dsHacksBackup8-29-23\\3dsbackup\Nintendo 3DS\66f8577af89050f1fa8c86bd581bd4b1\4d5c00cc478040655355333200035344\title\00040000\00173b00\content\00000000.app

WarpStrings D:\3dsHacksBackup8-29-23\\3dsbackup\Nintendo 3DS\66f8577af89050f1fa8c86bd581bd4b1\4d5c00cc478040655355333200035344\title\00040000\00173b00\content\00000000.app

Warp D:\3dsHacksBackup8-29-23\\3dsbackup\Nintendo 3DS\66f8577af89050f1fa8c86bd581bd4b1\4d5c00cc478040655355333200035344\title\00040000\00173b00\content\00000000.app
```

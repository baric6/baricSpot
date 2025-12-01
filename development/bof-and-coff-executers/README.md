# BOF and Coff Executers

#### What is a BOF and a COFF file

They are code snip its that can run in memory and report back to a listening server. By themselves they can be run and need a loader like a C2 to get them in memory then they can be executed. These files are fairly similar and can do the same kind of things but differs on how to get them to run.

#### COFF (Common Object File Format) <- more manual written with C/C++ also needs some kind of loader to get into memory

**COFF is an object file format.**\
It’s what compilers generate _before_ turning code into a final EXE or DLL.

Think of COFF like:

* a raw chunk of compiled machine code
* no entry point (`main`)
* no imports table
* no PE headers
* no loader

What can you do with a COFF

* Enumerate processes
* Dump credentials
* Patch memory
* Scan networks
* Read/write files
* Perform privilege checks
* Execute shellcode
* Collect system info
* Run custom C logic



#### BOF (Beacon Object File) <- used a lot with C2 servers that already has a implant&#x20;

A **BOF is a COFF file designed to be executed in-memory** by a C2 agent such as:

* Cobalt Strike Beacon
* Sliver implants (BOF support)
* Mythic agents
* Custom COFF loaders

A BOF is basically:

* Tiny C code
* Compiled to COFF
* Loaded into memory by the C2 agent
* Executed by calling a specific exported function (`go`)

Why BOFs exist? Because they are:

* **Small**
* **In-memory only** (no touching disk)
* **Fast to run**
* **Harder to detect**
* **Reusable modules**
* Enumerate processes
* Dump credentials
* Patch memory
* Scan networks
* Read/write files
* Perform privilege checks
* Execute shellcode
* Collect system info
* Run custom C logic


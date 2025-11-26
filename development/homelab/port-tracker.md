# Port Tracker

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

* **Automatic Port Discovery**: Scans the host system to find and display running services and their ports automatically. No manual data entry is needed.
* **Platform-Specific Collectors**: Includes specialized collectors for Docker and TrueNAS to gather rich, contextual information from the host.
* **Internal Port Detection**: Distinguishes between internal container ports and published host ports, providing complete visibility into containerized services.
* **Lightweight & Self-Contained**: Runs as a single process with an embedded SQLite database. No external database dependencies like PostgreSQL or Redis are required.
* **Peer-to-Peer Monitoring**: Add other `portracker` instances as peers to view all your servers, containers, and VMs from a single dashboard.
* **Hierarchical Grouping**: Organize servers in a parent-child structure, perfect for nesting servers, e.g. a VM's `portracker` instance under its physical host.
* **Enhanced TrueNAS Discovery**: Providing an optional TrueNAS API key allows `portracker` to discover running VMs\* and gather enhanced system information like the OS version and uptime.
* **Modern & Responsive UI**: A clean dashboard with light/dark modes, live filtering, and multiple data layout views (list, grid, table).

{% embed url="https://github.com/mostafa-wahied/portracker/" %}

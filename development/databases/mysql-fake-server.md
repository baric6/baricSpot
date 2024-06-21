# MySQL Fake Server

When the JDBC URL is controllable, a special MySQL server can read any file or perform deserialization operations on the JDBC client.

The MySQL protocol is partially implemented entirely using Java, with built-in common ysoserial chains, one-click launch, and automatic generation of usable payloads for testing.

Refer to the MySQL\_Fake\_Server project, the payload is transmitted from the user parameter. The deserialization operation should start with deser\_, and the rule is deser\_\[gadget]_\[cmd]. The file reading should start with fileread_, and the rule is fileread\_\[name].

Due to the existence of special characters in some file names or commands, it is possible to use the base64 transmission method, which is based on the original user and followed by base64 after base64, such as user=deser\_CB\_calc.exe is equal to user=base64ZGVzZXJfQ0JfY2FsYy5leGU=.

By default, the files are saved in the directory named after the current timestamp under the fake-server-files directory in the current directory (the directory is automatically created).

Download&#x20;

{% embed url="https://github.com/4ra1n/mysql-fake-server/blob/master/doc/README.md" %}

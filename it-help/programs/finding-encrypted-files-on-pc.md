# Finding encrypted files on PC

For many versions, Windows has included an advanced security feature called Encrypting File System (EFS). It allows the user to store files and folders encrypted, so they will be protected from unwanted access. However, File Explorer doesn't offer a quick way to find all encrypted files stored on your drive. Here's an alternative solution.

Encrypting File System (EFS) is a useful feature. Other user accounts cannot access your encrypted files, neither can anyone from the network or by booting into another OS and accessing that folder. This is the strongest protection which is available in Windows to protect individual files and folders without encrypting the whole drive.

When a folder or file is encrypted using Encrypting File System (EFS), the File Explorer app shows a pad lock overlay icon for such a file or folder.

<figure><img src="../../.gitbook/assets/image (238).png" alt=""><figcaption></figcaption></figure>

Tip: File Explorer can show encrypted files in green color. You need to turn on this feature manually as described in the article Show Compressed and Encrypted Files in Color in Windows 10.

<figure><img src="../../.gitbook/assets/image (239).png" alt=""><figcaption></figcaption></figure>

Show Compressed Encrypted Files In Color In File Explorer

When you encrypt a folder, new files saved into that folder will automatically be encrypted.

Note: Encryption will be disabled for a folder, if you compress it, move it to a ZIP archive, or copy to a location that doesn't support NTFS encryption with EFS.

Sometimes it can be useful to quickly find all your encrypted files in a folder. In Windows XP, Vista, Windows 7, Windows 8 and Windows 10, there is a console utility called "cipher". It is a command line tool to work with encrypted files using EFS (Encrypting File System).

Here is how it can be done.\
To Find All Encrypted Files in Windows 10,

Open a new command prompt

&#x20;Type the following command:&#x20;

`cipher /u /n /h`

Find Encrypted Files The command will list your encrypted files.

<figure><img src="../../.gitbook/assets/image (240).png" alt=""><figcaption></figcaption></figure>

You are done!

If you have plenty of files, it might be useful to save the list to a text file. Having a text file with the list of encrypted files makes it easy to find and check them out.

Execute the following command in the command prompt:

`cipher /u /n /h > "%UserProfile%\Desktop\encrypted_files.txt"`

This will create the file encrypted\_files.txt on your desktop.Windows 10 Find Encrypted Files

<figure><img src="../../.gitbook/assets/image (241).png" alt=""><figcaption></figcaption></figure>

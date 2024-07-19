# Uploading lookup table csv file

1. Under settings in the top right part of the menu and select Lookups
2. Select lookup table files&#x20;
3. there is a green button named New Lookup Table, File click it

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

4. Fill in the data and browse for the file needed
   1. Destination app : search
   2. upload a lookup file: must be a CSV file
   3. Destination filename: name it the same as your file
   4. click save

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

5. Go to search and type

`| inputlookup <filename or what you put in Destination filename>`

You should see you data&#x20;

6. To search for matching data you can query:

`*| lookup ip.csv "IP Address" as d_ip OUTPUT "IP Address" as ip | eval Ip=replace(srcIp, ":\d+$", "") | search Ip=* | stats count by Ip`

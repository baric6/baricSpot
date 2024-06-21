# Powershell port scanner

```
#This PowerShell script will scan the network for open ports and running services to identify vulnerabilities.

#Create an array to store the results
$results = @()

#Get a list of active computers on the network
$computers = Get-Content C:\computers.txt

#Loop through each computer
foreach($computer in $computers) {

    #Run netstat to get a list of open ports and running services
    $ports = netstat -ano -p tcp -r | Where { $_ -match $computer } 

    #Loop through each line of the output
    foreach($line in $ports) {

        #Split the line into elements
        $elements = $line.Split(' ')

        #Create a new object to store the result
        $result = "" | Select Computer, Port, Service

        #Populate the object with the values from the output
        $result.Computer = $computer
        $result.Port = $elements[1]
        $result.Service = $elements[2]

        #Add the object to the results array
        $results += $result
    }
}
```

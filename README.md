# Powershell Tasks

## Challenge 1: Find Listening Ports

- Given a list of port numbers, we want to use this list to see if the local port is listening.

### Script:
$system_ports = Get-NetTCPConnection -State Listen
$my_ports = Get-Content -Path C:\Users\Administrator\Desktop\ports.txt

foreach($port in $my_ports)
{
	If($port) -in $system_ports.LocalPort){
	echo $port
	} 
}


## Challenge 2: Find a file with password from multiple folders
 - Given an email folder contains copies of the emails John, Martha, and Mary have been sending to each other(and themselves). Find the file containing a password.

### Script:
$pass_var = ‘password’
$files = Get-ChildItem $path C:\Users\Administrator\Desktop\emails\*’  -recurse | Select-String $pass_var
echo $files
$https = ‘https'
$https_files = Get-ChildItem $path C:\Users\Administrator\Desktop\emails\*’  -recurse | Select-String $https
echo $https_files


## Challenge 3: Simple port scanner using Powershell
- Determine IP ranges to scan (in this case it will be localhost) and you can provide the input in any way you want
- Determine the port ranges to scan
- Determine the type of scan to run (in this case it will be a simple TCP Connect Scan)
  
### Script:
  
$target = "localhost"
for($i=130;$i -le 140;$i++)
{
Test-NetConnection -ComputerName $target -Port $i -InformationLevel "Detailed"
}

<img width="676" height="607" alt="image" src="https://github.com/user-attachments/assets/47ade17a-8eb6-40ed-982b-8c60af9e33a8" />

Note: Path of files and folders are added for the purpose of learning. I have implemented and executed above challenges in the virtual box of TryHackMe Server. 

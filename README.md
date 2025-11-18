# powershell_scripts

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
}<img width="754" height="243" alt="image" src="https://github.com/user-attachments/assets/0566e6ab-0b39-4c30-aae6-e54b64ab21cc" />


## Challenge 2: Find a file with password from multiple folders
 - Given an email folder contains copies of the emails John, Martha, and Mary have been sending to each other(and themselves). Find the file containing a password.

### Script:
$pass_var = ‘password’
$files = Get-ChildItem $path C:\Users\Administrator\Desktop\emails\*’  -recurse | Select-String $pass_var
echo $files
$https = ‘https'
$https_files = Get-ChildItem $path C:\Users\Administrator\Desktop\emails\*’  -recurse | Select-String $https
echo $https_files<img width="1066" height="289" alt="image" src="https://github.com/user-attachments/assets/81e48037-dbb2-44c5-ad1f-984fe17587a3" />


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

<img width="842" height="135" alt="image" src="https://github.com/user-attachments/assets/98c54389-43a2-4e76-a764-9b3ad3689076" />

# Powershell Remote Management

- Get a session on the remote PC
```
$cred = get-credential
Enter-PSSession -ComputerName erikmpc -credential $cred
```

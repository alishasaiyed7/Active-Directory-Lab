## Task 2: Unlock Multiple Accounts
```
Search-ADAccount -LockedOut | Unlock-ADAccount
```
Search-ADAccount -LockedOut - Search and  display all Locked account.
Unlock-ADAccount - It will unlock all the locked accounts.

## Task 3: Reset Passwords (Bulk)

Import-Module ActiveDirectory

Get-ADUser -Filter * -SearchBase "OU=Users,DC=domain,DC=local" | 
ForEach-Object {
    Set-ADAccountPassword $_ -Reset -NewPassword (ConvertTo-SecureString "Temp@1234" -AsPlainText -Force)
}

## 🧪 Task 4: Get List of Disabled Users
Get-ADUser -Filter 'Enabled -eq $false' -Properties Enabled |
Select Name, SamAccountName |
Export-Csv "..\outputs\disabled-users.csv" -NoTypeInformation

Note - still working on it

# Author 
Alisha saiyed

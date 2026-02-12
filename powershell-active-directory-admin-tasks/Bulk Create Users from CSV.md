## ✅ Step 1: Create the CSV File (users.csv)
🔹 Using Notepad (Simplest)

On your Domain Controller (or admin machine with RSAT):

Right-click on Desktop → New → Text Document

Rename it to:
👉 users.csv
# (Make sure it’s not users.csv.txt)

Right-click users.csv → Open with Notepad

Paste this:
```
FirstName,LastName,Username,Password,OU
John,Doe,jdoe@domain.local,P@ssw0rd123,"OU=Users,DC=domain,DC=local"
Jane,Smith,jsmith@domain.local,P@ssw0rd123,"OU=Users,DC=domain,DC=local"
```

Copy Paste and Change details to as many users you want.
# Note - Make Sure OU = users exist and Change DC to your Domain Controller.

Click File → Save

⚠️ Important:
Put double quotes around OU path because commas exist inside it.


## ✅ Step 2: Create the OU in Active Directory (If Not Already Created)

You must have this OU before running the script.

Open Active Directory Users and Computers

Right-click your domain (e.g., domain.local)

Click New → Organizational Unit

Name it:
👉 Users

Click OK

So your OU path becomes:
```
OU=Users,DC=domain,DC=local

```
✅ Step 3: Save the PowerShell Script

Right-click Desktop → New → Text Document

Rename to:
👉 bulk-create-users.ps1

Open it in Notepad and paste:
```
Import-Module ActiveDirectory

$users = Import-Csv "C:\Users\Administrator\Desktop\users.csv"

foreach ($user in $users) {
    New-ADUser `
        -Name "$($user.FirstName) $($user.LastName)" `
        -GivenName $user.FirstName `
        -Surname $user.LastName `
        -UserPrincipalName $user.Username `
        -SamAccountName ($user.Username.Split("@")[0]) `
        -AccountPassword (ConvertTo-SecureString $user.Password -AsPlainText -Force) `
        -Path $user.OU `
        -Enabled $true `
        -ChangePasswordAtLogon $true
}
```

# Note - If your desktop path is different, update the CSV path accordingly.

## ✅ Step 4: Run the Script (Safely)

Open PowerShell as Administrator

Allow script execution (lab only):
```
Set-ExecutionPolicy RemoteSigned
```
Navigate to Desktop: - Your location where your file is saved
```
cd C:\Users\Administrator\Desktop
```

Run script:
```
.\bulk-create-users.ps1
```

## ✅ Step 5: Verify Users Created

Open Active Directory Users and Computers

Go to OU = Users

You should see:

John Doe

Jane Smith
(and others if added)


## 🧠 Common Mistakes (And Fixes)

❌ OU not found error
👉 Fix: Make sure OU exists and DN path is correct

❌ Access denied
👉 Fix: Run PowerShell as Administrator

❌ Execution policy error
👉 Fix:
```
Set-ExecutionPolicy RemoteSigned
```
❌ CSV not found
👉 Fix: Make sure CSV file path in script matches actual location

# Author
Name- Saiyed Alisha



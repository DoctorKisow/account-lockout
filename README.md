# account-lockout
**account-lockout** - Account lockout notice.<br>
Matthew R. Kisow, D.Sc. <matthew.kisow@@nsabp.org><br>
Copyright &copy; Matthew R. Kisow, D.Sc.  2020-2021. 

## Install
1. Copy the script to sysvol scripts.
```shell
     copy account-lockout.ps1 \\<domain>\SysVol\<domain>\Scripts\
     copy account-lockout.ps1 C:\Scripts\
```
2.  Create a scheduled task:<br>
    **GENERAL**<br>
    ```shell
    a. Name:              Account Lockout Notification
    b. Description:       Send an email on an account lockout event.
    c. Security Options:
       1.) Create a service account with "Domain Admin" and "Logon as a Batch" rights.
       2.) Run whether the user is logged on or not.
       3.) Run with the highest privileges.
    ```
    
    **TRIGGERS**<br>
    ```shell
    a. Begin the task: On an event.
    b. Settings:
       1.) Basic
       2.) Log:      Security Log
       3.) Source:   Microsoft Windows security auditing.
       4.) Event ID: Event ID: 4740
    ```
    
    **ACTIONS**<br>
    ```shell
    a. Action:                    Start a program.<br>
    b. Program/script:            powershell.exe<br>
    c. Add arguements (optional): -NoProfile -ExecutionPolicy Bypass -nologo -file "C:\Scripts\account-lockout.ps1"<br>
    ```
    
## License
License (GPL v3.0)

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version. This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details. You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.

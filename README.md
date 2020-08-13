# firewalld-block-ipset

**IMPORTANT NOTICE:** *Use at your own risk. Do not use in production environments until you have tested the behavior of this code! I take no responsibilty for misuse, damages, or general nonsense resulting from using this code. Feel free to comment on any suggested improvements.*

## Requirements
* linux
* bash
* firewalld
* ipset
* a file 'index.txt' containing a list of country codes from ipdeny.com, one per line.
* ???

## Usage:
```
/bin/bash firewalld-block-ipset.sh
```
Note that the first time you run this, you may get some errors with firewalld. This is fine, as it'll try to remove nonexistant ipset lists/sources. After the initial run, you should start seeing 'success' in stdout and a final message showing how many targets were blocked. 

## Description:
Got a lot of bots and random connections coming to your server? Want to block an entire country to mitigate the problem? You've come to the right place! 

Use this script to block known ipv4 and ipv6 ranges associated with the countries you don't want to access your systems. Before running the script, get a list together of country codes via https://www.ipdeny.com/ipblocks/ and place them in a file called 'index.txt' in the same working directory as the script itself. Then, run however you see fit. Could be used to update ipset lists automagically via cron! Have fun, and block responsibly.

This pairs nicely with fail2ban -- I personally run both this script in a cron job and have fail2ban monitoring my ssh connections for repeat offenders. This greatly reduced the threat-pool by outright blocking some common offenders.

## Credits
* Thanks to `forum:IfThenElse` on the Linode forums -- source: https://www.linode.com/community/questions/11143/top-tip-firewalld-and-ipset-country-blacklist
* Thanks to the folks at https://www.ipdeny.com/ for providing lists of ip ranges by country-code for free public usage. 

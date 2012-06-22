1. Perform server backups - Contact CIIST (use Amanda).

2. Organize user folders within home directory:
    
    ::2.1 Remove users in 'to_delete' folder.
    
    ::2.2 Lock users' password ("usermod --expiredate 1"), in the 'to_cleanup' folder.

3. Exim - Ensure that email relaying is not allowed:

    3.1 Only accept messages from the localhost.
    
    3.2 Only accept messages from the outside to local ('inesc-id.pt', 'tagus.inesc-id.pt', 'gaips.inesc-id.pt') users specifically.

4. Webmail client (SquirrelMail FTW!) - Change URL (webmail or mail).

5. Stats management:

    web stats,
    eximstats,
    cacti,
    tripwire,
    apt-listchanges,
    resultado de apt-get upgrade.

6. Update INESC-ID Server instructions - From PDF to TXT.

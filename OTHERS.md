


Need to allow 8000 for testing 
    demo@chttl-8acc489f1587c5dc:~$ sudo ufw status
    [sudo] password for demo:
    Status: active
    
    To                         Action      From
    --                         ------      ----
    22                         ALLOW       Anywhere
    80                         ALLOW       Anywhere
    21/tcp                     ALLOW       Anywhere
    10000/tcp                  ALLOW       Anywhere
    22 (v6)                    ALLOW       Anywhere (v6)
    80 (v6)                    ALLOW       Anywhere (v6)
    21/tcp (v6)                ALLOW       Anywhere (v6)
    10000/tcp (v6)             ALLOW       Anywhere (v6)
    
    demo@chttl-8acc489f1587c5dc:~$


For this case, ufw is better than editing iptables

    demo@chttl-8acc489f1587c5dc:~$ sudo ufw allow 8000
    Rule added
    Rule added (v6)
    demo@chttl-8acc489f1587c5dc:~$ sudo ufw status
    Status: active
    
    To                         Action      From
    --                         ------      ----
    22                         ALLOW       Anywhere
    80                         ALLOW       Anywhere
    21/tcp                     ALLOW       Anywhere
    10000/tcp                  ALLOW       Anywhere
    8000                       ALLOW       Anywhere
    22 (v6)                    ALLOW       Anywhere (v6)
    80 (v6)                    ALLOW       Anywhere (v6)
    21/tcp (v6)                ALLOW       Anywhere (v6)
    10000/tcp (v6)             ALLOW       Anywhere (v6)
    8000 (v6)                  ALLOW       Anywhere (v6)



# Use ufw --help, to check commands

    (myvenv) demo@chttl-8acc489f1587c5dc:~/webapp$ sudo ufw status
    Status: active
    
    To                         Action      From
    --                         ------      ----
    22                         ALLOW       Anywhere
    80                         ALLOW       Anywhere
    21/tcp                     ALLOW       Anywhere
    10000/tcp                  ALLOW       Anywhere
    8000                       DENY        Anywhere
    8080                       ALLOW       Anywhere
    22 (v6)                    ALLOW       Anywhere (v6)
    80 (v6)                    ALLOW       Anywhere (v6)
    21/tcp (v6)                ALLOW       Anywhere (v6)
    10000/tcp (v6)             ALLOW       Anywhere (v6)
    8000 (v6)                  DENY        Anywhere (v6)
    8080 (v6)                  ALLOW       Anywhere (v6)
    
    (myvenv) demo@chttl-8acc489f1587c5dc:~/webapp$ sudo ufw delete 8000
    ERROR: Could not find rule '8000'
    (myvenv) demo@chttl-8acc489f1587c5dc:~/webapp$ sudo ufw delete 5
    Deleting:
     deny 8000
    Proceed with operation (y|n)? y

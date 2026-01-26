## Scenario: "Saskatoon": counting IPs.

**Description:** There's a web server access log file at `/home/admin/access.log`. The file consists of one line per HTTP request, with the requester's IP address at the beginning of each line.

Find what's the IP address that has the most requests in this file (there's no tie; the IP is unique). Write the solution into a file `/home/admin/highestip.txt`. For example, if your solution is `"1.2.3.4"`, you can do `echo "1.2.3.4" > /home/admin/highestip.txt`

**Root (sudo) Access:** False

**Test:** The SHA1 checksum of the IP address `sha1sum /home/admin/highestip.txt` is `6ef426cxxxxxxxx...` (just a way to verify the solution without giving it away.)



**Done:** 

> [!NOTE]
> **Initial/wrong understanding:** I got confused with this scenario, I thought all IPs in this output are unique and 10th column is representing maximum requests, so I used `awk '{print $10, $1}' | sort -kn 1 | tail -1`  to get the output but then I noticed that **sha1sum** is not matching with the desired solution and later I found that I understood the scenario wrong. 

**correct understanding:** every HTTP request have unique IP address and is counted as 1 request. So,we have to take a count/repetition of that unique IP address and find out the IP address making most HTTP calls. 

### steps taken for this:
1. 

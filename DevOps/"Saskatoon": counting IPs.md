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
1. used `cd ~` to come to home/user directory.
2. used `pwd` to confirm the current working directory.
3. used `ls` and then `tail -f access.log` to see and visualize the last 10 output of this file.
4. used `awk '{print $1}' access.log` to get only 1st column data which in this case was IPs.

> 5. **Final command:** used `awk '{print $1}' access.log | sort | uniq -c | sort -r | head -1` => Here, I am selecting 1st column of `access.log` output which is IPs, then using `sort` to sort it in ascending order, then using `uniq` command to count the IPs repetition, further sorting it recursively and taking 1st line of the output of this final command using `head`.

> 6. at last using command `echo "final_output_IP" > /home/admin/highestip.txt` to write the identified IP in existing file `highestip.txt`.

7. also verified if solution is correct using command `sha1sum /home/admin/highestip.txt`

## Scenario: "Saint John": what is writing to this log file?


**Description:** A developer created a testing program that is continuously writing to a log file `/var/log/bad.log` and filling up disk. You can check for example with `tail -f /var/log/bad.log`.
This program is no longer needed. Find it and terminate it. Do not delete the log file.

**Root (sudo) Access:** True

**Done:** 

1. used `ls` to find the filename in user directory which is writing log to `/var/log/bad.log`.
2. used `pwd` to confirm my current directory.
3. used `tail -f /var/log/bad.log` to check last 10 logs in this log file.
4. used `ls -al` to long list the available files in current directory to identify PID, which was `xyz`.
5. used `ps aux | grep bad` to confirm the PID.
6. used `kill xyz` to terminate the running program/process. 

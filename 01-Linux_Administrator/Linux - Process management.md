
# LINUX GUIDE - Process management
---
<br>

##
'at' command
---

command 'at' used for scheduling task / execution command
based time that we're set.

```bash
# Scheduling task
at <write the execution time>
```

```bash
at> <write the command here !> # press enter
at> # press CTRL + D to apply the schedule
```

```bash
# Check available scheduling task list
atq

# remove scheduling task
atrm <id>
```

<br>
<br>

## fg VS bg
---
simply if u run `sleep 60` in terminal<br>
the program takes over the terminal
<br>
<br>
literally u can't doing anything beside waiting<br>
the program end

but here's the thing.. <br><br>if u run `sleep 60 &` with the '&' symbol<br>the execution process stored in the backround<br>and.. u still can type anything in the terminal !

`fg = the command take over the terminal`<br>
`bg = the command was running in the backround`

<br>

try : 

```bash
# this categorized as foreground process (fg)
sleep 60
```

and try :

```bash
# this categorized as background process (bg)
sleep 60 &
```
<br>

### move the process 

fg --> bg

lets say u run this : 

```bash
sleep 60
```

press `ctrl` + `z` for pause the process (not suspend it)

and then run : 

```bash
bg
```

the paused process running again and now it stored in the backround. Check that process with run : 

```bash
jobs
```

<br>
<br>

bg --> fg

run this command : 

```bash
sleep 60 &
```
it will stored in the backround process<br>
u can check that with run : 

```bash
jobs
```

to move the process type from bg to fg, just run : 
```bash
fg
```

<br>all 
<br>

## nohup
---

nohup, stand's for no-hang-up

sometimes, we accidently close the terminal when we run something in there.

but when u running command with `nohup` and u close the terminal, the command still running even we already close the terminal.

<br>

Now... try open 2 separated terminal.

in first terminal, run this :

```bash
nohup sleep 225 &

#or

nohup sleep 255
```

and check the process running in second terminal by run :

```bash
ps -ef | grep sleep
```

the command meaning was : 
<br>

**"check the running process in 'everything full' mode, and specified show the sleep process."**

<br>

then u can see the process u specified want to find : 

```bash
user  19284    1 0  11:15  ?         00:00:00  sleep 225  
```

<br>
if u want to the process, just run : 

```bash
pkill sleep
```

<br>
<br>

## "ni" column in -top command
---

ni stands for nice value 

when u run : 

```bash
-top
```

there's column named `ni`<br>
basically it's just for priority CPU time usage

if comes with negative number (-), it called `not nice` value.<br>it means the program run with the highest priority and aggresively takes more CPU time

meanwhile, the other one called `nice value` means the program running with lowest priority and step aside from the highest priority.

<br>
<br>

## dmesg 
---

dmesg stand's for **diagnosis message**<br>

the command used to examine and control the kernel ring buffer.

### core use cases : 

- hardware troubleshooting

- Boot diagnostics

- Checking the system failures

<br>

### commonly used command and the arguments : 

<br>

```bash
sudo dmesg
```

 Displays the entire kernel log buffer (root privileges are usually required).

<br>
<br>


```bash
sudo dmesg -T
```  
Converts the raw, relative uptime timestamps into human-readable date and time formats. 

<br>
<br>

```bash
sudo dmesg -w
``` 
Follows the logs in real-time, printing new kernel events on screen as they happen (excellent for debugging hot-plugged devices). 

<br>
<br>



```bash
sudo dmesg -l err,warn
``` 
Filters the log output to only show messages flagged with a specific severity level, such as errors or warnings.

<br>
<br>


```bash
sudo dmesg | grep -i usb
```
Pipes the buffer into grep to quickly find references to a specific keyword or hardware type. <br>(the "usb" is for keyword example)

<br>
<br>

```bash
sudo dmesg -C
```
Clears the kernel ring buffer completely.

<br>
<br>

## iostat
---

iostat stand's for input/output statistic

it was a monitoring tools to measure CPU utilization and storage throughput, such HDD/SSD

<br>

### it used for :

- CPU utilization tracking 

- Device load monitoring

- Performance troubleshooting

<br> 

### commonly used command and the arguments :


```bash
iostat
```
Print a single summary report from system boot time.

<br>
<br>

```bash
iostat -d
```
Shows disk device statistics only, hiding the CPU report.

<br>
<br>

```bash
iostat -c
```
Shows CPU statistics only.

<br>
<br>

```bash
iostat -x
```
Displays extended statistics, including wait times (await) and device queue sizes (aqu-sz).

<br>
<br>

```bash
iostat 2 5
```
Repeats the report `every 2 seconds` for a total of **5 times**

<br>
<br>

## netstat
---

netstat as we know stands for **network statistics** ,

usually it used for network troubleshooting and monitor traffic performance.

with netstat, we can see how the network running in the back throught to be a process.

<br>

### commonly used command and the arguments :

<br>

```bash
netstat -a
```
Displays all active connections and listening ports.

<br>
<br>

```bash
netstat -n
```
Shows addresses and port numbers numerically ( but this skips DNS lookup for speed).

<br>
<br>

```bash
netstat -r
``` 
Displays the routing table.

<br>
<br>

```bash
netstat -s
``` 
Shows detailed protocol statistics for TCP, UDP, and IP.

<br>
<br>

```bash
#Command with the best arguments
netstat -ntlp
```
it show all the status and information about the protokol port.

---

#### checking information about cpu :
```bash
cat /proc/cpuinfo
```

#### checking information about memory usage : 

```bash
cat /proc/meminfo | grep Mem
```

log management : 

- /var/log/message
- /var/log/auth.log
- /var/log/secure
- /var/log/demsg
- /var/log/boot.log
- /var/log/httpd
- /var/log/mysql.log
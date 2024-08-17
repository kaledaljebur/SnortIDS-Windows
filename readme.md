This is customised SnortIDS v2.9 to suit Microsoft Windows, follow the following steps to get it working:

1. It is better to install it in a fresh Windows 10 to avoid the possible **_0xc00000b_** error if you use Windows Sever (there is another installation guide for Windows server case).
   - This Windows 10 can be used as a Network IDS and security analyser (security analyser is discussed in a different guide), but a copy of the network traffic should be forwarded to it in this case (this is not needed for the following steps).
2. Download and install Wireshark or just [Npcap](https://npcap.com/dist/npcap-1.79.exe).

   - Npcap needed by SnortIDS for traffic capturing and it is part of Wireshark.

3. Download SnortIDS from this [repository](https://github.com/kaledaljebur/snortids-windows/raw/main/Snort.zip) and unzip it in the C drive in Windows to be in
   - c:\Snort\ \
     ![alt text](images/snort-in-c-drive.png)
4. Run CMD as administrator and change directory to SnortIDS folder using:
   - cd c:\snort\bin \
     ![alt text](images/changedir.png)
5. Check the numbers of the available network adapters to select the one will be used by SnortIDS. \
   - snort -W
     ![alt text](images/snort-w.png)
   - In my case the number is 1 according to the above image, because 2 is for the loopback interface.
6. Run SnortIDS using:
   - snort -i 1 -c C:\Snort\etc\snort.conf -A console \
     ![alt text](images/snort-run.png)
   - Notice:
     - -i for the interface number.
     - -c for SnortIDS configuration file.
     - -A Alerts will be listed in the console.
7. Test the detection of ICMP, just to make sure the topology is working as expected.

   - Ping continuously the SnortIDS machine from external machine. \
     ![alt text](images/ping.png)
   - Then you should see the below in SnortIDS console even if the host firewall is blocking suck inbound requests: \
     ![alt text](images/snort-icmp.png)

8. Test the detection of SYN port scanning, this represent a passive attack as requeued by the assignment, ask your teacher if you have any questions.
   - Download and install [Zenmap](https://nmap.org/dist/nmap-7.95-setup.exe) in the ping Windows machine, then run it with the following options: \
     ![alt text](images/zenmap.png)
   - Then you should see the below in SnortIDS console. \
     ![alt text](images/nmap.png)
9. Analyse the log files:
   - Logs can be located in: \
     ![alt text](images/log.png)
   - Logs can be examined by Wireshark: \
     ![alt text](images/wireshark.png)
10. The two tested rules in SnortIDS can be locate here: \
    - c:\Snort\rules\local.rules \
      ![alt text](images/rules.png) \
      First rule at line 22 is for general ICMP ping detection if a quick test is needed. \
      The second at line 25 is for detecting SYN port scanning. \
      You can add # at the start of the line to disable any of them. \
      SnortIDS will need to be restarted for any changes.
11. Restarting SnortIDS can be by stopping the current running command using CRTL+C in the keyboard then run the SnordIDS command again (in step 6 above).

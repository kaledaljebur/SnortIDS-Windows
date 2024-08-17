This is customised SnortIDS to suite Microsoft Windows, follow the following step to get it working:

1. It is better to install it in Win10 to avoid the possible 0xc00000b error if you use Win Sever.
2. Download and install Wireshark or just [Npcap](https://npcap.com/dist/npcap-1.79.exe).

   - Npcap needed for SnortIDS and it is part of Wireshark

3. Download SnortIDS from this [repository](https://github.com/kaledaljebur/snortids-windows/blob/main/Snort.zip) and unzip it in the C drive in Windows to be in c:\Snort\ \
   ![alt text](images/snort-in-c-drive.png)
4. Run CMD as administrator and move to SnortIDS folder using:
   - cd c:\snort\bin
5. Check the order of the available network adapters to select the one will be used by SnortIDS \
   ![alt text](images/snort-w.png)

   - In my case the number is 1 according to the above image

6. Run SnortIDS using
   - snort -i 1 -c C:\Snort\etc\snort.conf -A console
   - Note that
     1. -i for the interface number
     2. -c for SnortIDS configuration file
     3. -A Alerts will be listed in the console
7. Test the ICMP detection, just to make sure the topology is working as expected.

   - Ping continuously the SnortIDS machine from external machine \
     ![alt text](images/ping.png)
   - Then you should see the below in SnortIDS console even if the host firewall is blocking suck inbound requests: \
     ![alt text](images/snort-icmp.png)

8. Test the SYN port scanning detection, this represent a passive attack and it is requeued by the assignment, ask your teacher if you have any questions.
   - Download and install [Zenmap](https://nmap.org/dist/nmap-7.95-setup.exe) in the ping Windows machine. \
     ![alt text](images/zenmap.png)
   - Then you should see the below in SnortIDS console \
     ![alt text](images/nmap.png)
9. Analyse the log files
   - logs can be located in: \
     ![alt text](images/log.png)
   - logs can be located in: \
     ![alt text](images/wireshark.png)

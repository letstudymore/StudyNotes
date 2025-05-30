
Finding BSSID from pcap file:
Open Pcap File > Filter > wlan.ssid == "NAME" 
Source MAC

aircrack-ng FILE.cap

aircrack-ng -a2 -b BSSID -w rockyou.txt FILE.cap


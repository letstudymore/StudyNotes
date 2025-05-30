
##  DNS Enumeration using Zone Transfer

Now, run cd command to jump to the root directory.

Run dig ns [Target Domain] command (here, the target domain is www.certifiedhacker.com).**
In this command, ns returns name servers in the result

Run **dig @[NameServer] [Target Domain] axfr** command (here, the name server is **ns1.bluehost.com** and the target domain is **www.certifiedhacker.com**)

**Transferencia de DNS - LINUX**

dig @ns1.bluehost.com www.certifiedhacker.com axfr

**No Windows 11**

Click windows **Search** icon on the **Desktop**. Search for **cmd** in the search field, the **Command Prompt** appears in the results, click **Open** to launch it.

The **Command Prompt** window appears; execute command **nslookup**.

In the nslookup **interactive** mode, execute command **set querytype=soa**

Type the target domain **certifiedhacker.com** and press **Enter**. This resolves the target domain information.

set **querytype=soa** sets the query type to SOA (Start of Authority) record to retrieve administrative information about the DNS zone of the target domain **certifiedhacker.com**.
  
In the **nslookup** interactive mode, execute command **ls -d [Name Server]** (here, the name is **ns1.bluehost.com**).





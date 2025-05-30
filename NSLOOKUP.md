

In the nslookup interactive mode, type set type=a and press Enter. Setting the type as “a” configures nslookup to query for the IP address of a given domain.


Thus, if the response is coming from your local machine’s server (Google), but not the server that legitimately hosts the domain www.certifiedhacker.com; it is considered to be a non-authoritative answer. Here, the IP address of the target domain www.certifiedhacker.com is 162.241.216.11.

Since the result returned is non-authoritative, you need to obtain the domain's authoritative name server.

Type set type=cname and press Enter. The CNAME lookup is done directly against the domain's authoritative name server and lists the CNAME records for a domain.

Type certifiedhacker.com and press Enter.

This returns the domain’s authoritative name server (ns1.bluehost.com), along with the mail server address (dnsadmin.box5331.bluehost.com), as shown in the screenshot.

The authoritative name server stores the records associated with the domain. So, if an attacker can determine the authoritative name server (primary name server) and obtain its associated IP address, he/she might attempt to exploit the server to perform attacks such as DoS, DDoS, URL Redirection, etc.
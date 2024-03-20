egrep "minlen|credit" /etc/security/pwquality.conf | grep -v "#"


#!/bin/bash

# Set variables
PWQUALITY_CONF="/etc/security/pwquality.conf"

# Update pwquality.conf file
sudo sed -i.bak \
-e '/\s*dcredit.*/s/.*/dcredit=-1/' \
-e '/susucredit.*/s/.*/ucredit=-1/' \
-e '/selcredit.*\solcredit.*/s/.*/lcredit=-1/' \
-e '/minlen.*/s/.*/minlen=8/' \
$PWQUALITY_CONF


What this command does

chage -d 2024-03-20 -m 7-M 90-I-1-E-1 <user id>

This command modifies the password change information for a user. Let's break it down:

- `chage`: This command is used to change user password expiry information.
- `-d 2024-03-20`: Sets the date of the last password change to March 20, 2024.
- `-m 7`: Sets the minimum number of days between password changes to 7.
- `-M 90`: Sets the maximum number of days the password is valid before the user is required to change it (in this case, 90 days).
- `-I -1`: Sets the number of days after a password expires before the account is disabled (in this case, the account will not be disabled after the password expires).
- `-E -1`: Sets the number of days before the account expires that the user is warned that their password will expire (in this case, the user will not receive a warning).

Replace `<user id>` with the actual user ID for which you want to modify the password change information.
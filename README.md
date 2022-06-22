# Mailer
A toy script for fetching and writing emails.

## Usage
```
usage: mailer [-h] [--server {kth,outlook}] {send,send-file,fetch} ...

Send and receive mails

optional arguments:
  -h, --help            show this help message and exit
  --server {kth,outlook}

commands:
  {send,send-file,fetch}

```

Fill in the `configuration.yml` file with appropriate information. Different mail providers use different values, so you need to look up how they work for yours. The host/port can be found by searching for IMAP (ingoing) or SMTP (outgoing) for your specific email provider. For example, "gmail IMAP SMTP".

First time you'll get asked for a password, and the following times it'll use a encrypted version of the password stored in your home folder under ".mailer/.users". 

**NOTE:** The encryption is purely for testing, as it's completely useless. The encryption key is stored at ".mailer/.key" and can be used to decrypt the password. Also, the password is decrypted in the code as the libraries want the raw passwords, so anyone who can attach a debugger at the right place can see the password in plain text.

You can send a mail through the command line by passing in arguments or by passing in a file. The file should then start with the required email headers:
* "From: "
* "To: "
* "Subject: "

"Cc: " and "Date: " are optional. The value of the headers can be omitted or overridden if they are provided as arguments in the command line.

# Why won't mail send? "Network is unreachable"

If you find in /var/log/mail.log the following...

```
connect to gmail-smtp-in.l.google.com[2607:f8b0:400d:c06::1a]:25: Network is unreachable
```

...Postfix might have a preference for IPv6 when the destination/path has an IPv4 requirement.

Change inet_protocol option in postfix settings. Go to /etc/postfix/main.cf and change from:
```
inet_protocols = all
```
to:
```
inet_protocols = ipv4
```
Then...
```
service postfix stop
service postfix start
service postfix flush
```

Source: https://unix.stackexchange.com/questions/110390/why-i-cant-send-mail-to-remote-mailbox

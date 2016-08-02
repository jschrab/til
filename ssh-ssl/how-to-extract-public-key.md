# How to Extract a Public Key from a Private Key

```
$ openssl rsa -in privkey.pem -pubout
```
...sends the public key of **privkey.pem** to stdout

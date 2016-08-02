### How to Extract Organizational Details from a CSR

```
$ openssl req -noout -text -in server.csr
```
...sends the Common Name, Organization, Organizational Unit, etc. of **server.csr** to stdout

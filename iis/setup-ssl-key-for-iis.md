# Setup SSL Key for IIS

```
openssl pkcs12 -export -out domain.name.pfx -inkey domain.name.key -in domain.name.crt
```

Might need to sudo if there is an "unable to write 'random state'" error.

Source: http://www.sherweb.com/blog/when-given-crt-and-key-files-make-a-pfx-file/

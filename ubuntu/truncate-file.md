# Truncate a File While Maintaining Permissions

This is so silly...

```bash
: > myfile.txt
```
":" is a no-op in Bash. So "do nothing and redirect the result into _myfile.txt_."

Permissions are preserved.

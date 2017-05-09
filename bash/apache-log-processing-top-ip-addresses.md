# Apache Log Processing - Top IP Addresses

Take an Apache log file, pull the IP address from the front of a line, sort them, filter down to unique addresses, sort the "counts", then show just the top 20.

```Bash
cat access.log > awk '{print $1}' | sort -n | uniq -c | sort -nr | head -20
```

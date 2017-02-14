### Bigger postBuffer
Cloning of some git repos may be either large themselves or have large objects in them that may result in a disconnect because of a timeout:
```bash
fatal: The remote end hung up unexpectedly
fatal: early EOF
fatal: index-pack failed
```
A larger postBuffer can help:
```bash
git config --global http.postBuffer 524288000
```
More details from the git config man page, http.postBuffer is about:
```
Maximum size in bytes of the buffer used by smart HTTP transports when POSTing data to the remote system.

For requests larger than this buffer size, HTTP/1.1 and Transfer-Encoding: chunked is used to avoid creating a massive pack file locally. Default is 1 MiB, which is sufficient for most requests.
```
Source: http://stackoverflow.com/a/6849424/12694

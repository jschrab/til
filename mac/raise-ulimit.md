# How to raise the ulimit _or_ How to solve the "Too many open files in system" problem

Summary: MacOS has paltry files-open limits for developers, who have high resource needs. It needs to be raised but El Capitan locks this sort of thing down requiring more work to change the limits.

1. Create two files, owned by root:wheel

  /Library/LaunchDaemons/limit.maxfiles.plist

  ```xml
<?xml version="1.0" encoding="UTF-8"?>  
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"  
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">  
  <dict>
    <key>Label</key>
    <string>limit.maxfiles</string>
    <key>ProgramArguments</key>
    <array>
      <string>launchctl</string>
      <string>limit</string>
      <string>maxfiles</string>
      <string>524288</string>
      <string>524288</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>ServiceIPC</key>
    <false/>
  </dict>
</plist>
```

  /Library/LaunchDaemons/limit.maxproc.plist

  ```xml
<?xml version="1.0" encoding="UTF-8"?>  
<!DOCTYPE plist PUBLIC "-//Apple/DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">  
  <plist version="1.0">
    <dict>
      <key>Label</key>
        <string>limit.maxproc</string>
      <key>ProgramArguments</key>
        <array>
          <string>launchctl</string>
          <string>limit</string>
          <string>maxproc</string>
          <string>2048</string>
          <string>2048</string>
        </array>
      <key>RunAtLoad</key>
        <true />
      <key>ServiceIPC</key>
        <false />
    </dict>
  </plist>
```
2. Reload these files with...

  ```bash
  sudo launchctl load -w /Library/LaunchDaemons/limit.maxfiles.plist
  sudo launchctl load -w /Library/LaunchDaemons/limit.maxproc.plist
  ```
3. Reboot MacOS

Source: http://blog.dekstroza.io/ulimit-shenanigans-on-osx-el-capitan/

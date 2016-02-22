# How to securely delete a file on MacOS X

**srm**  removes  each  specified  file by overwriting, renaming, and truncating it before unlinking. This prevents other people from undeleting or recovering any information about the file from the command line.

```
srm -v <filename>
```
... or to recursively delete a folder ...
```
srm -rv <directory-name>
```

**THIS IS NOT A GUARANTEE ON SSD BASED MAC'S**  
CVE-2015-5901 - Makes it clear that block relocating by an SSD controller may make it _appear_ that a file has been securely deleted but it may not be. This is why this feature was removed in El Capitan.

Source - https://www.intego.com/mac-security-blog/how-to-securely-empty-trash-in-os-x-el-capitan/

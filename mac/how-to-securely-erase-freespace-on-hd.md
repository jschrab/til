# How to securely erase free space on a Mac HD/SSD

To fully clean up your drive, you can use another Terminal command to securely erase all its free space. (This feature used to be available in Disk Utility, but Apple removed it.). The command is as follows:

```
diskutil secureErase freespace LEVEL /Volumes/DRIVE
```

Replace DRIVE with the name of your drive, and LEVEL to a number from 0 to 4. The following describes what these numbers mean:

0 writes zeroes to the disk once  
1 writes a series of random numbers  
2 writes zeroes 7 times  
3 writes zeroes 35 times  
4 writes zeroes 3 times

Be aware that for large volumes, the amount of time it can take to securely erase free space on a volume can be extraordinary.

It is possible, in the case of SSD's, that a full secure erase isn't possible because of SSD block controller reallocation of blocks.

As Your Attorney, I must advise you have a full backup of your Mac on hand before trying this.

Source: https://www.intego.com/mac-security-blog/how-to-securely-empty-trash-in-os-x-el-capitan/

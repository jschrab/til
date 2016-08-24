# Updates Held Back - How and Why?

Given...

```bash
$ sudo apt-get upgrade                                                                                                
Reading package lists... Done                                                                                                          
Building dependency tree                                                                                                               
Reading state information... Done                                                                                                      
The following packages have been kept back:                                                                                            
  linux-headers-server linux-image-server linux-server                                                                                 
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

If the upgrade would require another package to be deleted, or a new package to be installed, the package will be "kept back." As the man page for apt-get upgrade explains:

    Packages currently installed with new versions available are retrieved and upgraded; under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed.

To get past this, you can do

**sudo apt-get --with-new-pkgs upgrade**

This allows new packages to be installed. It will let you know what packages would be installed and prompt you before actually doing the install.

Source: http://unix.stackexchange.com/a/241062/186330

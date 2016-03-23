# Fix File Content Permissions

##### Make sure the Files directory is owned by the proper user and group - navigate to the Drupal *files* directory...
```
chown -R :www-data files
```
This will recursively set the group owner as the Apache user.

##### From /sites/default, we'll modify the permissions on the files directory:
```
chmod g+ws files
```
Notice that we didn't recursively modify the permissions. This will happen later. For now, we're just giving the Files directory a permission set that should look like this ("ls -al" is your friend): drwxrwsr-x

This will allow the user (you) and the group (Apache) the ability to read/write within Files. *The "s" makes the directory sticky, so that any files within will inherit the read/write access automatically.*

If this is a new Files directory and doesn't yet have anything in it, you're done. Otherwise, keep reading...
Fixing the permissions of pre-existing files in the Files directory

The Files directory is now set up correctly, but all of the files are still inaccessible, or perhaps do not allow write access by Apache. You might be fooled into thinking that things are done, as you should be able to successfully upload files. However, if you want to modify or delete something that already exists, you may not be able to without performing the following steps...

##### Navigate to /sites/default/files - Issue the following command to adjust directory permissions:

```
find . -type d -exec chmod g+ws {} \;
```

This will recursively give all directories read/write/sticky (just like the permission you already applied to the files directory).

##### Issue the following command to adjust file permissions:

```
find . -type f -exec chmod 664 {} \;
```

This will recursively give all files read/write by user/group, and read to anonymous (e.g. world).

And you're done! The files directory should now be operating smoothly.

Source: http://bridgecitystudio.com/tutorials/fixing-permissions-files-directory-drupal

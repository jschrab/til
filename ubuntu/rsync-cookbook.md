# RSYNC Cookbook

Basic sync of Drupal content files

rsync --verbose --progress --stats --recursive --times -perms --links --delete --checksum --dry-run  -e ssh sourcedomain.com:/var/www/vhosts/mydocument-root/httpdocs/sites/default/files/ ~/Vagrant/mydocument-root/sites/default/files

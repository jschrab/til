# Careful About /var/cache

If you don't have proper permissions on the var/ folders, Magento can write its cache information to the system /tmp folder.

This can lead to a situation where you've changed the base URLs in the Magento database, cleared cache (manual deletion of all mage-?? folders in var/cache), (cleared APC cache if you're running the op-code cache), (manually disabled the compiler (1.4.x.x and later)) and the system still looks for the original site.

Most people who own their own server discover that the site magically starts working after fixing, clearing and resetting permissions and then rebooting the server. The server reboot clears /tmp of the Magento cache files and Magento finally starts looking at its own configuration to find where it's located.

Source: https://stackoverflow.com/questions/8940458/cant-change-magento-base-url-stuck-in-cache/8947825#8947825

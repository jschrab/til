# Disable Software Update Notification 'Red dot' on Dock

```bash
defaults write com.apple.systempreferences AttentionPrefBundleIDs 0
killall Dock
```
Source: https://apple.stackexchange.com/questions/344278/how-can-i-disable-the-red-software-update-notification-bubble-on-the-system-pref

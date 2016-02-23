### PHP Performance Tweaks - Pt.1

Recommendations for realpath cache settings, particularly for large app sites using Drupal or Magento:
```
realpath_cache_size = 64k
realpath_cache_ttl = 3600
```

Source - http://haydenjames.io/set-monitor-phps-realpath_cache_size-correctly/

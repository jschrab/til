### Increase File Upload Limit

Out of the box IIS has a limit of ~30MB for file uploads, which may not be enough for large PDF's (for example). This can be changed.

```
<system.webServer>
...
<security>
    <requestFiltering>
        <requestLimits maxAllowedContentLength="2147483648"/>
    </requestFiltering>
</security>
...
</system.webServer>
```

Source: https://devnet.kentico.com/articles/file-upload-limitation-on-iis6-7

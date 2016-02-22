### Extract a video id from a wide variety of YouTube URLs

```regex
/^.*(youtu.be\/|v\/|u\/\w\/|embed\/|watch\?v=|\&v=)([^#\&\?]*).*/
```

...will extra a video id (v=<videoid>) from a YouTube URL. Cases covered...
* Protocol indifferent
* **youtube.com** or **youtu.be** shortened
* **embed** or **watch**
* Ignore query string parameters beyond **v**

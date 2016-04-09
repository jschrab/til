### FFMPG Conversion Crash Course

Transition a .MOV video from MOV to MP4. Keep h.264 video as-is, transition audio from "something else" to AAC, 256k-bitrate.

```
ffmpeg -i my-mov-movie.mov -c:v copy -c:a aac -b:a 256k my-mp4-movie.mp4
```

Source: https://trac.ffmpeg.org/wiki/Encode/AAC

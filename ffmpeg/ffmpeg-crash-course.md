### FFMPG Conversion Crash Course

Transition a .MOV video from MOV to MP4. Keep h.264 video as-is without transcoding, transition audio from "something else" to AAC, 256k-bitrate.

```
ffmpeg -i my-mov-movie.mov -c:v copy -c:a aac -b:a 256k my-mp4-movie.mp4
```

Source: https://trac.ffmpeg.org/wiki/Encode/AAC

Transition the audio track of a .mp4 to AAC but keep the video track as-is. Some players do not care for MP3 audio tracks inside of MP4 containers.

```
ffmpeg -i input.mp4 -vcodec copy -acodec aac -strict experimental -ac 2 -ar 44100 -ab 192k output.mp4
```

Source: http://superuser.com/a/331727

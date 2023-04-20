# ffmpeg command lines

## 1. Create PowerPoint compatible h264 file

        ffmpeg -i input%03d0.png -vcodec h264 -vprofile main -vf "scale=2*trunc(iw/2):-2,setsar=1" -pix_fmt yuv420p -an output.mp4
  
## ffmpeg Download links

https://www.gyan.dev/ffmpeg/builds/

https://github.com/BtbN/FFmpeg-Builds/releases

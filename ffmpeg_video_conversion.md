# FFmpeg

Extract from https://www.ffmpeg.org/about.html

FFmpeg is the leading multimedia framework, able to decode, encode, transcode, mux, demux, stream, filter, and play pretty much anything that humans and machines have created. It supports the most obscure ancient formats up to the cutting edge. No matter if some standards committee, the community or a corporation designed them. It is also highly portable: FFmpeg compiles, runs, and passes our testing infrastructure FATE across Linux, Mac OS X, Microsoft Windows, the BSDs, Solaris, etc. under various build environments, machine architectures, and configurations.

## Download links

https://www.gyan.dev/ffmpeg/builds/

https://github.com/BtbN/FFmpeg-Builds/releases

##  FFmpeg command lines

### Create PowerPoint compatible h264 file

        ffmpeg -i input%03d0.png -vcodec h264 -vprofile main -vf "scale=2*trunc(iw/2):-2,setsar=1" -pix_fmt yuv420p -an output.mp4
  

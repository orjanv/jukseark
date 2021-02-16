# avconv/ffmpeg

## Flip a video 90 degrees clockwise
    avconv -i in.mp4 -vf "transpose=1" -strict -2 out.mp4

## Use ffmpeg to create a video of a picture and a sound file
    ffmpeg -loop 1 -i image.jpg -i audio.wav -c:v libx264 -tune stillimage -c:a aac -strict experimental -b:a 192k -pix_fmt yuv420p -shortest out.mp4

## convert a video to gif using ffmpeg and gifsicle
    ffmpeg -i in.mov -s 600x400 -pix_fmt rgb24 -r 10 -f gif - | gifsicle --optimize=3 --delay=3 > out.gif

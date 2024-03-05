# avconv/ffmpeg

## Flip a video 90 degrees clockwise
    avconv -i in.mp4 -vf "transpose=1" -strict -2 out.mp4

## Use ffmpeg to create a video of a picture and a sound file
    ffmpeg -loop 1 -i image.jpg -i audio.wav -c:v libx264 -tune stillimage -c:a aac -strict experimental -b:a 192k -pix_fmt yuv420p -shortest out.mp4

## convert a video to gif using ffmpeg and gifsicle
    ffmpeg -i in.mov -s 600x400 -pix_fmt rgb24 -r 10 -f gif - | gifsicle --optimize=3 --delay=3 > out.gif

## Faster video speed
    ffmpeg -i input.mp4 -filter:v "setpts=0.5*PTS" output.mp4

## Slower Video Speed
    ffmpeg -i input.mp4 -filter:v "setpts=2*PTS" output.mp4

## You remove audio by using the -an flag.
    ffmpeg -i $input_file -c copy -an $output_file



## Video to GIF
   SET filters="fps=%4,scale=%3:-1:flags=lanczos"
   ffmpeg -v warning -i %1 -vf "%filters%,palettegen" -y palette.png
   ffmpeg -v warning -i %1 -i palette.png -lavfi "%filters% \[x\]; \[x\]\[1:v\] paletteuse" -y %2
   DEL palette.png

   togif.bat <input.mp4> <output.gif> <width> <fps>

## Extract audio from a video
   ffmpeg -i "path\to\my_input_video_file.mp4" "path\to\my_output_audio_only.wav"

## Extract specific video and audio stream
   ffmpeg -i "path\to\my_input_video_file.mp4" -map 0:0 -c copy video.mp4 -map 0:1 -c copy audio0.m4a -map 0:2 -c copy audio1.m4a

## Concatenate two or more video clips
   (echo file 'first file.mp4' & echo file 'second file.mp4' )>list.txt
   ffmpeg -safe 0 -f concat -i list.txt -c copy output.mp4

## Convert 10-bit H.265 to 10-bit H.264
   ffmpeg -i input -c:v libx264 -crf 18 -c:a copy output.mkv

## Convert 10-bit H.265 to 8-bit H.265
   ffmpeg -i input -c:v libx265 -vf format=yuv420p -c:a copy output.mkv

## Convert 10-bit H.265 to 8-bit H.264
   ffmpeg -i input -c:v libx264 -crf 18 -vf format=yuv420p -c:a copy output.mkv

## Convert multiple .webm audio files to .mp3 in one go
   find -name "*.webm" -exec ffmpeg -i {} -acodec libmp3lame -ab 128k {}.mp3 \;

## Convert a series of .jpg-files into a video with a given quality and framerate
   ffmpeg -framerate 15 -pattern_type glob -i 'DSC*.JPG' -s 1920x1080 -c:v libx264 -crf 20 -pix_fmt yuv420p aurora-30112021-up-15fps.mp4

# Imagemagick

## Resize all .png-images
    for f in *.png; do convert $f -resize 1000x900 1000px_$f; done

## Create a video from a set of images
    ffmpeg -pattern_type glob -i '*.jpg' -pix_fmt yuv420p out.mp4

## Make a collage of images with five columns and fill automatically numbers of rows
    montage -geometry +0+0 -tile 5x *.jpg result.jpg
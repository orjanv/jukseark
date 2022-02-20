# Imagemagick

## Resize all .png-images
    for f in *.png; do convert $f -resize 1000x900 1000px_$f; done

## Create a video from a set of images
    ffmpeg -pattern_type glob -i '*.jpg' -pix_fmt yuv420p out.mp4

## Make a collage of images with five columns and fill automatically numbers of rows
    montage -geometry +0+0 -tile 5x *.jpg result.jpg

## allow writing to PDF
    sudo sed -i_bak \
    's/rights="none" pattern="PDF"/rights="read | write" pattern="PDF"/' \
    /etc/ImageMagick-6/policy.xml

## Convert Single Page of PDF File to Image
To convert a single page of PDF to image, use the following command:

    convert -density 150 presentation.pdf[0] -quality 90 test.jpg

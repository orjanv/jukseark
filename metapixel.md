## LAge digre kollasjer basert på et bilde

### Prepare existing images

    metapixel-prepare -r sourcefolder destinationfolder --width=48 --height=48

## Create a mosaic

    metapixel --metapixel input.jpg output.png -l destinationfolder -s 10

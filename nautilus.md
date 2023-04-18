## scripts for nautilus

Place the bash-files in this folder: ~/.local/share/nautilus/scripts/


### convert multiple eps files to png

multiple_eps_to_png.sh 

    #!/bin/bash
    # Converts multiple .eps files into .png

    # Ask for the name of the subfolder to place the resized images in
    subfolder=$(zenity --entry --text "Enter the name of the subfolder to place the converted images in:")

    # Create the subfolder if it doesn't exist
    if [ ! -d "$subfolder" ]; then
        mkdir "$subfolder"
    fi

    # Read the selected file paths into an array
    filepaths=("${@}")

    # Iterate over the selected files
    for filepath in "${filepaths[@]}"; do
        # Check if the selected file is an image
        if [[ "$(file -b --mime-type "$filepath")" == application/postscript ]]; then
            # Get the filename without the extension
            filename=$(basename "$filepath" | sed 's/\.[^.]*$//')
            # Convert the filename to lowercase
            filename=$(echo "$filename" | tr '[:upper:]' '[:lower:]')
            # Resize the image using convert
            convert "$filepath" -colorspace sRGB -density 150 -flatten "$subfolder/$filename.png"
        fi
    done


### resize multiple images to 1920px

resize_multiple_images.sh 

    #!/bin/bash
    # Resizes selected images to 1920 pixels wide using convert

    # Ask for the name of the subfolder to place the resized images in
    subfolder=$(zenity --entry --text "Enter the name of the subfolder to place the resized images in:")

    # Create the subfolder if it doesn't exist
    if [ ! -d "$subfolder" ]; then
        mkdir "$subfolder"
    fi

    # Read the selected file paths into an array
    filepaths=("${@}")

    # Iterate over the selected files
    for filepath in "${filepaths[@]}"; do
        # Check if the selected file is an image
        if [[ "$(file -b --mime-type "$filepath")" == image/* ]]; then
            # Get the filename without the extension
            filename=$(basename "$filepath" | sed 's/\.[^.]*$//')
            # Convert the filename to lowercase
            filename=$(echo "$filename" | tr '[:upper:]' '[:lower:]')
            # Resize the image using convert
            convert "$filepath" -resize 1920 "$subfolder/$filename.resized.jpg"
            # Rename the original file with a suffix indicating that it has been resized
            mv "$filepath" "$filename.original.jpg"
        fi
    done



### resize a single image to 1920px

1920_convert.sh 

    #!/bin/bash
    # Resizes an image to 1920 pixels wide using convert

    # Get the path of the selected file
    filepath="$PWD/$1"

    # Check if the selected file is an image
    if [[ "$(file -b --mime-type "$filepath")" == image/* ]]; then
        # Get the filename without the extension
        filename=$(basename "$filepath" | sed 's/\.[^.]*$//')
        # Convert the filename to lowercase
        filename=$(echo "$filename" | tr '[:upper:]' '[:lower:]')
        # Resize the image using convert
        convert "$filepath" -resize 1920 "$filename.resized.jpg"
        # Rename the original file with a suffix indicating that it has been resized
        mv "$filepath" "$filename.original.jpg"
        # Rename the resized file with the original filename and extension
        mimetype=$(mimetype -b "$filepath")
        mv "$filename.resized.jpg" "$filename.resized.${mimetype##*/}"
    fi


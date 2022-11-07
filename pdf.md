## gs or ps2pdf

    /ebook gives a good balanced reduce

### Compress PDF-files

    gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/ebook -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

### Compress PDF-files

    ps2pdf -dPDFSETTINGS=/ebook input.pdf output.pdf

### Unite/Combine multiple PDFs into one

    pdfunite in-1.pdf in-2.pdf in-n.pdf out.pdf


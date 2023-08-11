## Install command line tool pdftoppm

To use the `pdftoppm` command-line tool, you need to first install `pdftoppm` which is a part of the poppler / poppler-utils / poppler-tools package. Install this package as follows depending on your Linux distribution

On Debian/Ubuntu & Mint

```bash
sudo apt install poppler-utils
```

On RHEL/CentOS & Fedora

```bash
sudo dnf install poppler-utils
```

On OpenSUSE

```bash
sudo zypper install poppler-tools
```

On Arch Linux]

```bash
sudo pacman -S poppler
```

### Convert PDF Document to Image

```bash
pdftoppm -<image_format> <pdf_filename> <image_name>
```

[tecmint](https://www.tecmint.com/convert-pdf-to-image-in-linux-commandline/)

### Imagemagick for image to pdf

On Debian

```bash
sudo apt install imagemagick
```

On RHEL/CentOS & Fedora

```bash
sudo dnf install imagemagick
```

In that case, all you need is to edit the **policy.xml** file using an editor like vim.

```bash
sudo vim /etc/ImageMagick-6/policy.xml
```

Look for the line in the following example:
<policy domain="coder" rights="none" pattern="PDF" />
To fix the error, replace the rights from “none” to “read|write”

### To jpg to pdf

```bash
convert *.jpg all.pdf
```

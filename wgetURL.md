```bash
wget --mirror --convert-links --adjust-extension --page-requisites --no-parent [URL]
```
Where:

- `--mirror` tells wget to download the entire website recursively.
- `--convert-links` converts links so that they work locally.
- `--adjust-extension` adds suitable extensions to filenames.
- `--page-requisites` downloads all the necessary files for a complete webpage.
- `--no-parent` tells wget not to ascend to the parent directory when downloading recursively.

Replace `[URL]` with the URL of the website you want to download.

## Change file/folder permission/ownership in Linux

How to change file/folder ownership?

```bash
sudo chown -R owner /
```

How to change file/folder permission like read/write/execute?

```bash
sudo chmod owner /
```

tips

- `-R` used for recursvely used for sub-directory
- owner like `root/$USER`
- / => your file location.

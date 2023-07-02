## ifuse basic command

### unmount your iphone when you have mount

```bash
fusermount -u ~/iPhone
```

### view that share file in your iPhone

```bash
ifuse --list-apps
```

### mount documents in iPhone directory

```bash
ifuse --documents com.spotify.client ~/iPhone
```

This command mount virtual space share by install application to view what application `ifuse --list-apps` and see their package name `com.spotify.client`

### if want mount all your iPhone directory

```bash
ifuse ~/iPhone/
```

##### Oh i forget your should make iPhone folder on home folder

```bash
mkdir iPhone
```

## ifuse basic for file transfer file between your linux machince and iPhone

### unmount your iPhone when you have mount

```bash
fusermount -u ~/iPhone
```

### view that share virtual space in your iPhone by application

```bash
ifuse --list-apps
```

### mount documents in iPhone directory

## in this example using Spotify `<appid>`

```bash
ifuse --documents com.spotify.client ~/iPhone
```

This command mount virtual space share by install application to view what application `ifuse --list-apps` and see their <appid> package name `com.spotify.client`

### if want mount all your iPhone directory

```bash
ifuse ~/iPhone/
```

##### Oh i forget your should make iPhone folder on home folder before using upper command directly

```bash
mkdir iPhone
```

check source code
[ifuse](https://github.com/libimobiledevice/ifuse)

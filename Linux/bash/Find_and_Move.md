# Find and Move

You can use the find command to recursively search for certain files in a directory and its subdirectories, and then use

or execution another command.

- `find`: This is the command used to search for files and directories.
- `/path/to/directory`: Replace this with the actual path to the directory where you want to start the search. This can be any directory on your system.
- `-type f`: This option specifies that we're only interested in regular files.
- `-name "*.jpg"`: This option specifies that we're searching for files with the extension `.jpg`.
- `-exec`: This option allows us to execute a command on each file found.
- `mv {} ~/`: This is the command that moves each file found (represented by `{}`) to the home directory (`~/`).

## Example:

```bash
find /path/to/directory -type f -name "*.jpg" -exec mv {} ~/ \;
```

### OR for current directory.

```bash
find . -type f -name "*.xml" -exec mv {} ~/ \;
```

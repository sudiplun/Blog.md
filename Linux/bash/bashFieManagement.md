## How to Remove a Directory in Linux

To permanently remove a directory in Linux, use either **rmdir** or **rm** command:

- For empty directories, use **`rmdir [dirname]`** or **`rm -d [dirname]`**
- For non-empty directories, use `rm -r [dirname]`

Before you remove a directory, you need to know the name of it. To discover files and directories, use the **ls** command, and to know the current directory you are in, use the **pwd** command.

|                        |                                                                     |
| ---------------------- | ------------------------------------------------------------------- |
| **Command and Option** | **Description**                                                     |
| rm -d                  | Remove an empty directory using the **rm** command.                 |
| rm -r                  | Remove a non-empty directory and its content.                       |
| rm -f                  | Ignore any prompt when deleting a write-protected file.             |
| rm -rf                 | Ignore any prompt when deleting a write-protected non-empty folder. |
| rm -i                  | Output a prompt before deleting every file.                         |
| rm -I                  | Output a prompt only once before deleting more than three files.    |
| rm \*                  | Wildcard that represents multiple characters.                       |
| rm ?                   | Wildcard that represents a single character.                        |
| rmdir -p               | Remove an empty subdirectory and its parent directory.              |
| rmdir -v               | Print the information that the specified directory was deleted.     |

### How to Remove an Empty Directory (rmdir Command)

In the Linux environment, files and directories will be permanently deleted as there’s no recycle bin or trash folder where you can retrieve them. If you delete a file or directory in Linux by mistake, the only way to recover it is from a backup.

Using the **rmdir** command prevents such unwanted actions as it only works for empty directories. It will return the following error message if the directory contains files:

rmdir: failed to remove ‘Directory’: Directory not empty

`rmdir: failed to remove ‘Directory’: Directory not empty`

The syntax for the **rmdir** command is as follows:

rmdir [option] DirectoryName

`rmdir [option] DirectoryName`

If you don’t want to use any command line option, remove it from the syntax. Remember that the command line is case-sensitive. Therefore, if the folder name contains uppercase letters, type it accordingly.

For example, here’s a command for deleting the **Simple-Directory** folder:

rmdir Simple-Directory

`rmdir Simple-Directory`

The **rmdir** command also works for multiple empty directories. Add the directories in the command as additional arguments to delete multiple directories in Linux.

rmdir Directory_1 Directory_2 Directory_3

`rmdir Directory_1 Directory_2 Directory_3`

Now let’s see options you can use with the **rmdir** command. The first one is **-p,** which works for deleting a subdirectory and its parent directory. For example, if your directory path is **/Directory/SubDirectory**, use the following command:

rmdir -p /Directory/SubDirectory

`rmdir -p /Directory/SubDirectory`

This command will delete the **SubDirectory** folder in the **Directory** path first. Then, if the **Directory** folder is empty after the **SubDirectory** was removed, the folder will also get deleted.

The next option is **verbose**, represented with **-v** in the command line. This option will print a text as a confirmation that the specified directory has been deleted. Here’s an example of this command:

rmdir -v Simple-Directory

`rmdir -v Simple-Directory`

The output message will be like this:

rmdir: removing directory, ‘Simple-Directory’

`rmdir: removing directory, ‘Simple-Directory’`

### How to Remove a Non-Empty Directory (rm Command)

Now let’s see how to remove non-empty directories using the **rm** command. This command is originally used to remove files, but we can use it to remove directories using options like **-r**, **-rf**, and **-d**. The basic syntax for the **rm** command is as follows:

rm [option] FileOrFolderName

`rm [option] FileOrFolderName`

Use a **recursive** option, represented by **-r**, to remove the directory and its content. The following command shows how to delete **Simple-Directory** and its content:

rm -r Simple-Directory

`rm -r Simple-Directory`

**Warning!** If you delete a non-empty directory using the **rm -r** command, all the files inside it will be permanently deleted, and you can only recover them from a backup. Execute this command with caution.

If the directory is write-protected, you will be prompted to confirm before proceeding with the directory removal. To delete a directory without being prompted, use the **-rf** option.

rm -rf Simple-Directory

`rm -rf Simple-Directory`

The **rm** command also works for removing empty directories in Linux. However, unlike the **rmdir** command, you have to use the **-d** option.

rm -d Simple-Directory

`rm -d Simple-Directory`

Just as with the **rmdir** command, you can use the **rm** command to remove multiple directories. Add directory names as new arguments in the command line:

rm -r Directory_1 Directory_2 Directory_3

`rm -r Directory_1 Directory_2 Directory_3`

## How to Delete a File With the rm Command

You may want to use the **rm** command to manually remove files instead of deleting a non-empty folder straight away. This method is safer as it prevents removing important files accidentally.

To delete a single file in the current working directory, use the **rm** command followed by the file name:

rm file.txt

`rm file.txt`

To delete multiple files in the directory, write all the file names you want to delete in the command:

rm file1.txt file2.txt file3.txt

`rm file1.txt file2.txt file3.txt`

All the commands above work if you are in the same directory as the specified files. However, you can put the file path into the command line argument to delete a file that’s not in your current working directory.

rm dir/subdir/file.txt

`rm dir/subdir/file.txt`

Since the files will be permanently removed, you can add the **-i** option in the command to make the terminal prompt you to confirm every file deletion. This way, you prevent unpleasant mistakes from happening.

rm -i file1.txt file2.txt file3.txt

`rm -i file1.txt file2.txt file3.txt`

Type **Y** and press **Enter** if you want to delete the file, or type **N** and press **Enter** if you don’t.

Use **-I** instead to get prompted only once before deleting more than three files. While this is less safe than the **-i** option, it still gives extra protection to avoid deleting important files.

rm -I file1.txt file2.txt file3.txt

`rm -I file1.txt file2.txt file3.txt`

However, the system will prompt you anyway before removing files if they’re write-protected. If you don’t want to get prompted when deleting such files, use the **-f** option.

rm -f file.txt

`rm -f file.txt`

The commands we’ve discussed so far will delete specific files. However, using wildcards, you can delete multiple files with a single command. There are two types of wildcards – the asterisk (**\***) and the question mark (**?**).

The asterisk represents multiple unknown characters, and one of the most common use examples is deleting files with a certain extension. The command below will delete all **.txt** files in the current working directory:

rm \*.txt

`rm *.txt`

You can also use the asterisk to delete all files beginning with a specific letter.

rm a\*

`rm a*`

In the example above, the asterisk represents all unknown characters that come after the letter **a**. The command will delete all files beginning with **a** regardless of their extensions, such as **amazon.txt**, **alligator.png**, and **aaron.zip**.

The question mark wildcard, on the other hand, represents a single character. In conjunction with the asterisk wildcard, you can use it to delete files with a single character extension, such as **.S**, **.O**, and **.C**.

rm \*.?

`rm *.?`

**Warning!** Be careful when using wildcards, as you may end up deleting important files. First, check all the files in the directory using the **ls** command. Make sure that there are no important data or system files before using the wildcard command.

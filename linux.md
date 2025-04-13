# 🐧Linux commands 🐧
## Compress a folder using bzip2
To compress a folder using bzip2, you'll first need to create a tarball (.tar file) of the folder and then compress it with bzip2. You can use the following command:
```
tar -cvjf folder_name.tar.bz2 folder_name/
```
## Explanation:
    tar: The command to create and manipulate tar archives.
    -c: Create a new archive.
    -v: Verbose mode, showing the files being processed.
    -j: Use bzip2 compression.
    -f: Specify the name of the output file (folder_name.tar.bz2).
    folder_name/: The folder you want to compress.
This will create a compressed .tar.bz2 file of your folder.

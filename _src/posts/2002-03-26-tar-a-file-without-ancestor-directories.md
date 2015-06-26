    Title: tar a file without ancestor directories
    Date: 2002-03-26T16:51:15
    Tags: bash, command

`tar` command may generate a file with unnecessary ancestor directories. use `C` option to remain the file only:

```bash
$ tar -czf xi.tar.gz -C /one/two/three/xi .
```

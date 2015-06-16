    Title: 在github上使用frog博客引擎
    Date: 2015-06-15T22:54:40
    Tags: 教程, racket, frog, 博客

1. 制作用于访问github的ssh密钥
    1. 查看.ssh已有密钥
```bash
$ ls -al ~/.ssh
```
  若使用已有密钥，则忽略xxx。
    2. 制作新ssh密钥
```bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
Enter file in which to save the key (/Users/you/.ssh/id_rsa): [press enter]
Enter passphrase (empty for no passphrase): [type a passphrase]
# Enter same passphrase again: [type passphrase again]
```
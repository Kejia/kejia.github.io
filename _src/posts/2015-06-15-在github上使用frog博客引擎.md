    Title: 在github上使用frog博客引擎
    Date: 2015-06-15T22:54:40
    Tags: 教程, racket, frog, 博客

1.  制作用于访问github的ssh密钥

refer to: https://help.github.com/articles/generating-ssh-keys/

1.1 查看.ssh已有密钥

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
3. check whether ssh-agent is running

```bash
$ eval "$(ssh-agent -s)"
# Agent pid 59566
```

4. add my key to ssh-agent

```bash
$ ssh-add ~/.ssh/id_rsa
```

5. copy pub key

```bash
$ xclip -sel clip < ~/.ssh/id_rsa.pub
```

6. copy the key to github

settings > add ssh key

7. test

```bash
$ ssh -T git@github.com
```

# set up github user page

refer to: https://www.thinkful.com/learn/a-guide-to-using-github-pages/start/new-project/user-page/

1. create the user page repo

repo name must be: username.github.io

# create frog

refer to: https://github.com/greghendershott/frog

1. clone github user page repo

```bash
$ mkdir frog
$ cd frog
$ git clone https://github.com/username/username.github.io.git
```

2. install frog

```bash
$ raco pkg install frog
$ raco pkg update --update-deps frog
$ aptitude install python-pygments
$ aptitude install python3-pygments
```

3. create the frog project

```bash
$ cd username.github.io
$ raco frog --init
```

4.  create a post

```bash
$ raco frog -n "My Post Title"
```

5. preview

```bash
$ raco frog -bp
```

6. deploy to github

```bash
$ raco frog -b
$ git add .
$ git commit -m 'post my blog'
$ git push origin master
```
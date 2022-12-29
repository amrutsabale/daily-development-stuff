#### to abort running git pull

```
git merge --abort
```

#### git pull without rebase

```
git pull origin master --no-rebase
```

#### open git config file

```
open ~/.gitconfig
```

#### set default merge strategy

```
1. "open git config file"
2. "and set"
   [branch]
   autosetuprebase = always
```

#### add alias to terminal

```
1. vim ~/.zshrc
2. add this line
   alias c="clear"
3. exit the vim
4. save using this command
   source ~/.zshrc
```

#### add alias to git

```
1.  vim ~/.gitconfig
2.  add alias here
    [alias]
    co = checkout
    cm = commit -m
    s = status
    st = stash
    sta = stash apply
    l = log
    ps = push
    pl = pull
    aa = add .
3.  exit the vim
```

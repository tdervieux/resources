# Markdown Syntax
[Check this link for complete markdown syntax](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

# Git 

### check the remote repo
```bash
> git remote 
origin
upstream
> git remote show // seems to be the same as git remove
```
### check the url of a specific repo
```csh
> git remote show origin
* remote origin
  Fetch URL: https://github.com/PixarAnimationStudios/OpenTimelineIO.git
  Push  URL: https://github.com/PixarAnimationStudios/OpenTimelineIO.git
  HEAD branch: master
  Remote branch:
    master tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
```
###create a ssh key
```
xclip -sel clip < ~/.ssh/id_dsa.pub
```
### add upstream repo
```csh
git remote add upstream git@github.com:PixarAnimationStudios/OpenTimelineIO.git
```

### merge with upstream/master
> git merge upstream/master


### visualize commit graph in the shell
```csh
> git log --oneline --graph --all
```

###update my repo from upstream
```csh
> git fetch upstream
```

### add a local repo
```csh
git remote add forked /home/tdervieux/tree/OpenTimelineIO
or
git remote add upstream git@github.com:PixarAnimationStudios/OpenTimelineIO.git
or
git remote add upstream https://github.com/PixarAnimationStudios/OpenTimelineIO.git
```


### rebase
```csh
[otio] > git rebase -i forked/master
```

### push a branch to a repo
```csh
git push forked otioviewerFeature
```

### visualize your git branches
```csh
> gitk --all
```
# houdini

# Python
## Create a virtual environment

1. cd to $VIRTUAL_ENV_ROOT
2. virtualenv my_env_name #(otio)
3. source my_env_name/bin/activate.csh
4. pip install -U pip
5. pip install -U setuptools
6. cd ~/otio_dir
7. pip install -e .
8. pip install PySide2==5.11.0
9. pip install -e .\[dev] #linter, mock library 
10. rehash; which otioview #should be pointing at your dir```

11.to turn it off: `deactivate`



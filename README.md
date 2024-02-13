# Skip The Search
## Useful commands, shortcuts, and alias to help speed up the dev process

Kill a locked process
```
sudo lsof -i :3000
kill -9 <PID>
```

Uninstall all pip packages
```
pip freeze > requirements.txt
pip uninstall -r requirements.txt -y
```

Search for a string in home directory (Mac)
```
grep -nrI "string to search" . --exclude-dir=Library
```

Delete branch locally
```
git branch -d localBranchName
```

List remote branches
```
git branch -r
```

Delete branch remotely
```
git fetch --prune
git push origin --delete remoteBranchName
```

[Transfer a file over ssh using scp](https://unix.stackexchange.com/a/188289)
```
scp -i permissionfile examplefile yourusername@remoteserver:/home/yourusername/
```

Getting list of startup applications in Linux
```
ls /etc/init.d
```

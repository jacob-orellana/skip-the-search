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
or
pip freeze | xargs pip uninstall -y
```

Search for a file in home directory (Mac)
```
find / -name "my_file.txt" 2>/dev/null
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

Transfer repository from Bitbucket to Github
```
cd repo-directory
git remote rename origin bitbucket
git remote add origin https://github.com/username/new-repo.git
git branch -M main
git push -u origin --all
git remote rm bitbucket
```

Remove the previously tracked files from the Git index/cache according to `.gitignore`.
```
git rm --cached $(git ls-files --exclude-from=.gitignore)
```

[Transfer a file over ssh using scp](https://unix.stackexchange.com/a/188289)
```
scp -i permissionfile examplefile yourusername@remoteserver:/home/yourusername/
```

Getting list of startup applications in Linux
```
ls /etc/init.d
```

View program taking up a specific port
```
lsof -i :8000
```

Change a user’s password via SQL
```
ALTER USER 'superuser'@'localhost' IDENTIFIED BY 'password'
FLUSH PRIVILEGES;
```

Get sizes for a specific directory
```
sudo du -h --max-depth=1 /path/to/directory
```

Kill a locked process
```bash
sudo lsof -i :3000
kill -9 <PID>
```

Uninstall all pip packages
```bash
pip freeze > requirements.txt
pip uninstall -r requirements.txt -y
or
pip freeze | xargs pip uninstall -y
```

Search for a file in home directory (Mac)
```bash
find / -name "my_file.txt" 2>/dev/null
```

Search for a string in home directory (Mac)
```bash
grep -nrI "string to search" . --exclude-dir=Library
```

Delete branch locally
```bash
git branch -d localBranchName
```

List remote branches
```bash
git branch -r
```

Delete branch remotely
```bash
git fetch --prune
git push origin --delete remoteBranchName
```

Transfer repository from Bitbucket to Github
```bash
cd repo-directory
git remote rename origin bitbucket
git remote add origin https://github.com/username/new-repo.git
git branch -M main
git push -u origin --all
git remote rm bitbucket
```

Untracks files listed in .gitignore — removes from index only, history unaffected
```bash
git rm --cached $(git ls-files --exclude-from=.gitignore)
```

[Transfer a file over ssh using scp](https://unix.stackexchange.com/a/188289)
```bash
scp -i permissionfile examplefile yourusername@remoteserver:/home/yourusername/
```

Getting list of startup applications in Linux
```bash
ls /etc/init.d
```

View program taking up a specific port
```bash
lsof -i :8000
```

Change a user’s password via SQL
```bash
ALTER USER 'superuser'@'localhost' IDENTIFIED BY 'password'
FLUSH PRIVILEGES;
```

Get sizes for a specific directory
```bash
sudo du -h --max-depth=1 /path/to/directory
```

Install if needed:  
⚠️ FYI git filter-repo ***removes the remote on purpose***  
It's a safety feature to stop you from accidentally force pushing rewritten history.  
```bash
pip install git-filter-repo 
brew install git-filter-repo 
```

Remove a specific file from entire history  
```bash
git filter-repo --path secret.env --invert-paths 
```

Remove by glob pattern  
```bash
git filter-repo --path-glob '*.env' --invert-paths
```

This one-liner reads each pattern from .gitignore and builds filter-repo args  
```bash
git filter-repo $(grep -v '^#' .gitignore | grep -v '^$' | sed 's/^/--path-glob /') --invert-paths --dry-run
git push origin --force --all
git push origin --force --tags
```

^That one-liner can be fragile with complex .gitignore files, so here's a more robust script  
```bash
args=() 
while IFS= read -r pattern; do 
	# Skip comments and empty lines 
	[[ "$pattern" =~ ^#.*$ || -z "$pattern" ]] && continue 
	# Trim whitespace 
	pattern=$(echo "$pattern" | xargs) 
	[ -z "$pattern" ] && continue 
	args+=(--path-glob "$pattern") 
done < .gitignore 

if [ ${#args[@]} -gt 0 ]; then 
	git filter-repo "${args[@]}" --invert-paths 
fi
```

Push rewritten history
```bash
git push origin --force --all
git push origin --force --tags
```


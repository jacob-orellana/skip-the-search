# Install if needed: 
# FYI git filter-repo **removes the remote on purpose**
# it's a safety feature to stop you from accidentally force pushing rewritten history.
pip install git-filter-repo 
brew install git-filter-repo 

# Remove a specific file from entire history  
git filter-repo --path secret.env --invert-paths 

# Remove by glob pattern 
git filter-repo --path-glob '*.env' --invert-paths

# This one-liner reads each pattern from .gitignore and builds filter-repo args 
git filter-repo $(grep -v '^#' .gitignore | grep -v '^$' | sed 's/^/--path-glob /') --invert-paths --dry-run
git push origin --force --all
git push origin --force --tags

# ^ That one-liner can be fragile with complex .gitignore files, so here's a more robust script
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

git push origin --force --all
git push origin --force --tags

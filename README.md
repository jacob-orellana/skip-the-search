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
grep -nrI "in_alert_state" . --exclude-dir=Library
```

# Skip The Search
## Useful commands, shortcuts, and alias to help speed up the dev process

Kill a locked process
`sudo lsof -i :3000`
`kill -9 <PID>`

Uninstall all pip packages
`pip list --format=freeze |xargs pip uninstall -y`

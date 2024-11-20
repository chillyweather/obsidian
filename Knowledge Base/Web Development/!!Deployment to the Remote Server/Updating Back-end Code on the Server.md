To update our code, we'll need to go to our project folder on the server and pull the latest changes from GitHub:

```bash
# Run this on the VM
git pull
```

After that, all that remains is to reboot PM2 for the changes to our back end to take effect:

```bash
# Run this on the VM
pm2 restart app
```
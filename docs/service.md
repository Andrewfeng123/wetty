## Run WeTTY as a service daemon

WeTTY can be run as a daemon using init.d or systemd.

### init.d

```bash
$ npm -g i wetty
$ sudo cp ~/.node_modules/wetty/conf/wetty.conf /etc/init
$ sudo start wetty
```

### systemd

A template unit file is provided at `conf/wetty.service.example`.

### systemd

```bash
sudo cp /path/to/wetty/conf/wetty.service.example /etc/systemd/system/wetty.service
# Edit WorkingDirectory and any ExecStart flags as needed
sudo systemctl daemon-reload
sudo systemctl enable --now wetty
```

This will start WeTTY on port 3000. Common `ExecStart` flags:

```
pnpm start -- --base=/ --port=3000 --ssh-host=hostname
```

Run as `User=root` to get a `/bin/login` prompt (any local user can log in). Run
as a non-root user to SSH to localhost as that user instead.

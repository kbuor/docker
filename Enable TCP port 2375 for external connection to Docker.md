## Enable TCP port 2375 for external connection to Docker
---
See this issue.
Docker best practise to Control and configure Docker with systemd.

> Create daemon.json file in `/etc/docker`:
```shell
{
 "debug": true,
 "hosts": ["tcp://172.168.192.102:2376", "unix:///var/run/docker.sock"]
}
```

> Add `/etc/systemd/system/docker.service.d/override.conf`

```shell
[Service]
ExecStart=
ExecStart=/usr/bin/dockerd
```

> Reload the systemd daemon:

```shell
 systemctl daemon-reload
```

> Restart docker:

```shell
 systemctl restart docker.service
```

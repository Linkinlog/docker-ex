# Docker Network test

# Usage

- Simply run `docker compose up -d` in both the root directory and the `service1` directory and then visit `docker.test`

*If you do not have a DNS rule pointing all `.test` traffic to `127.0.0.1` then you should, yet for this test adding the following entries to `/etc/hosts` will suffice.*
```bash
echo '127.0.0.1 docker.test'      | sudo tee -a /etc/hosts
```


# Key Areas

 - Uses Traefiks docker provider to find other services
     - Notably, this behaves oddly if on separate networks
 - Has suspiciously named networks
 - Currently works on some computers
 - Does not work on:
```bash
$ docker version

Client:
 Cloud integration: v1.0.35+desktop.13
 Version:           26.0.0
 API version:       1.45
 Go version:        go1.21.8
 Git commit:        2ae903e
 Built:             Wed Mar 20 15:14:46 2024
 OS/Arch:           darwin/arm64
 Context:           desktop-linux

Server: Docker Desktop 4.29.0 (145265)
 Engine:
  Version:          26.0.0
  API version:      1.45 (minimum version 1.24)
  Go version:       go1.21.8
  Git commit:       8b79278
  Built:            Wed Mar 20 15:18:02 2024
  OS/Arch:          linux/arm64
  Experimental:     false
 containerd:
  Version:          1.6.28
  GitCommit:        ae07eda36dd25f8a1b98dfbf587313b99c0190bb
 runc:
  Version:          1.1.12
  GitCommit:        v1.1.12-0-g51d5e94
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```

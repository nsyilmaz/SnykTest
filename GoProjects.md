# Snyk Test
## Go Security Test
Download modules to local cache
```sh
go mod download
```
Now you can run snyk test command.

SCA:
```sh
snyk test --strict-out-of-sync=false --show-vulnerable-paths=all  --all-projects
```
```sh
snyk test --file=go.mod
```

SAST:
```sh
snyk code test --strict-out-of-sync=false --show-vulnerable-paths=all  --all-projects
```
If modules used from private repos, authentication should be set in several configs.
1. Repo should be cloned via SSH
```sh
git@gitlab.com:Your-Org/Your-Repo.git
```
2. Following command should be run
```sh
git config --global url."git@gitlab.com:".insteadOf "https://gitlab.com/"
```
OR

following lines should be added to `~/.gitconfig` file
```sh
[url "git@gitlab.com:"]
        insteadOf = https://gitlab.com
```
3. Following lines should be added to `~/.netrc` file
```sh
machine gitlab.com
login UserName
password Gitlab-Private-Token
```

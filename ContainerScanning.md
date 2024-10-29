# Snyk Test
## Container Scanning
Directly scan public docker hub images
```sh
snyk container test node:20.18
```
You can scan images from other registries
```sh
snyk container test cgr.dev/chainguard/node:latest
```
Also from Gitlab registry
```sh
snyk container test registry.gitlab.com/Your-Org/application/payments:d283208c --username XXXXX --password XXXXX
```
You can also login to registry via docker and then scan the images.

Docker Login (put your Gitlab access token when prompted):
```sh
docker login   registry.gitlab.com/Your-Org  -u XXXXX
```
Scan Image:
```sh
snyk container test registry.gitlab.com/Your-Org/application/payments:d283208c
```
Docker Logout:
```sh
docker logout   registry.gitlab.com/Your-Org
```


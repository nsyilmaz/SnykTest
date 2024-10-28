# Snyk Security Test
## Node - npm - yarn Security Test
Access to directory with specific version of Node via docker

Node:18
```sh
docker run -ti  --name node-18  --rm  --workdir /app        -v $(pwd):/app/  -v ~/.ssh:/root/.ssh  node:18  /bin/sh
```
Node:20
```sh
docker run -ti  --name node-20-12-0 --rm  --workdir /app        -v $(pwd):/app/  -v ~/.ssh:/root/.ssh  node:20.12.0  /bin/sh
```
If required you can change npm to specific version (inside docker container)
```sh
npm install -g npm@9 
```
!!!In some cases you may need .npmrc file to install from authenticated packageurls!!!
Run package installation command inside docker container.
```sh
npm install
```
or
```sh
yarn install
```
Now you can run snyk test command outside docker, since docker accessed and installed the packaged in the same directory.

SCA:
```sh
snyk test --all-projects
```
SAST:
```sh
snyk code test --all-projects
```

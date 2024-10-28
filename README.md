# Package Managers
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

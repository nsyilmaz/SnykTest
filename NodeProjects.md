# Snyk Test
## Node - npm - yarn Security Test
Access to directory with specific version of Node via docker

Node:18
```sh
docker run -ti  --name node-18  --rm  --workdir /app      -v $(pwd):/app/  -v ~/.ssh:/root/.ssh  node:18  /bin/sh
```
Node:20
```sh
docker run -ti  --name node-20-12-0 --rm  --workdir /app      -v $(pwd):/app/  -v ~/.ssh:/root/.ssh  node:20.12.0  /bin/sh
```
If required you can change npm to specific version (inside docker container)
```sh
npm install -g npm@9 
```

Run package installation command inside docker container.
```sh
npm install
```
or
```sh
yarn install
```
If you need to upgrade only the vulnerale dependency:

e.g.: XXXXXXX@1.0.0 > del@5.1.0 > globby@10.0.2 > fast-glob@3.2.12 > micromatch@4.0.6 

Here the micromatch@4.0.6 is vulnerable and you are only able to upgrade micromatch to v4.0.8

If fast-glob@3.2.12 depends on "micromatch": "^4.0.7" (dependency version is used with carrot sign ^ , first check this: https://www.npmjs.com/package/fast-glob?activeTab=dependencies) you can use npm dedup.
```sh
npm i micromatch@4.0.8 --save-exact
```
```sh
npm dedup
```
Now you can run snyk test command outside docker, since docker accessed and installed the packaged in the same directory.

SCA:
```sh
snyk test --strict-out-of-sync=false --show-vulnerable-paths=all  --all-projects
```
SAST:
```sh
snyk code test --strict-out-of-sync=false --show-vulnerable-paths=all  --all-projects
```

!!!In some cases you may need .npmrc file to install modules from private repos or authenticated packageurls!!!
Copy following lines into `.npmrc` file.
```sh
@Your-Org:registry=https://gitlab.com/api/v4/packages/npm/
//gitlab.com/api/v4/packages/npm/:_authToken=Your-Gitlab-Token
```

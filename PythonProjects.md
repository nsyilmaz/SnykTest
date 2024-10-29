# Snyk Test
## Python - pip3 Security Test
Create a virtual environment for clean work

```sh
python3 -m venv .venv
source .venv/bin/activate
```
Install libraries in thiw environment
```sh
pip3 install -r requirements.txt
```
Now you can run snyk test command in virtual environment.

SCA:
```sh
snyk test  --file=requirements.txt --package-manager=pip
```
SAST:
```sh
snyk code test  --file=requirements.txt --package-manager=pip
```
Then, deactivate the virtual environment
```sh
deactivate
```

# Snyk Test
## Snyk Monitor (Using Dashboard)
If you want to monitor repo scanning on dashboard
```sh
snyk monitor --org=SnykOrgID 
```
You can also specify command for python projects
```sh
snyk monitor --org=SnykOrgID --command=python3 
```
You can also specify branch name
```sh
snyk monitor --org=SnykOrgID  --target-reference=YourBranchName
```

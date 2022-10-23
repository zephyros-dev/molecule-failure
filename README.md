# Description
- This repo is for reproducing the issue of having some task fail when molecule converge is run with docker-from-docker VSCode extension with amd64 image on Mac M1
# Steps to reproduce
1. Install and open VSCode
2. Install VSCode remote container extension (ms-vscode-remote.remote-containers)
3. Press F1 in VSCode container and search for `Dev Containers: Rebuild and Reopen in Container`
4. Run these commands to converge the roles inside the devcontainer:
```
cd test
molecule converge
```
# Expected results
- Converge should run successfully
# Actual results
- The APT update task will fail with the following error:
```
PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
ok: [instance]

TASK [Include role] ************************************************************

TASK [test : test] *************************************************************
fatal: [instance]: FAILED! => {"changed": false, "module_stderr": "", "module_stdout": "", "msg": "MODULE FAILURE\nSee stdout/stderr for the exact error", "rc": 0}

PLAY RECAP *********************************************************************
instance                   : ok=1    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0
```
# My personal Ansible Scripts

General Ansible Scripts

## Colection

### Windows

* [x] [Enable Remote Desktop](windows/enable_remote_desktop.yml)
* [x] [Install BloodHound v3.0.5](windows/bloodhound_v3.0.5.yaml)
* [x] [Install BloodHound v4.2.0](windows/bloodhound_v4.2.0.yaml)


## Installing (client)

```bash
pip install netaddr
ansible-galaxy collection install community.general
ansible-galaxy collection install ansible.posix
ansible-galaxy collection install ansible.windows
ansible-galaxy collection install community.windows
```

## Preparing Windows

Before run any ansible command run this commands bellow in a powershell

```powershell
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
Invoke-Expression ((New-Object System.Net.Webclient).DownloadString('https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1'))
```

## Executing

```bash
ip="10.10.10.10"; # Windows/Linux server IP
ansible-playbook -i $ip, script.yml
```

## Common error (MacOS Client)

```
objc[7453]: +[__NSCFConstantString initialize] may have been in progress in another thread when fork() was called.
objc[7453]: +[__NSCFConstantString initialize] may have been in progress in another thread when fork() was called. We cannot safely call it or ignore it in the fork() child process. Crashing instead. Set a breakpoint on objc_initializeAfterForkError to debug.
```

To solve this error run
```bash
export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES
```

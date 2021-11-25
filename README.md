# wsl-setup

Description of the setup of the WSL distro for my development.

## Configure WSL under Windows

Enable Windows subsystem for Linux:

```powershell
Enable-WindowsOptionalFeature -Online -NoRestart -FeatureName Microsoft-Windows-Subsystem-Linux
Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform -NoRestart
```

Enable version 2 of WSL:

```cmd
Invoke-WebRequest https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi -OutFile D:\dat\WSL\wsl_update_x64.msi -UseBasicParsing
Invoke-WebRequest https://... -OutFile D:\dat\WSL\kernel\vmlinux -UseBasicParsing
start D:\dat\WSL\wsl_update_x64.msi
wsl --set-default-version 2
```

Configure non-default kernel in `%USERPROFILE%\.wslconfig`:

```
[wsl2]
kernel=D:\\dat\\WSL\\kernel\\vmlinux
```

## Install Ubuntu as base distro

```powershell
Invoke-WebRequest -Uri http://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64-wsl.rootfs.tar.gz -OutFile focal-server-cloudimg-amd64-wsl.rootfs.tar.gz -UseBasicParsing
wsl --import DPurge D:\dat\WSL\DPurge focal-server-cloudimg-amd64-wsl.rootfs.tar.gz
wsl --set-version DPurge 2
wsl --setdefault DPurge
```

If you need to unregister it:

```powershell
wsl --unregister DPurge
```


<div align="center">
  <a href="https://learn.microsoft.com/en-us/windows/wsl/"><img src="https://github.com/vishnu1002/cmd-help/assets/145321614/b3d331db-c7cb-4caf-ac1a-187a46ab647b"></a>
</div>


Windows Subsystem for Linux (WSL) is a feature of Windows that allows you to run a Linux environment on your Windows machine, without the need for a separate virtual machine or dual booting. WSL is designed to provide a seamless and productive experience for developers who want to use both Windows and Linux at the same time.

## WSL2 Setup via Command Line
You can install WSL2 directly from the command line (cmd or PowerShell) on Windows 10 (2004+) and Windows 11:

```sh
wsl --install
```

To install a specific distro (e.g., Ubuntu):
```sh
wsl --install -d Ubuntu-20.04
```

## Listing Available (Online) Distros
List all Linux distros available for install from Microsoft:
```sh
wsl --list --online
# or
wsl -l -o
```

## Listing Installed Distros
Show all distros currently installed on your system:
```sh
wsl --list --verbose
# or
wsl -l -v
```

## Removing/Unregistering a Distro
This will completely remove a distro and all its data:
```sh
wsl --unregister <DistroName>
```
Example:
```sh
wsl --unregister Ubuntu-20.04
```

## Other Useful WSL Commands
- Update WSL:
  ```sh
  wsl --update
  ```
- Set default distro:
  ```sh
  wsl --set-default <DistroName>
  ```
- Launch a specific distro:
  ```sh
  wsl -d <DistroName>
  ```
- Export a distro to a tar file:
  ```sh
  wsl --export <DistroName> <FileName.tar>
  ```
- Import a distro from a tar file:
  ```sh
  wsl --import <DistroName> <InstallLocation> <FileName.tar>
  ```
- Shutdown all running WSL instances:
  ```sh
  wsl --shutdown
  ``` 

<div align="center">
  <a href="https://learn.microsoft.com/en-us/windows/wsl/"><img src="https://github.com/vishnu1002/cmd-help/assets/145321614/b3d331db-c7cb-4caf-ac1a-187a46ab647b"></a>
</div>


Windows Subsystem for Linux (WSL) is a feature of Windows that allows you to run a Linux environment on your Windows machine, without the need for a separate virtual machine or dual booting. WSL is designed to provide a seamless and productive experience for developers who want to use both Windows and Linux at the same time.

## WSL2 Setup
1. Open `Windows features on or off`
2. Check the following options
	- Virtual Machine Platform
	- Windows Hypervisor Platform
	- Windows Subsystem for Linux
3. Apply and restart
4. Update WSL2 kernal. [WSL2 Linux kernal update package](https://learn.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package)
5. Download Ubuntu [Microsoft Store](https://apps.microsoft.com/detail/9pdxgncfsczv?hl=en-us&gl=US)

## Verify Installation
1. Open cmd and run the following commands
```
wsl --status
wsl --update
wsl
```
2. Mount other drives
```
cd /mnt/<drive letter c,d,e,f>
```

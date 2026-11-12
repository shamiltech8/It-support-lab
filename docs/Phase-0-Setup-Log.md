# Phase 0: Setup Log

Label: Real (problems I met and fixed while setting up the lab)

## Problem 1: VirtualBox install failed in Ubuntu WSL2
- Symptom: `sudo apt install virtualbox` failed with package download errors, including a 404 for kernel headers.
- Investigation: checked the environment and found Ubuntu was running inside WSL2, not as a standalone Linux install.
- Root cause: WSL2 uses a Microsoft-managed kernel, and VirtualBox belongs on the Windows host, not inside WSL2.
- Fix: installed VirtualBox 7.0.8 directly on Windows.
- Verification: VirtualBox Manager opens.

## Problem 2: VBoxManage was not recognized in PowerShell
- Symptom: `VBoxManage --version` returned "command not recognized".
- Investigation: checked that VirtualBox was installed, then ran the executable with its full path.
- Root cause: the VirtualBox folder is not in the Windows PATH variable.
- Fix: used the full path to `VBoxManage.exe`.
- Verification: it returned version 7.0.8.
- Note: PATH not permanently fixed; the full path works.

## Problem 3: Checking hardware virtualization
- Symptom: needed to know whether VMs could run on this laptop.
- Investigation: ran `VBoxManage list hostinfo` and checked Task Manager.
- Finding: hardware virtualization and nested paging supported, virtualization enabled.
- Result: no BIOS change needed.

## Problem 4: Low available RAM (8 GB laptop)
- Symptom: only about 0.8 GB of RAM was free.
- Investigation: checked free RAM with PowerShell (`Get-CimInstance Win32_OperatingSystem`).
- Root cause: Windows, background apps and WSL2 were using most of the memory.
- Fix: ran `wsl --shutdown`, closed unneeded apps, capped WSL2 memory in `.wslconfig`.
- Verification: free RAM rose to about 3 GB.
- Decision: run one VM at a time, and plan a lightweight lab.

## Not done yet
- Windows and Server ISO downloads, Packet Tracer, a real VM test (completed separately once done)

# Enable Hyper-V

This repository contains a script to enable or install Hyper-V along with Hyper-V Manager.

## Instructions

1. Clone or download the repository to your local machine.
2. Locate the `Enable Hyper-V.bat` file in the downloaded folder.
3. Right-click the `Enable Hyper-V.bat` file and select "Run as administrator".

```powershell
pushd "%~dp0"

dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt

for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"

del hyper-v.txt

Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL

pause
```

## Notes
- Make sure to run the script as an administrator to ensure it has the necessary permissions.
- This script is intended for systems that support Hyper-V.

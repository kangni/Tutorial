@echo off
:first
for /f "skip=3 tokens=4" %%i in ('sc query "VMware NAT Service"') do set "zt=%%i" &goto :second

:second
if /i "%zt%"=="RUNNING" (
echo Service On
) else (
echo FUCK RUIJIE
net start "VMware NAT Service"
)
ping 127.0.0.1 -n 25>nul
goto :first

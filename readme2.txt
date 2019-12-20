::作者 wwx461400
@echo off
set NOW_TIME_HH=%time:~0,2%                 

if "%NOW_TIME_HH%" lss "10" (set NOW_TIME_HH=0%time:~1,1%) else (set NOW_TIME_HH=%time:~0,2%)   

set NOW_TIME=%date:~0,4%%date:~5,2%%date:~8,2%%NOW_TIME_HH%%time:~3,2%%time:~6,2%                      

set NOW_ONLY_TIME=%NOW_TIME_HH%:%time:~3,2%:%time:~6,2% 

set TIME_HH=%time:~0,2%
if "%TIME_HH%" lss "10" (set TIME_HH=0%time:~1,7%) else (set TIME_HH=%time:~0,8%)


set "hms=%date:~0,10%%TIME_HH%"

set log_path=%hms%

set log_path=%log_path:/=%    
set log_path=%log_path::=%

mkdir "SarData%log_path%"    
cd "SarData%log_path%"          
adb shell getprop ro.serialno > serialno.txt
adb pull /data/log/fmd/SST
pause

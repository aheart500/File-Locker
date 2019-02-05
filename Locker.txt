@ECHO OFF
title Locker
if EXIST "File Hidden" goto UNLOCK
if EXIST "File" goto LOCK 
:LOCK
ren "File" "File Hidden"
attrib +h +s "File Hidden"
echo Locked
goto END
:UNLOCK
set/p  "pass=>"
if NOT %pass% == password goto FAIL
attrib -h -s "File Hidden"
ren "File Hidden" "File"
echo Unlocked
goto END
:FAIL
echo Invalid Password
goto END
:END
@pause
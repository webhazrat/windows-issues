# windows-issues

## 1. tasklist command missing issue
1. Open Command Prompt as Administrator
2. Run the WMI repair commands
   : net stop winmgmt /y
3. Rebuild the repository
  : winmgmt /resetrepository
4. Start the WMI service again
  : net start winmgmt
5. Restart your PC

## 2. Windows Time service
Run as administrator
1. net stop w32time
2. w32tm /unregister
3. w32tm /register
4. net start w32time

Configure NTP Server
w32tm /config /manualpeerlist:"time.cloudflare.com,0x8 time.google.com,0x8 pool.ntp.org,0x8" /syncfromflags:manual /update

Restart and Resync the Service
1. net stop w32time
2. net start w32time
3. w32tm /resync /force

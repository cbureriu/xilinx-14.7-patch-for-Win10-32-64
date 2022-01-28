# Xilinx Design Suite 14.7 patch for Windows10 32/64
Allows running Xilinx Design Suite version 14.7 under Windows 10 32/64 bit.
All ISE Design Tools will be patched by replacing the libPortability.dll with a library that is Win10 compatible libPortabilityNOSH.dll that has SmartHeap disabled. 

The patch does not negatively impact operation and performance of the tools. The patch scripts have to be executed in the Xilinx installation folder. The usage below assumes installation to C:\Xilinx folder. You can change that to your folder, if different.

For PlanAhead 14.7 you still need to manually add '-m32' to the shortcut or start menu so that the target becomes:
C:\Xilinx\14.7\ISE_DS\PlanAhead\bin\planAhead.bat -m32

# environment variables

set XILINX = C:\Xilinx\14.7\ISE_DS\ISE

set XILINX_EDK = C:\Xilinx\14.7\ISE_DS\EDK

# patch usage

c:\Xilinx\patch.bat

# revert to original

c:\Xilinx\revert.bat

# Installing Platform Cable USB Drivers

Sometimes the USB-to-JTAG adapter is not getting recognized (LED off). This requires uninstalling existing drivers and then installing the right drivers.

## Step 1 - Uninstalling

cd C:\Xilinx\14.7\ISE_DS\common\bin\nt64   <- this is the default install location, yours may be different, adjust as needed
wdreg -inf windrvr6.inf uninstall
wdreg -inf xusbdrvr.inf uninstall
net stop XilinxPC4Driver
del "%WINDIR%\system32\drivers\windrvr6.sys"
del "%WINDIR%\system32\drivers\xusb*.sys"
del "%WINDIR%\system32\drivers\xpc4drvr.sys"




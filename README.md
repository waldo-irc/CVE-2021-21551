# CVE-2021-21551
Exploit to SYSTEM for CVE-2021-21551

SpoolPrinter Privesc using SeImpersonatePrivileges was made thanks to @_ForrestOrr https://github.com/forrest-orr/DoubleStar/tree/main/Payloads/Source/Stage3_SpoolPotato I basically just tossed the exploit function in his code and altered it ever so barely.
NtQuerySystemInformation was taken from  @Void_Sec https://voidsec.com/exploiting-system-mechanic-driver/ almost blatantly - cannot take ANY credit for how I leaked the Token location.

At this time we just provide an upgraded cmd.exe shell.  If you want something else you'll have to edit the exploit yourself.

**UPDATE This now provides a system shell if no arguments are provided.  This can also accept an unlimited number of arguments as privilege names you would like to obtain and provide you a shell with only those specific privileges if you'd like.

![EXAMPLE ONE](https://github.com/waldo-irc/CVE-2021-21551/blob/main/System.PNG)

![EXAMPLE TWO](https://github.com/waldo-irc/CVE-2021-21551/blob/main/CustomPrivs.PNG)

All I did was merge the techniques to make a full privesc and toss in the "Fill in the blanks" from https://labs.sentinelone.com/cve-2021-21551-hundreds-of-millions-of-dell-computers-at-risk-due-to-multiple-bios-driver-privilege-escalation-flaws/
Not much I can take credit for here!  But in case you're wondering my twitter is @waldoirc
This is my first public exploit ever.  

Tested on Windows Versions 1903, 1909, and 2004.  Plans to make it work with more incoming.  Any other Windows versions with same token offsets will also work.  Need to do testing to see which versions of Windows these are.

Only currently works from medium integrity.

ADDITIONAL WAYS I WILL IMPLEMENT:
1. Will make a BoF for Cobalt Strike
2. Reflective DLL
3. Use the Read Primitive to steal a System Token and make it work from low integrity as well
**4. Clean it up and make it less noisy by masking current privs ONLY by adding SeImpersonate only using the Read Primitive + a mask of "SeImpersonatePrivilege"          : 0x00000001d
	- This is now completed.
5. Make it dnymically work with all version of windows without hardcoding SE_TOKEN_PRIVILEGES offset

This exploit is for educational purposes only.  Please do not use this where you do not have permission.

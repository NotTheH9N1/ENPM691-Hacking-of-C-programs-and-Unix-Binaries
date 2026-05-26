# ENPM691 - Hacking of C Programs and Unix Binaries

**Advanced Binary Exploitation Coursework**  
University of Maryland, College Park  
All homeworks were completed in 32-bit x86 Kali Linux with GDB, objdump, and custom exploit scripts.

---

## Selected Homework Highlights

### HW05: Stack Buffer Overflow and Shellcode Exploitation
Demonstrated classic code injection by overflowing a fixed-size buffer with `gets()` and overwriting the saved return address to execute custom shellcode that spawns a root shell via `execve("/bin/sh")`. Two different techniques were implemented: direct return-address overwrite and function-pointer casting.  
**Tags:** `buffer-overflow`, `shellcode`, `code-injection`, `privilege-escalation`

### HW06: JMP ESP Gadget Exploitation for SUID Privilege Escalation
Bypassed the need to predict the exact buffer address by using a `jmp *%esp` gadget inside the binary itself. The exploit redirected execution to attacker-controlled shellcode on the stack, achieving root shell on an SUID binary despite ASLR being disabled.  
**Tags:** `jmp-esp`, `gadget`, `suid`, `stack-exploit`

### HW07: Return-Oriented Programming (ROP) Chain Exploitation
Built a full ROP chain to bypass NX (non-executable stack) protection. Chained short instruction sequences ("gadgets") ending in `ret` to set up registers and call `execve("/bin/sh")` without injecting any new code.  
**Tags:** `rop`, `nx-bypass`, `gadgets`, `return-oriented-programming`

### HW08: Global Offset Table (GOT) Hijacking Attack
Exploited the dynamic linking mechanism by overwriting GOT entries for `printf()` and `puts()` during a buffer overflow. Demonstrated the full PLT/GOT resolution process in GDB and achieved arbitrary code execution by redirecting library function calls.  
**Tags:** `got-hijacking`, `plt`, `dynamic-linking`, `binary-exploitation`

### HW09: Format String Exploitation Attack
Used a format-string vulnerability (`printf(user_input)`) with the `%n` specifier to write arbitrary values to memory. Overwrote a global function pointer to redirect execution to a privileged `target_function()` that spawned a root shell.  
**Tags:** `format-string`, `arbitrary-write`, `%n`, `function-pointer-hijack`

### HW11: Heap Use-After-Free Exploitation
Exploited a classic heap use-after-free vulnerability using fastbin LIFO reuse. Freed a username chunk, then forced a password allocation to reuse the same memory, creating pointer aliasing that bypassed `strcmp()` authentication and granted root access.  
**Tags:** `heap`, `use-after-free`, `fastbin`, `memory-reuse`

---

**Total Assignments:** 11 homeworks covering memory layout, compiler optimizations, stack/heap exploitation, format strings, ROP, GOT hijacking, and more.

Feel free to explore the individual homework PDFs for full reports, exploit scripts, GDB transcripts, and disassembly.

---


---

<h3 id="analysis">ANALYSIS</h3>
<h4 id="the-rom-bios">1 The ROM BIOS</h4>
<p>after <code>cd lab</code>:<br>
run <code>make qemu-gdb</code> in a ternimal, wo got:</p>
<pre class=" language-undefined"><code class="prism language-*** language-undefined">*** Now run 'make gdb'.
***
qemu-system-i386 -drive file=obj/kern/kernel.img,index=0,media=disk,format=raw -serial mon:stdio -gdb tcp::26000 -D qemu.log  -S
VNC server running on 127.0.0.1:5900
</code></pre>
<p>run <code>make gdb</code> in another terminal:</p>
<pre><code>gdb -n -x .gdbinit
GNU gdb (Ubuntu 9.2-0ubuntu1~20.04) 9.2
Copyright (C) 2020 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later &lt;http://gnu.org/licenses/gpl.html&gt;
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
&lt;http://www.gnu.org/software/gdb/bugs/&gt;.
Find the GDB manual and other documentation resources online at:
    &lt;http://www.gnu.org/software/gdb/documentation/&gt;.

For help, type "help".
Type "apropos word" to search for commands related to "word".
+ target remote localhost:26000
warning: No executable has been specified and target does not support
determining executable automatically.  Try using the "file" command.
The target architecture is assumed to be i8086
[f000:fff0]    0xffff0:	ljmp   $0x3630,$0xf000e05b
0x0000fff0 in ?? ()
+ symbol-file obj/kern/kernel
warning: A handler for the OS ABI "GNU/Linux" is not built into this configuration
of GDB.  Attempting to continue with the default i8086 settings.
</code></pre>
<p>(result is a little differenet with tutorial)</p>
<p>The following line:</p>
<pre><code>[f000:fff0]    0xffff0:	ljmp   $0x3630,$0xf000e05b
</code></pre>
<p>is GDB’s disassembly of the first instruction to be executed. From this output you can conclude a few things:</p>
<ul>
<li>The IBM PC starts executing at physical address 0x000ffff0, which is at the very top of the 64KB area reserved for the ROM BIOS.(below 1MB)</li>
<li>The PC starts executing with  CS = 0xf000  and  IP = 0xfff0.</li>
<li>The first instruction to be executed is a  jmp  instruction, which jumps to the segmented address  CS = 0xf000  and  IP = 0xe05b.</li>
</ul>
<p><img src="https://images2015.cnblogs.com/blog/809277/201512/809277-20151226140726515-1184467718.png" alt="structure of A PC's physical address space"></p>
<p>Basic Input/Output System</p>


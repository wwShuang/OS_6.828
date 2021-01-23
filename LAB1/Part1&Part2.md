---


---

<blockquote>
<p>MIT-6.828-OS-LAB1-Part1&amp;Part2<br>
author: galaxyG<br>
Lab website : <a href="https://pdos.csail.mit.edu/6.828/2018/labs/lab1/">https://pdos.csail.mit.edu/6.828/2018/labs/lab1/</a><br>
System Environment: Ubuntu 20.04.1 LTS_64-bit<br>
(i’m not a native speaker, if there is any grammar mistake, pls let me know, thank u!)</p>
</blockquote>
<h2 id="software-setup">Software Setup</h2>
<blockquote>
<p>Original <a href="https://www.cnblogs.com/fatsheep9146/p/5068353.html">blog</a>.</p>
</blockquote>
<p><strong>QEMU installation</strong><br>
follow this steps: <a href="https://en.wikibooks.org/wiki/QEMU/Linux">wekipidia</a><br>
（if you encounter any errors here,  just setup the software you need to install according to the error information）</p>
<h2 id="part-1-pc-bootstrap">Part 1: PC Bootstrap</h2>
<h3 id="error-log">ERROR LOG</h3>
<p>1 follow the procedure of <a href="https://pdos.csail.mit.edu/6.828/2018/labs/lab1/">lab1 tutorial</a>:</p>
<p><strong>ERROR 1- about multilib</strong>:</p>
<blockquote>
<p>(If you get errors like “undefined reference to `__udivdi3’”, you probably don’t have the 32-bit gcc multilib. If you’re running Debian or Ubuntu, try installing the gcc-multilib package.)</p>
</blockquote>
<p>Pay attention when Install multilib:</p>
<ul>
<li>check the version of gcc in your system <code>gcc -v</code>. for example, my gcc version is  8.4.0  so I use the command:<br>
<code>sudo apt-get install gcc-8-multilib</code></li>
</ul>
<p><strong>ERROR 2 - TCP port</strong></p>
<blockquote>
<p>localhost:26000: Connection timed out.<br>
<a href="https://stackoverflow.com/questions/50157959/use-of-target-remote-localhost26000">question and answer</a></p>
</blockquote>
<p>Reason:<br>
<code>gdbserver</code> listening on the given port 25000, but the <code>client</code> is going to the port 26000. So just keep the port number same.</p>


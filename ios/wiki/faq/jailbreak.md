# Why does PojavLauncher require jailbreak?

On iOS/iPadOS, every executable needs to be signed or trustcached while having 
an adhoc signature. Additionally, the memory pages of the processes must also be 
backed with a signature when they are executed given that they do not have the 
`dynamic-codesigning` entitlement (which cannot be normmally obtained while 
jailed) or has the `get-task-allow` entitlements and has `CS_DEBUGGED` set on 
it, else the process gets terminated while trying to do it.  Additionally, the 
`dynamic-codesigning` entitlement is required to create memory pages that are 
both readable, writable and executable. PojavLauncher uses JIT (Just-In-Time) 
compliation for in java to improve performance, which is used to run minecraft. 
A JIT compiler emits instructions at runtime and then exeute them. This do not 
work jailed because you can only have readable-executable and readable-writable 
memory pages. Although it is possible to switch the permissions back and forth 
or map some pages readable-writable, then mirror-map them as 
readable-executable, JIT compilation still will not work due to these pages 
being unsigned.

## Methods considered

### Using Zero VM

This is commonly confused with `-Xint` although this is actually worse than 
that. In a Zero VM, there is no JIT compliation. Everything is interptered. This 
can work jailed. However, the performance will be so bad that it is better 
measured in seconds per frame instead of frames per seconds! Therefore this will 
not really work.

### Using threaded interpter/"fake JIT"

In a threaded interpter, all the possible "JIT" results are pre-compiled. At 
runtime, the threaded interpter generates ("JIT") memory pointers to the 
precompiled code in memory and have the CPU execute that. Since all the code 
executed is pre-compiled and therefore signed, this can work jaied. The 
performance is much better than a normal interpter while being sigificantly 
worse than a JIT compiler. However, java has no threaded interpreter backend so 
it needs to be implemented from scratch, and the performance is actually still 
quite bad compared to JIT, so this does not really work either.

### Using psychcic_paper

psychic_paper is a bug from at least iOS 11 up to iOS/iPadOS 13.5 beta 2 that 
allows obtaining arbitary entitlements. However, these versions already have
jailbreaks.

### Using ptrace() trick

This works up until iOS/iPadOS 13.7. Basically up until iOS/iPadOS 13.7, a 
process can set `CS_DEBUGGED` on itself by calling `ptrace()` with 
`PT_TRACE_ME`. This allows a readable-writable mirror map readable-executable 
"bullproof" JIT to be set up.  However, if the process terminated for whatever 
reason other than itself calling `exit()`, the app will be unusable until a 
reboot due to an iOS bug. Additionally, these versions already have a jailbreak.

### CS_EXECSEG_ALLOW_UNSIGNED bug

This is a flag that can be set while installing the app. On iOS/iPadOS 14.2-14.3 
this allows for bullproof JIT to happen regardless of an a debugger being 
attached. However, these versions already have jailbreaks.

### Using WebAssembly JIT

In this case, the JIT compiler is made to emit WebAssembly where it will be JIT 
compiled again into native code by WebKit. However, the delay is high as this 
involves inter-process communication. Addtionally, since this is "double-JIT" 
the performance would not be as good. This is also unimplemented in java.

### Run with debugger

This can work for bulletproof JIT, even with latest iOS/iPadOS, tethered with a 
debugger from another device ([JitterBug](https://github.com/osy/jitterbug))/PC 
(AltJIT/libimobiledevice). This is not convenient. This can also be 
semi-untehered with JitterBug when signed with network extension entitlement 
with a paid developer account (or when signed with a testflight certificate). 
The performance will be slightly worse, and you cannot modify jetsam but 
iOS/iPadOS has a bug where mirror mapped memory is also considered actual memory 
usage. (Although this can be worked around by not remapping all at once) 
However, support for jailed debugger JIT is not implemented into PojavLauncher.

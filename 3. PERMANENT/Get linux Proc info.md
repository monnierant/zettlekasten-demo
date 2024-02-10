---
type: evidence
topic: Sysadmin 
---

- Topic : #VeilleIT/Sysadmin 
- Tags : #linux 

# Idea


## Combined report

`lscpu`

> [!example] 
>  ```
> Architecture:          x86_64
> CPU op-mode(s):        32-bit, 64-bit
> Byte Order:            Little Endian
> CPU(s):                4
> On-line CPU(s) list:   0-3
> Thread(s) per core:    1
> Core(s) per socket:    4
> Socket(s):             1
> NUMA node(s):          1
> Vendor ID:             GenuineIntel
> CPU family:            6
> Model:                 42
> Model name:            Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
> Stepping:              7
> CPU MHz:               1596.397
> CPU max MHz:           3400.0000
> CPU min MHz:           1600.0000
> BogoMIPS:              6185.95
> Virtualization:        VT-x
> L1d cache:             32K
> L1i cache:             32K
> L2 cache:              256K
> L3 cache:              6144K
> NUMA node0 CPU(s):     0-3
> Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts md_clear flush_l1d
> ```

## Full list of info for each CPU

`cat /proc/cpuinfo`

> [!example] 
> ```
> processor       : 0
> vendor_id       : GenuineIntel
> cpu family      : 6
> model           : 42
> model name      : Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
> stepping        : 7
> microcode       : 0x2f
> cpu MHz         : 1596.394
> cache size      : 6144 KB
> physical id     : 0
> siblings        : 4
> core id         : 0
> cpu cores       : 4
> apicid          : 0
> initial apicid  : 0
> fpu             : yes
> fpu_exception   : yes
> cpuid level     : 13
> wp              : yes
> flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts md_clear flush_l1d
> bugs            : cpu_meltdown spectre_v1 spectre_v2 spec_store_bypass l1tf mds swapgs itlb_multihit
> bogomips        : 6185.95
> clflush size    : 64
> cache_alignment : 64
> address sizes   : 36 bits physical, 48 bits virtual
> power management:
> ```
 

## Some other options

- `sudo dmidecode --type processor`

# Links

Sources : [9 Useful Commands to Get CPU Information on Linux](https://www.tecmint.com/check-linux-cpu-information/)

## West : Similar

## East : Opposite

## North : Theme / Question

[[How to know Linux VM ressources]]

## South : What does it lead to


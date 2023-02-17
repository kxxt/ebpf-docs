# Program types (Linux)

eBPF programs can be used for large and ever growing variety of different purposes. Different types of eBPF programs exist to accommodate these different use-cases. The Linux kernel may restrict or allow certain features depending on the program type, not all types of programs can do the same things because of where they are executed in the kernel. The verifier will enforce such restrictions.

## ELF sections

The concept of a program type only exists at the kernel/syscall level. There is no standardized way of marking which program type a particular program within an [ELF](../../elf.md) is. The industry standard that most [loaders](../../loader.md) follow the example set out by LibBPF which is to patterns in the [ELF](../../elf.md) section names to convey the program type. 

## Index of program types

* [BPF_PROG_TYPE_SOCKET_FILTER](BPF_PROG_TYPE_SOCKET_FILTER.md)
* BPF_PROG_TYPE_KPROBE
* BPF_PROG_TYPE_SCHED_CLS
* BPF_PROG_TYPE_SCHED_ACT
* BPF_PROG_TYPE_TRACEPOINT
* BPF_PROG_TYPE_XDP
* BPF_PROG_TYPE_PERF_EVENT
* BPF_PROG_TYPE_CGROUP_SKB
* BPF_PROG_TYPE_CGROUP_SOCK
* BPF_PROG_TYPE_LWT_IN
* BPF_PROG_TYPE_LWT_OUT
* BPF_PROG_TYPE_LWT_XMIT
* [BPF_PROG_TYPE_SOCK_OPS](BPF_PROG_TYPE_SOCK_OPS.md)
* BPF_PROG_TYPE_SK_SKB
* BPF_PROG_TYPE_CGROUP_DEVICE
* BPF_PROG_TYPE_SK_MSG
* BPF_PROG_TYPE_RAW_TRACEPOINT
* BPF_PROG_TYPE_CGROUP_SOCK_ADDR
* BPF_PROG_TYPE_LWT_SEG6LOCAL
* BPF_PROG_TYPE_LIRC_MODE2
* BPF_PROG_TYPE_SK_REUSEPORT
* BPF_PROG_TYPE_FLOW_DISSECTOR
* BPF_PROG_TYPE_CGROUP_SYSCTL
* BPF_PROG_TYPE_RAW_TRACEPOINT_WRITABLE
* BPF_PROG_TYPE_CGROUP_SOCKOPT
* BPF_PROG_TYPE_TRACING
* BPF_PROG_TYPE_STRUCT_OPS
* BPF_PROG_TYPE_EXT
* BPF_PROG_TYPE_LSM
* BPF_PROG_TYPE_SK_LOOKUP
* BPF_PROG_TYPE_SYSCALL

## Index of section names

<!-- TODO -->
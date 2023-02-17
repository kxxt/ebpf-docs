# Helper functions

Helper functions are functions defined by the kernel which can be invoked from eBPF programs. These helper functions allow eBPF programs to interact with the kernel as if calling a function. The kernel places restrictions on the usage of these helper functions to prevent misuse. Check the pages of the individual calls for details on its usage.

Helper functions can have a large variety of purposes. This page attempts to categorize them by function.

## Map helpers

These are helpers with the primary purpose involves the interaction with a map.

### Generic map helpers

These helpers can be used on a lot of different maps, especially the generic map types like array and hash maps.

* [bpf_map_lookup_elem](bpf_map_lookup_elem.md)
* [bpf_map_update_elem](bpf_map_update_elem.md)
* [bpf_map_delete_elem](bpf_map_delete_elem.md)
* bpf_for_each_map_elem
* bpf_map_lookup_percpu_elem
* bpf_spin_lock
* bpf_spin_unlock
  
### Perf event array helpers

These helpers are used with `BPF_MAP_TYPE_PERF_EVENT_ARRAY` maps.

* bpf_perf_event_read
* bpf_perf_event_output
* bpf_perf_event_read_value
* bpf_perf_prog_read_value

### Tail call helpers

These helpers are used with `BPF_MAP_TYPE_PROG_ARRAY` maps.

* bpf_tail_call

### Timer helpers

These helpers are used to manage timers.

* bpf_timer_init
* bpf_timer_set_callback
* bpf_timer_start
* bpf_timer_cancel

## Queue and stack helpers

These helpers are used with `BPF_MAP_TYPE_QUEUE` and `BPF_MAP_TYPE_STACK` maps.

* bpf_map_push_elem
* bpf_map_pop_elem
* bpf_map_peek_elem
* bpf_msg_push_data
* bpf_msg_pop_data

### Ringbuffer helper

These helpers are used with `BPF_MAP_TYPE_RINGBUF` maps.

* bpf_ringbuf_output
* bpf_ringbuf_reserve
* bpf_ringbuf_submit
* bpf_ringbuf_discard
* bpf_ringbuf_query

### Task storage helpers

These helpers are used with `BPF_MAP_TYPE_TASK_STORAGE` maps.

* bpf_task_storage_get
* bpf_task_storage_delete

### Inode storage helpers

These helpers are used with `BPF_MAP_TYPE_INODE_STORAGE` maps.

* bpf_inode_storage_get
* bpf_inode_storage_delete

### Socket storage helpers

These helpers are used with `BPF_MAP_TYPE_SK_STORAGE` maps.

* bpf_sk_storage_get
* bpf_sk_storage_delete

### Local cGroup storage helpers

These helpers are used with `BPF_MAP_TYPE_CGROUP_STORAGE` and `BPF_MAP_TYPE_PERCPU_CGROUP_STORAGE` maps.

* bpf_get_local_storage

### Global cGroup storage helpers

These helpers are used with `BPF_MAP_TYPE_CGRP_STORAGE` maps.

* bpf_cgrp_storage_get
* bpf_cgrp_storage_delete

### User ring buffer

These helpers are related to `BPF_MAP_TYPE_USER_RINGBUF` maps.

* bpf_user_ringbuf_drain

## Probe and trace helpers

These helpers are used in probing and tracing functions like kprobes, tracepoints and uprobes.

* bpf_get_attach_cookie

### Memory helpers

These helpers are used to read from or write to kernel or userspace memory.

* bpf_probe_read
* bpf_probe_write_user
* bpf_probe_read_str
* bpf_get_stack
* bpf_probe_read_user
* bpf_probe_read_kernel
* bpf_probe_read_user_str
* bpf_probe_read_kernel_str
* bpf_copy_from_user
* bpf_copy_from_user_task
* bpf_copy_from_user_task
* bpf_find_vma

### Process influencing helpers

These helpers are used to influence processes.

* bpf_override_return
* bpf_get_retval
* bpf_set_retval
* bpf_send_signal
* bpf_send_signal_thread

### Tracing helpers

These helpers return information specific to `BPF_PROG_TYPE_TRACING` programs.

* bpf_get_func_ip
* bpf_get_func_arg
* bpf_get_func_ret
* bpf_get_func_arg_cnt
* bpf_sock_from_file
  
## Information helpers

These helpers return information from the kernel which is otherwise not available to eBPF programs.

### Time helpers

These helpers return time information.

* bpf_ktime_get_ns
* bpf_jiffies64
* bpf_ktime_get_boot_ns
* bpf_ktime_get_coarse_ns
* bpf_ktime_get_tai_ns

### Process info helpers

These helpers return information about processes, particularly the one for which the current eBPF program is invoked.

* bpf_get_current_pid_tgid
* bpf_get_current_uid_gid
* bpf_get_current_comm
* bpf_get_cgroup_classid
* bpf_get_ns_current_pid_tgid
* bpf_get_current_task
* bpf_get_stackid
* bpf_current_task_under_cgroup
* bpf_get_current_cgroup_id
* bpf_get_current_ancestor_cgroup_id
* bpf_get_task_stack
* bpf_get_current_task_btf
* bpf_task_pt_regs

### CPU info helpers

These helpers return information about the current state of the CPU.

* bpf_get_smp_processor_id
* bpf_get_numa_node_id
* bpf_read_branch_records
* bpf_get_branch_snapshot
* bpf_per_cpu_ptr
* bpf_this_cpu_ptr

## Print helpers

These helpers are used to print logs from an eBPF program which will appear in the kernel tracing log.

* bpf_trace_printk
* bpf_snprintf
* bpf_snprintf_btf
* bpf_trace_vprintk

### Iterator print helpers
  
These helpers are used to print logs to the sequence files used by eBPF iterator programs.

* bpf_seq_printf
* bpf_seq_write
* bpf_seq_printf_btf

## Network helpers

These helpers are related to networking.

* bpf_get_netns_cookie
* bpf_check_mtu
* bpf_get_route_realm
* bpf_fib_lookup

### Socket buffer helpers

These helpers read from, write to, or modify socket buffers in some way.

* bpf_skb_store_bytes
* bpf_skb_load_bytes
* bpf_skb_vlan_push
* bpf_skb_vlan_pop
* bpf_skb_get_tunnel_key
* bpf_skb_set_tunnel_key
* bpf_skb_get_tunnel_opt
* bpf_skb_set_tunnel_opt
* bpf_skb_change_proto
* bpf_skb_change_type
* bpf_skb_under_cgroup
* bpf_skb_change_tail
* bpf_skb_pull_data
* bpf_skb_adjust_room
* bpf_skb_change_head
* bpf_skb_get_xfrm_state
* bpf_skb_load_bytes_relative
* bpf_skb_cgroup_id
* bpf_skb_ancestor_cgroup_id
* bpf_skb_ecn_set_ce
* bpf_skb_cgroup_classid
* bpf_skb_set_tstamp
* bpf_skb_output
* bpf_set_hash
* bpf_get_hash_recalc
* bpf_set_hash_invalid

### Checksum helpers

These helpers calculate and/or update checksums.

* bpf_l3_csum_replace
* bpf_l4_csum_replace
* bpf_csum_diff
* bpf_csum_update
* bpf_csum_level

### Redirect helpers

These helpers redirect the flow of packets in some way.

* bpf_clone_redirect
* bpf_redirect
* bpf_redirect_map
* bpf_sk_redirect_map
* bpf_msg_redirect_map
* bpf_redirect_peer
* bpf_sk_redirect_hash
* bpf_msg_redirect_hash
* bpf_redirect_neigh
  
### XDP helpers

These helpers are specific to `BPF_PROG_TYPE_XDP` programs.

* bpf_xdp_adjust_head
* bpf_xdp_adjust_tail
* bpf_xdp_adjust_meta
* bpf_xdp_output
* bpf_xdp_get_buff_len
* bpf_xdp_load_bytes
* bpf_xdp_store_bytes

### Sk msg helpers

These helpers are specific to `BPF_PROG_TYPE_SK_MSG` programs.

* bpf_msg_apply_bytes
* bpf_msg_cork_bytes
* bpf_msg_pull_data

### LWT helpers

These helpers are specific to `BPF_PROG_TYPE_LWT_*` programs.

* bpf_lwt_push_encap
* bpf_lwt_seg6_store_bytes
* bpf_lwt_seg6_adjust_srh
* bpf_lwt_seg6_action

### SYNCookie helpers

These helpers are related to syn cookies.

* bpf_tcp_check_syncookie
* bpf_tcp_gen_syncookie
* bpf_tcp_raw_gen_syncookie_ipv4
* bpf_tcp_raw_gen_syncookie_ipv6
* bpf_tcp_raw_check_syncookie_ipv4
* bpf_tcp_raw_check_syncookie_ipv6

### Socket helpers

These helpers are related to socket.

* bpf_sk_select_reuseport
* bpf_sk_lookup_tcp
* bpf_sk_lookup_udp
* bpf_sk_release
* bpf_sk_fullsock
* bpf_sk_assign
* bpf_sk_cgroup_id
* bpf_sk_ancestor_cgroup_id
* bpf_get_socket_cookie
* bpf_get_socket_uid
* bpf_setsockopt
* bpf_sock_map_update
* bpf_getsockopt
* bpf_sock_ops_cb_flags_set
* bpf_sock_hash_update
* bpf_tcp_sock
* bpf_get_listener_sock
* bpf_tcp_send_ack
* bpf_skc_lookup_tcp
* bpf_skc_to_tcp6_sock
* bpf_skc_to_tcp_sock
* bpf_skc_to_tcp_timewait_sock
* bpf_skc_to_tcp_request_sock
* bpf_skc_to_udp6_sock
* bpf_skc_to_mptcp_sock
* bpf_skc_to_unix_sock
* bpf_bind

### Socket ops helpers

These helpers are specific to `BPF_PROG_TYPE_SOCK_OPS` programs.

* bpf_load_hdr_opt
* bpf_store_hdr_opt
* bpf_reserve_hdr_opt

## Infrared related helpers

These helpers are specific to `BPF_PROG_TYPE_LIRC_MODE2` programs.

* bpf_rc_repeat
* bpf_rc_keydown
* bpf_rc_pointer_rel

## Syscall helpers

These helpers are specific to `BPF_PROG_TYPE_SYSCALL` programs.

* bpf_sys_bpf
* bpf_btf_find_by_name_kind
* bpf_sys_close
* bpf_kallsyms_lookup_name

### LSM helpers

These helpers are specific to `BPF_PROG_TYPE_LSM` programs.

* bpf_bprm_opts_set
* bpf_ima_inode_hash
* bpf_ima_file_hash

## Sysctl helpers

These helpers are specific to `BPF_PROG_TYPE_CGROUP_SYSCTL` programs.

* bpf_sysctl_get_name
* bpf_sysctl_get_current_value
* bpf_sysctl_get_new_value
* bpf_sysctl_set_new_value

## Dynptr

These helpers are related to dynamic pointers

* bpf_dynptr_from_mem
* bpf_ringbuf_reserve_dynptr
* bpf_ringbuf_submit_dynptr
* bpf_ringbuf_discard_dynptr
* bpf_dynptr_read
* bpf_dynptr_write
* bpf_dynptr_data

## Loop helpers

These helpers are used to execute loops.

* bpf_loop

## Utility helpers

These helpers are smaller utility functions which don't really fit in elsewhere.

* bpf_get_prandom_u32
* bpf_strtol
* bpf_strtoul
* bpf_strncmp
* bpf_d_path

## Misc

* bpf_kptr_xchg
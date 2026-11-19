# newminhh/issues — Central Issue Tracker (`新明` — "New Tomorrow")

Welcome to the central issue tracker for the **[`newminhh`](https://github.com/newminhh)** (`新明` — "New Tomorrow") ecosystem: a container-less **`i386` (`ELFCLASS32`, `EM_386`) compatibility system for `x32`-only (`ELFCLASS32`, `EM_X86_64`, ILP32) Linux**.

All bug reports, legacy `i386` application/library compatibility reports, and feature requests across the `newminhh` split repositories are tracked here.

---

## Before Opening an Issue

1. **Read the Documentation:** Start at **[`newminhh/docs`](https://github.com/newminhh/docs)** ([`README.md`](https://github.com/newminhh/docs/blob/main/README.md), [`ARCHITECTURE.md`](https://github.com/newminhh/docs/blob/main/ARCHITECTURE.md), and [`TESTING_AND_VM.md`](https://github.com/newminhh/docs/blob/main/TESTING_AND_VM.md)).
2. **Verify Kernel `x32` Requirements:** Ensure your target/guest kernel is compiled with `CONFIG_X86_X32_ABI=y` (or `CONFIG_X86_X32=y`) and booted with `syscall.x32=y` (see the [2026 Kernel Requirements Notice](https://github.com/newminhh/docs#target--guest-debian-x32)).
3. **Collect Diagnostic Logs:** Re-run with `NEWMINHH_DEBUG=1` to capture structured `[newminhh:<component>]` logs from `stderr`.
4. **Follow Our Code of Conduct:** Participation is governed by the **[Code of Conduct (`CODE_OF_CONDUCT.md`)](https://github.com/newminhh/docs/blob/main/CODE_OF_CONDUCT.md)**.

---

## Issue Templates

Click **[New Issue](https://github.com/newminhh/issues/issues/new/choose)** and select one of the structured templates:

| Template | File | Use When |
| :--- | :--- | :--- |
| **Bug Report** | [`.github/ISSUE_TEMPLATE/bug_report.yml`](./.github/ISSUE_TEMPLATE/bug_report.yml) | Reporting a crash, incorrect output, memory leak, build failure, or regression in `compat`, `dbt`, `patcher`, `common`, `tests`, or `vm` |
| **i386 Binary / Library Compatibility Report** | [`.github/ISSUE_TEMPLATE/compatibility_report.yml`](./.github/ISSUE_TEMPLATE/compatibility_report.yml) | Reporting an unmodified 32-bit `i386` executable or `.so` library that fails due to an unimplemented libc/libm/pthread wrapper, syscall number, opcode, or struct layout |
| **Feature Request** | [`.github/ISSUE_TEMPLATE/feature_request.yml`](./.github/ISSUE_TEMPLATE/feature_request.yml) | Proposing a new symbol wrapper, syscall translation, JIT optimization, static rewriter pass, or CLI/benchmark capability |

---

## Tracked Repositories

| Repository | Description |
| :--- | :--- |
| [`newminhh/docs`](https://github.com/newminhh/docs) | Primary entrypoint documentation, architecture reference, VM/testing guide, and Code of Conduct |
| [`newminhh/newminhh`](https://github.com/newminhh/newminhh) | Umbrella workspace, unified `Makefile`, and `bin/newminhh` CLI |
| [`newminhh/common`](https://github.com/newminhh/common) | Shared C/assembly ABI contracts (`newminhh_abi.h`, `newminhh_log.h`) |
| [`newminhh/compat`](https://github.com/newminhh/compat) | `libnewminhh_compat.so` — `cdecl` ↔ `x32` SysV runtime bridge, W^X trampolines, syscalls, struct repacking, `dlopen`/`dlsym` |
| [`newminhh/dbt`](https://github.com/newminhh/dbt) | `libnewminhh_dbt.so` & `newminhh-run` — In-process `i386` ELF32 loader and Long Mode `x32` JIT engine |
| [`newminhh/patcher`](https://github.com/newminhh/patcher) | `newminhh-patch` — Containerized (`re-env:latest`) static & hybrid `i386`-to-`x32` ELF32 rewriter |
| [`newminhh/tests`](https://github.com/newminhh/tests) | Parts 1–5 verification corpus (`C01`–`C11`, `S01`–`S03`, `N01`–`N09`) and `/proc/<pid>/smaps` benchmark suites |
| [`newminhh/vm_test_scripts`](https://github.com/newminhh/vm_test_scripts) | Debian `x32` `libvirt-qemu` provisioning and execution scripts |

# z/OS Porting Changes for sqlite-vec

## Summary
Ported `sqlite-vec` v0.1.7-alpha.10 to z/OS.

## Changes
- **Makefile**:
  - Added support for conditional assignment (`?=`) of `INSTALL_*_DIR` to allow overrides from `buildenv`.
  - Removed `sudo` and `ldconfig` calls which are not compatible with z/OS or required.
  - Ensured correct installation paths for z/OS using `ZOPEN_INSTALL_DIR`.
- **sqlite-vec.c**:
  - Added `#ifndef __MVS__` around `u_int*` typedefs to avoid conflicts with system headers.
- **sqlite-vec.h.tmpl**:
  - Defined `SQLITE_VEC_API` with `__attribute__((visibility("default")))` on z/OS to ensure symbols (like `sqlite3_vec_init`) are exported from the shared library.

## Build Requirements
- `sqlite`
- `make`
- `coreutils` (for `install`)

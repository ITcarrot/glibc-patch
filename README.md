# glibc-patch
Patch the software with new glibc on old linux system.

- Resolve the following error on linux executables:
```
/lib64/libm.so.6: version `GLIBC_*.**' not found
/lib64/libc.so.6: version `GLIBC_*.**' not found
/lib64/libstdc++.so.6: version `CXXABI_*.*.*' not found
/lib64/libstdc++.so.6: version `GLIBCXX_*.*.**' not found 
```
- Help run vscode server on older linux

## Requirements
- Operating system: linux_amd64

## Usage
1. Download / Clone this repository to your computer
2. Go to the local directory of this repository

### Patch Executables
To resolve the glibc errors on linux executables, run:
```bash
bin/glibc-patch path/to/executable
```
**WARNING: DO NOT move this repository AFTER any patches!**

### Patch Vscode Server
1. Trun OFF the vscode setting -> Remote.SSH: Use Exec Server
2. Connect to the remote via Vscode Remote.SSH until it fails to start the server
  - The vscode server exectuable will be downloaded in this step
3. Close Vscode
4. Go to the directory of this repository on the remote system, run:
```bash
bin/glibc-patch-vscode
```
  - If you change the server install path, run the following instead:
  ```bash
  bin/glibc-patch-vscode path/to/.vscode-server
  ```
5. Vscode server is now available, connect it.
6. The above process should be done again when the Vscode upgrades.

**WARNING: DO NOT move this repository AFTER any patches!**

### Patch Antigravity Server
1. Connect to the remote via Antigravity until it fails to start the server
   - The antigravity server executable will be downloaded in this step
2. Close Antigravity
3. Go to the directory of this repository on the remote system, run:
```bash
bin/glibc-patch-antigravity
```
   - If you change the server install path, run the following instead:
   ```bash
   bin/glibc-patch-antigravity path/to/.antigravity-server
   ```
4. Antigravity server is now available, connect it.
5. The above process should be done again when the Antigravity upgrades.

**WARNING: DO NOT move this repository AFTER any patches!**

## Technical Details
- ELF editor: [patchelf-0.18.0](http://github.com/NixOS/patchelf)
- Glibc version: 2.38 from [ubuntu debs](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.38-3ubuntu1_amd64.deb)
- Libstdc++ version: 13.1 from [ubuntu debs](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-13/libstdc++6_13.1.0-2ubuntu2~23.04_amd64.deb)

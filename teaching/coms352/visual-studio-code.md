---
layout: class
title: COM S 352 Visual Studio Code
class-name: COM S 352
header: coms352-header.html
---
## Visual Studio Code

### 1. Download and Install

Download and install [Visual Studio Code](https://code.visualstudio.com/) for Windows, Linux or Mac.

### 2. Add local Extensions

Add the following local extensions.
* Remote - SSH
* RISC-V Support

### 3. Prepare pyrite.cs.iastate.edu

```sh
ssh username@pyrite.cs.iastate.edu
```

```sh
git clone git://github.com/mit-pdos/xv6-riscv.git
```

### 4. Connect to pyrite.cs.iastate.edu

Connect to pyrite.cs.iastate.edu.

Open Remote Explorer

Right click on pyrite.cs.iastate.edu -> xv6-riscv and open in current window.

### 5. 

Open Explorer.

Expand .vscode and modify lanuch.json to the following:
```json
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Debug xv6-riscv",
            "type": "cppdbg",
            "request": "launch",
            "preLaunchTask": "Run make qemu-gdb",
            "program": "${workspaceRoot}/kernel/kernel",
            "cwd": "${workspaceRoot}/gdb",
            "miDebuggerServerAddress": "0.0.0.0:26000",
            "miDebuggerPath": "${workspaceRoot}/gdb/riscv64-unknown-elf-gdb",
            "miMode": "gdb",
        }
    ]
} 
```

Add a new file in .vscode called tasks.json.
```json
{
  // See https://go.microsoft.com/fwlink/?LinkId=733558
  // for the documentation about the tasks.json format
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Run make qemu-gdb",
      "type": "shell",
      "command": "make qemu-gdb",
      "isBackground": true,
      "problemMatcher": [
        {
          "pattern": [
            {
              "regexp": ".",
              "file": 1,
              "location": 2,
              "message": 3
            }
          ],
          "background": {
            "activeOnStart": true,
            "beginsPattern": ".",
            "endsPattern": ".",
          }
        }
      ]
    }
  ]
}
```


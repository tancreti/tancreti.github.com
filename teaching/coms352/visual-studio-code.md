launch.json
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

tasks.json
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


## C

###Editor
Preferred editor: vscode

###Configuring the envrionment:

ctrl -shift + p => shows the palette.
C/C++ Edit configurations UI => 
	Set correctly the compiler path: in linux: /usr/bin/gcc
	Set the intellisense mode: gcc-x64
It will have created a .code folder with c_cpp_properties.json configuration.


Tasks:configure tasks ==> Create tasks file from template => others => 
Creates a tasks file: Modify the content to be something like this:
```shell

{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "build hello world",
            "type": "shell",
            "command": "gcc",
            "args": [
                "-g",
                "-o",
                "helloworld",
                "helloworld.c"
            ],
            "group": {
                "kind":"build",
                "isDefault": true
            }
        }
    ]
}

instead of hello world add the file name to compile from.
```


Debug ==> open launch json ==> c++(GDB/LLDB)
Creates a launch.json file: Modify the content to be something like this:
```shell
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/helloworld",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}
```

###Creating your executable file

```shell
$ touch helloworld.c

#add the following to your example:

#include <stdio.h>
int main(){
    printf("Hello, world!");
    return 0;
}

```

###Executing the task:
press: CTRL + SHIFT + B => will compile according to tasks.json file generating the executable helloworld.

###Debugging:
To debug press F5 key. Note that you can previously add a debugging point in your code.

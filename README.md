# Practice Code: Modern CMake
Delibrate practice project for updating skills on latest versions of CMake.

## Objectives
Configure and setup CMake to be able to build a C++ Windows console application using
Visual Studio Code on Windows 10.  In order to make this practice more interesting, the 
application must use the following dependent libraries.

- Boost C++
- ZLib
- Google Test
- Apache Arrow/Parquet

Initially, the binary versions of these libraries will be installed using Anaconda.  The
**conda** folder will hold the description of how the Anaconda enviroment can be created.

## Build Procedure
### Generation Step
Execute the following commands to generate the Visual Studio build files.

```mkdir build```
```cd build```
```cmake -G "Visual Studio 15 2017 Win64" -DCMAKE_BUILD_TYPE=Release ..```

## Setting Up GitHub/SSH/Visual Studio Code
The following link has the general information [Connecting to GitHub with SSH](https://help.github.com/articles/connecting-to-github-with-ssh/).  Execute the
following steps from this web page.
- Checking for existing SSH keys
- Generating a new SSH key and adding it to the ssh-agent
- Adding a new SSH key to your GitHub account
- Testing your SSH connection

### Switch to Windows SSH to prevent Authentication Errors
Once everything has been setup, we need to switch git to use the Windows version
of OpenSSH in order to make things work properly from a normal command window
that is used to launch Visual Studio Code.  The instructions on how to do this 
is document here [VSCode Issue #13680](https://github.com/Microsoft/vscode/issues/13680#issuecomment-414841885).  Below
is a brief outline of the steps/commands.

- Make Git use the Windows version of OpenSSH
  - ````git config --global core.sshCommand "C:/Windows/System32/OpenSSH/ssh.exe"````
- Set the ssh-agent service to run automatically
  - Open Task Manager, Services tab, click Open Services
  - Find OpenSSH Authentication Agent, open properties, set Startup Type to Automatic
  - Also start the service or restart the computer
- Add your password protected key to the agent
  - ````ssh-add````

This seems to work fine with Git for Windows (version 2.20.1).
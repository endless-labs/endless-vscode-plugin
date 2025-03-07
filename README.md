# endless-move-analyzer

## Table of Contents

- Introduction
- Features
- Installation

## Introduction
The `endless-move-analyzer` is a Visual Studio Code plugin for Move language developed by Endless.

## Installation
Note:

If you already have installed `aptos-move-analyzer` or `sui-move-analyzer`, please disable or uninstall them before installing `endless-move-analyzer`, because it may have some conflicts.

### How to Install (Must Read)
The `endless-move-analyzer` Visual Studio Code extension works via two type of components:
- `endless-move-analyzer language server`
- the VS Code extension itself ( move-analyzer.vsix and move-syntax.vsix)

That means we need to install both two components.

#### Installing `endless-move-analyzer language server`

- Ubuntu 24 X86-64: move-analyzer, md5 checksum: 466b3fa065245ab76d9ecb8cfbb20cd0
- Ubuntu 20 X86-64: move-analyzer, md5 checksum: 1df4cacb73a8e7a70f680d461507d5c4
- Windows10/11 X86-64: move-analyzer, md5 checksum: 9c621566fd23f02cdb014641f5c71bfa

Download and Install the precompiled binaries:  
- Download the binary files for your platform from the endless-move-analyzer release page.
- Rename the file to `move-analyzer`.
- Ensure `move-analyzer` is include in your system's PATH environment variable.

After completing the above steps, restart VS Code.

#### Installing VS Code extensions

Here, we need to install two extensions:
1. endless-move-syntax
2. endless-move-analyzer

The `endless-move-syntax` extension provides syntax highlighting, language support for The Move language, including support for defining structures, functions, and other keywords.

The `endless-move-analyzer` extension integrates with the language server to deliver comprehensive Move language support in VS Code.

VS Code extension is installed via:
1. manually installed in local VSIX file
2. VS Code Marketplace: Further instructions will be added once this section is finalized

**Installing the endless-move-syntax VS Code extension**

Using the Install from VSIX command in the Extensions view command dropdown, or the Extensions: Install from VSIX command in the Command Palette, point to the `move-syntax.vsix` file.

**Installing the endless-move-analyzer VS Code extension**

Using the Install from VSIX command in the Extensions view command dropdown, or the Extensions: Install from VSIX command in the Command Palette, point to the `move-analyzer.vsix` file.

Open any Move project directory(where the Move.toml is located), and open or create files that end in .move, you should see that keywords and types appear in different colors, and you can try other features.
After completing the above steps, restart VS Code.

At this point, the entire plugin is ready to use. The plugin offers a variety of settings that you can access by going to (Preferences > Settings*). Search for the endless-move-analyzer setting.

## Troubleshooting

### cannot find the `move-analyzer` program
For PATH reason
If you see an error message language server executable `move-analyzer` could not be found in the bottom-right of your Visual Studio Code screen when opening a Move file, it means that the `move-analyzer` executable could not be found in your PATH. You may try the following:

Confirm that invoking `move-analyzer --version` in a command line terminal prints out `move-analyzer` version number. 

If it doesn't, then retry the instructions in [Installing `endless-move-analyzer language server`](#installing-endless-move-analyzer-language-server). 

If it does successfully print this output, try closing and re-opening the Visual Studio Code application, as it may not have picked up the update to your PATH.

If you installed the endless-move-analyzer executable to a different location that is outside of your PATH, then you may have the extension look at this location by using the the Visual Studio Code settings (⌘, on macOS, or use the menu item Code > Preferences > Settings). Search for the endless-move-analyzer.server.path setting, and set it to the location of the `move-analyzer` you installed.

If you're using it in MacOS, you may meet the error Macos cannot verify if this app contains malicious software, you need to add support for endless-move-analyzer in the system settings Program Trust.

### analyzer not work

A. Need Move.toml
Open a Move source file (a file with a .move file extension) and if the opened Move source file is located within a buildable project (a Move.toml file can be found in one of its parent directories), the following advanced features will be available:

- compiler diagnostics
- go to definition
- go to references
- type on hover
- autocomplete
- outline view
- generate spec
...
Therefore, the Move.toml file must be found in the project directory for the plug-in's functionality to take effect.

In addition, if you have already opened the move project before, the installed plug-in will not take effect in time. You need to reopen the VS Code window and open the move project code again before the plug-in is activated.

B. Need Compile Project with Move.toml
When you first open a project, there will be some dependencies (configured in Move.toml) that need to be downloaded, so you need to run `endless move compile` command first to build the project. During the build process, the dependencies will be downloaded. Once all the dependencies for the project have been downloaded, endless-move-analyzer can properly parse the dependencies and project source code.
The npm/Microsoft/Google recommended **Node.js version manager for _Windows_**.

# This is not the same thing as [nvm](https://github.com/creationix/nvm), which is a completely separate project for Mac/Linux only.

Like this project? Let people know with a [tweet](https://twitter.com/intent/tweet?hashtags=nodejs&original_referer=http%3A%2F%2F127.0.0.1%3A91%2F&text=Check%20out%20NVM%20for%20Windows!&tw_p=tweetbutton&url=http%3A%2F%2Fgithub.com%2Fcoreybutler%2Fnvm-windows&via=goldglovecb). 

Better yet, **click the "Sponsor" button** at the top of this screen. Patreon sponsors will receive patron-only update posts.


## Common Issues & Resolutions

Please see the [Common Issues](https://github.com/coreybutler/nvm-windows/wiki/Common-Issues) page before posting an issue.

# Node Version Manager (nvm) for Windows

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/coreybutler/nvm-windows?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge) (I post development updates here)

![Issues](https://img.shields.io/github/issues/coreybutler/nvm-windows.svg)
![Stars](https://img.shields.io/github/stars/coreybutler/nvm-windows.svg)
[![Open Source Helpers](https://www.codetriage.com/coreybutler/nvm-windows/badges/users.svg)](https://www.codetriage.com/coreybutler/nvm-windows)

Manage multiple installations of node.js on a Windows computer.

**tl;dr** [nvm](https://github.com/creationix/nvm), but for Windows, with an installer. [Download Now](https://github.com/coreybutler/nvm-windows/releases)! This has always been a node version manager, not an io.js manager, so there is no back-support for io.js. However, node 4+ is supported.

![NVM for Windows](http://i.imgur.com/BNlcbi4.png)

There are situations where the ability to switch between different versions of Node.js can be very
useful. For example, if you want to test a module you're developing with the latest
bleeding edge version without uninstalling the stable version of node, this utility can help.

![Switch between stable and unstable versions.](http://i.imgur.com/zHEz8Oq.png)

### Installation & Upgrades

#### Uninstall existing node

Please note, you need to uninstall any existing versions of node.js before installing NVM for Windows. Also delete any existing nodejs installation directories (e.g., "C:\Program Files\nodejs") that might remain. NVM's generated symlink will not overwrite an existing (even empty) installation directory.

#### Uninstall existing npm

You should also delete the existing npm install location (e.g. "C:\Users\\&lt;user&gt;\\AppData\Roaming\npm"), so that the nvm install location will be correctly used instead. Backup the global `npmrc` config (e.g. `C:\Users\&lt;user&gt;\AppData\Roaming\npm\etc\npmrc`), if you have some important settings there, or copy the settings to the user config `C:\Users\&lt;user&gt;\.npmrc`.

#### Install nvm-windows

nvm-windows comes with an installer (and uninstaller), because getting it should be easy. 

#### Reinstall any global utilities

After install, reinstalling global utilities (e.g. gulp) will have to be done for each installed version of node:
```
nvm use 4.4.0
npm install gulp-cli -g
nvm use 0.10.33
npm install gulp-cli -g
```
[Download the latest installer from the releases](https://github.com/coreybutler/nvm/releases).

![NVM for Windows Installer](http://i.imgur.com/x8EzjSC.png)

### Upgrading nvm-windows

**To upgrade nvm-windows**, run the new installer. It will safely overwrite the files it needs to update without touching your node.js installations. Make sure you use the same installation and symlink folder. If you originally installed to the default locations, you just need to click "next" on each window until it finishes.

### Usage

**nvm-windows runs in an Admin shell**. You'll need to start `powershell` or Command Prompt as Administrator to use nvm-windows

NVM for Windows is a command line tool. Simply type `nvm` in the console for help. The basic commands are:

- `nvm arch [32|64]`: Show if node is running in 32 or 64 bit mode. Specify 32 or 64 to override the default architecture.
- `nvm install <version> [arch]`: The version can be a node.js version or "latest" for the latest stable version. Optionally specify whether to install the 32 or 64 bit version (defaults to system arch). Set `[arch]` to "all" to install 32 AND 64 bit versions.
- `nvm list [available]`: List the node.js installations. Type `available` at the end to show a list of versions available for download.
- `nvm on`: Enable node.js version management.
- `nvm off`: Disable node.js version management (does not uninstall anything).
- `nvm proxy [url]`: Set a proxy to use for downloads. Leave `[url]` blank to see the current proxy. Set `[url]` to "none" to remove the proxy.
- `nvm uninstall <version>`: Uninstall a specific version.
- `nvm use <version> [arch]`: Switch to use the specified version. Optionally specify 32/64bit architecture. `nvm use <arch>` will continue using the selected version, but switch to 32/64 bit mode based on the value supplied to `<arch>`. For information about using `use` in a specific directory (or using `.nvmrc`), please refer to [issue #16](https://github.com/coreybutler/nvm-windows/issues/16).
- `nvm root <path>`: Set the directory where nvm should store different versions of node.js. If `<path>` is not set, the current root will be displayed.
- `nvm version`: Displays the current running version of NVM for Windows.
- `nvm node_mirror <node_mirror_url>`: Set the node mirror.People in China can use *https://npm.taobao.org/mirrors/node/*
- `nvm npm_mirror <npm_mirror_url>`: Set the npm mirror.People in China can use *https://npm.taobao.org/mirrors/npm/*

### Gotcha!

Please note that any global npm modules you may have installed are **not** shared between the various versions of node.js you have installed. Additionally, some npm modules may not be supported in the version of node you're using, so be aware of your environment as you work.

### Antivirus

Users have reported some problems using antivirus, specifically McAfee. It appears the antivirus software is manipulating access to the VBScript engine. See [issue #133](https://github.com/coreybutler/nvm-windows/issues/133) for details and resolution.

As of 1.1.7, the executable and installation files are code-signed by [Ecor Ventures LLC](https://ecorventures.com)/[Author.io](https://author.io). This should help prevent false positives with most antivirus software.

### Using Yarn

**tldr;** `npm i -g yarn`

See the [wiki](https://github.com/coreybutler/nvm-windows/wiki/Common-Issues#how-do-i-use-yarn-with-nvm-windows) for details.

### Build from source

- Install go from http://golang.org
- Download source / Git Clone the repo
- Change GOARCH to amd64 in build.bat if you feel like building a 64-bit executable
- Fire up a Windows command prompt and change directory to project dir
- Execute `go get github.com/blang/semver`
- Execute `go get github.com/olekukonko/tablewriter`
- Execute `build.bat`
- Check the `dist`directory for generated setup program. 


---



## Errror for node_modules/** no found 解决方案：

由于翻墙限制 `nvm` 下载的依赖包不完整， 需要手动下载（覆盖）才能使用

- 1. 下载 `nvm` 安装版
- 2. 下载指定的 `Node` 版本（最好是非安装版）http://nodejs.cn/download/ 
- 3. 打开 `nvm` 文件路径 （C:\Users\USER_NAME\AppData\Roaming\nvm\）
- 4. 在 `nvm` 路径中把第1步下载的node放置 `nvm` 根目录 并改名如：v12.6.0
- 5. 如需下载多个版本重复上面步骤即可
- 6. 通过 `nvm list` 验证是否有对应的 `Node` 版本， `nvm use 12.6.0` 进行切换


cppcryptfs Build and Installation
--------------

You will need the following software, **all available for free**, to build cppcryptfs:

Microsoft Visual Studio 2019 Community Edition, perl, nasm, and git. git is optional.


You will also need to install Dokany.

You will need to download the source code for the OpenSSL and RapidJSON projects from github.  

Only OpenSSL needs to be built separately.  cppcryptfs uses only header files from RapidJSON, so you don't need to build RapidJSON.

You will also need Microsoft Visual Studio 2019.

The Community Edition of Microsoft Visual Studio 2019 will work, and it is free.

https://www.visualstudio.com/vs/community/

The professional edition or the enterprise edition should be fine if you already have either of those.

You need to install Visual Studio in such a way that you can compile C++ applications with support for Microsoft Foundation Classes (MFC).  

When installing Visual Studio 2019, select "Desktop development with C++", and be sure that both ATL and MFC support are selected.

Here is a screenshot that shows what to select when installing Visual Studio.

[Visual Studio install screenshot](/screenshots/visual_studio_2019_install.png?raw=true) 

Also, the Visual Studio projects that make up cppcryptfs all use the /Qspectre
flag for Spectre mitigation.  For this to be effective (and for the build to work starting with Visual Studio 2019), you will need to install the Spectre-mitigated libraries from Microsoft. Thise can be selected when you instal Visual Studio 2019 or installed later by running the Visual Studio 2019 installation program again. 


[Visual Studio install Spectre-mitigated libraries screenshot 1](/screenshots/visual_studio_2019_spectre_libs1.png?raw=true) 

[scroll down to get to the selections in the next screenshot]

[Visual Studio install Spectre-mitigated libraries screenshot 2](/screenshots/visual_studio_2019_spectre_libs2.png?raw=true) 

In order to build OpenSSL, you will also need perl and nasm.  

For Perl, the OpenSSL documentation recommends using the free ActiveState ActivePerl.

http://www.activestate.com/activeperl/downloads

nasm (The Netwide Assembler) is available from here http://www.nasm.us/.  There should be a link to the latest stable version in the middle of page.  Using the nasm installer is recommended if you want to be able to follow these build instructions verbatim. 

Note: You should run the nasm installer as your normal user.  When it prompts you to re-run the installer as administrator, just press ok.  This will cause nasm to be installed in the place where these instructions expect it to be installed (under the current user's local appdata directory).

Git is available from https://git-scm.com/downloads

The git that comes with cygwin also works.  

You don't need git if you download the source zip files from github
and unzip them.

These instructions assume that you are using git.  You don't need to have a github account to use git.


Dokany
------
Unless you want to develop or debug Dokany, you should just install one of the Dokany release binaries from here.

https://github.com/dokan-dev/dokany/releases

Using DokanSetup_redist.exe is probably the safest bet. Be sure to go into the installer options and select "install development files".

OpenSSL
---------
cppcryptfs uses OpenSSL for doing the actual encrypting and decrypting of data.

You will need to build OpenSSL from its source code.

Please refer to the "INSTALL" file from the OpenSSL distribution if these instructions don't work.

After installing Visual Studio, nasm, git, and ActiveState perl, open a new Windows command prompt (cmd.exe).

You will need an elevated (administrator) command prompt for running the command that installs OpenSSL.  You can build it in a normal command prompt, though.

To start an elevated command prompt in Windows 10, click on the search (magnifying glass) icon in the lower left of the screen and type "cmd". Then right-click on "Command Prompt" and select "Run as administrator".

[how to start an elevated command prompt screenshot](/screenshots/cmd_as_administrator.png?raw=true)

Whether or not you are using git, everything will go easier if you put everything in c:\git.

Getting OpenSSL from github will get you the latest development version of OpenSSL.  However, the cppcryptfs releases are built using the
current 1.1.1x Long Term Support (LTS) version of OpenSSL (currently openssl-1.1.1m).  These are available from https://www.openssl.org/source/.  To use those, you will need to download
the .tar.gz and extract it into a directory.  You can build it with the same instructions that follow regardless of how you get OpenSSL.

Microsoft has announced a compiler-based mitigation for one variant of the Spectre vulnerability.  To use it, you need to have version 15.5 or higher of Visual Studio.  To use the mitigation with OpenSSL, you need to add the /Qspectre flag to the compiler optimization flags.  OpenSSL currently does not use this flag.  Also, to be extra safe, add the /guard:cf (Control Flow Guard) flag.  To use these, you need to edit c:\\git\openssl\\Configurations\\10-main.conf and change "/O2" to "/O2 /Qspectre /guard:cf".  


Run this command to put nasm in your path (assuming you used the nasm installer).


```
set PATH=%LOCALAPPDATA%\bin\NASM;%PATH%
```


Then run the batch file that comes with Visual Studio that sets up the environment variables for compiling from the command line.

```
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64

```

Use "x86" in place of "amd64" if you are doing a 32-bit build.

The vcvarsall.bat from Visual Studio 2019 must be run in a Windows cmd.exe command shell.  It doesn't like being run in third-party command shells.


Then run (ActiveState) perl to configure OpenSSL for a Visual Studio AMD64/X86_64 static build.  

Use "VC-WIN32" instead of  "VC-WIN64A" if you're doing a 32-bit build.


```
perl Configure VC-WIN64A no-shared
```

Then run "nmake" to build OpenSSL.


```
nmake
```

Then run "nmake install" to install it.  


```
nmake install
```

nmake install must be run from an elevated (administrator) command prompt in order for it to work.  If you built OpenSSL from a non-elevated command prompt, then start an elevated one, cd to c:\git\openssl, and be sure to invoke vcvarsall.bat as shown above again in the elevated command prompt before running nmake install in it. 

There might be errors about installing the OpenSSL documentation.  They won't affect your ability to build cppcryptfs.

RapidJSON
------

RapidJSON is used for parsing the config file gocryptfs.conf.  cppcryptfs uses only header files from RapidJSON, so there is no need to build RapidJSON separately.

```
c:
cd \git
git clone https://github.com/Tencent/rapidjson.git
```

cppcryptfs
----------
First, clone cppcryptfs.

```
c:
cd \git
git clone https://github.com/bailey27/cppcryptfs.git
```

Then go to c:\\git\\cppcryptfs in Windows Explorer and double-click on cppcryptfs.sln.  This will load the project into Visual Studio.

Then change the build configuration to "Release" and the target platform to "x64". Select "x86" instead of "x64" if you are doing a 32-bit build.

Here is a screenshot that shows where to set the build configuration and target platform (see the red underlines).

[Visual Studio build configuration and target platform screenshot](/screenshots/build_config_and_target.png?raw=true) 

Then do Build -> Build Solution, or just press the F7 key.

You may get an compilation error in atlenc.h.  This file is from Microsoft.  They may have fixed the problem by the time you read this.

If you get a compilation error on line 726 of atlenc.h, then you need to start a text editor as administrator and edit the file.

change on line 726

```
char* tmp = '\0';

```

to

```
char* tmp = nullptr;

```

and build again.



There is no installation program for cppcryptfs.  You will need to copy cppcryptfs.exe (e.g. C:\\git\\cppcryptfs\\x64\\Release\\cppcryptfs.exe) to some directory in your path or onto your desktop.


Whenever Dokany releases a new version, they install their header (include) and library files in a path that has the Dokany version number in its name.  Therefore, if cppcryptfs gets behind the current Dokany version, even a minor one, then you will need to change the include and library paths in the cppcryptfs Visual Studio project.  

To change the include path in Visual Studio, right click on "cppcryptfs" in the Solution Explorer pane.  Then select "Properties" and go to "C/C++" then "General".  Then edit "Additional Include Directories" so that the current Dokany version is there in the path for the Dokany header files.  Make sure you have selected the Configuration and Platform that you are actually building for when you do this.

To change the library path, go to "Linker" and then "Input" and edit "Additional Dependencies".

Here are links to screenshots: 

[Visual Studio include paths screenshot](/screenshots/include_paths.png?raw=true) 

[Visual Studio library paths screenshot](/screenshots/library_paths.png?raw=true) 

The screenshots were made with Visual Studio 2015 when Dokany 1.0.2 was the Dokany version that cppcryptfs was expecting to use, but Dokany 1.0.3 was installed.  The UI for changing these things in Visual Studio 2019 is the same.



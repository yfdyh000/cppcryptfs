cppcryptfs 的构建和所需环境
--------------

构建 cppcryptfs 需要下列软件（**均可免费下载**）：

Microsoft Visual Studio 2019 社区版、perl、nasm 和 git。git 是可选的。


您还需要安装 Dokany。

您需要从 Github 下载 OpenSSL 和 RapidJSON 项目的源代码。

只有 OpenSSL 需要单独构建。cppcryptfs 仅使用 RapidJSON 的头文件，因此不需要构建 RapidJSON。

您还需要 Microsoft Visual Studio 2019。

Microsoft Visual Studio 2019 的社区版就已足够，并且它是免费的。

https://www.visualstudio.com/vs/community/

如果您已拥有并使用专业版或企业版，那应该也没问题。

您需要按正确的方式安装 Visual Studio，以便可以编译需要 Microsoft 基础类（MFC）支持的 C++ 应用程序。

安装 Visual Studio 2019 时，请选中“使用 C++ 进行桌面开发”，并确保同时选中了 ATL 和 MFC 支持。

下方的屏幕截图展示了安装 Visual Studio 时需要选中的内容。

[Visual Studio 安装屏幕截图](/screenshots/visual_studio_2019_install.png?raw=true)

另外，制作 cppcryptfs 的 Visual Studio 项目都使用 /Qspectre 标志来缓解 Spectre 漏洞。为了使此功能生效、使构建正常完成，您需要安装微软的 Spectre 缓解库。这些库可以在安装 Visual Studio 2019 时选中，也可以再次运行 Visual Studio 2019 安装程序来安装。


[Visual Studio install Spectre-mitigated libraries screenshot 1](/screenshots/visual_studio_2019_spectre_libs1.png?raw=true)

[向下滚动查看下一张截图中的选项]

[Visual Studio install Spectre-mitigated libraries screenshot 2](/screenshots/visual_studio_2019_spectre_libs2.png?raw=true)

为了构建 OpenSSL，你还需要 perl 和 nasm。

对于 Perl，OpenSSL 文档建议使用免费的 ActiveState ActivePerl。

http://www.activestate.com/activeperl/downloads

nasm（The Netwide Assembler）可从 http://www.nasm.us/ 取得。页面中间应该有一个指向最新稳定版本的链接。如果您希望完全按照本构建说明操作，建议使用 nasm 安装程序。

注意：您应该以普通用户身份运行 nasm 安装程序。当它提示您以管理员权限重新运行安装程序时，只需按确定（ok）。这样 nasm 才能安装在本说明文档所期望的位置（当前用户的本地 appdata 目录下）。

Git 可从 https://git-scm.com/downloads 取得

cygwin 附带的 git 也可以用。

如果您从 Github 下载源代码 zip 文件，则不需要 git，只需将其解压缩。

本说明假定您在使用 git。使用 git 无需拥有 github 帐户。


Dokany
------
除非您想开发或调试 Dokany，否则您应该从此处安装 Dokany 发布的二进制文件。

https://github.com/dokan-dev/dokany/releases

使用 DokanSetup_redist.exe 可能是最稳妥的选择。请务必进入安装程序选项，然后选择“安装开发文件（install development files）”。

OpenSSL
---------
cppcryptfs 使用 OpenSSL 对数据进行实际的加密和解密。

您将需要构建 OpenSSL 的源代码。

如果这些说明不起效果，请参照 OpenSSL 发行版中的“INSTALL”文件。

安装 Visual Studio、nasm、git 和 ActiveState perl 后，打开新的 Windows 命令提示符（cmd.exe）。

您需要有一个提升到管理员权限的命令提示符才能运行安装 OpenSSL 的命令。不过，也可以在普通的命令提示符下构建。

要在 Windows 10 中启动提升权限的命令提示符，请单击屏幕左下角的搜索（放大镜）图标，键入“cmd”。然后右键单击“命令提示符”并选择“以管理员身份运行”。

[如何启动提升权限的命令提示符的屏幕截图](/screenshots/cmd_as_administrator.png?raw=true)

无论你是否使用 git，如果你将所有东西都放在 c:\git 中，一切都能更容易。

从 Github 获取 OpenSSL 将为您提供 OpenSSL 的最新开发版本。 但是，cppcryptfs 的发布版本使用的是 OpenSSL 目前的 1.1.1x 长期支持（LTS）版本（当前为 openssl-1.1.1m）。它可从 https://www.openssl.org/source/ 取得。要使用它们，需要下载其 .tar.gz 文件并将其解压缩到一个目录。无论您如何取得 OpenSSL，都可以使用下列说明来构建它。

微软已经宣布了针对 Spectre 漏洞变体之一的一个基于编译器的缓解措施。如要使用它，您需要使用 Visual Studio 的 15.5 或更高版本。如要将缓解措施与 OpenSSL 结合使用，需要将 /Qspectre 标志添加到编译器的优化标志。OpenSSL 目前不使用此标志。此外，为了更加安全，请添加 /guard:cf（控制流防护）标志。为了使用它，需要编辑 c:\\git\openssl\\Configurations\\10-main.conf 并将 "/O2" 更改为 "/O2 /Qspectre /guard:cf"。


运行此命令以将 nasm 放在您的路径中（假设您使用了 nasm 安装程序）。


```
set PATH=%LOCALAPPDATA%\bin\NASM;%PATH%
```


然后运行 Visual Studio 随附的批处理文件，该文件将设置从命令行进行编译所需的环境变量。

```
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64

```

如果您要构建 32 位版本，使用“x86”代替“amd64”。

Visual Studio 2019 中的 vcvarsall.bat 必须在 Windows 的 cmd.exe 中运行，它不适合在第三方的 shell 中运行。


然后运行（ActiveState）perl 以为 Visual Studio AMD64 / X86_64 静态构建配置 OpenSSL。

如果您正在进行 32 位构建，使用“VC-WIN32”而不是“VC-WIN64A”。


```
perl Configure VC-WIN64A no-shared
```

然后运行“nmake”来构建 OpenSSL。


```
nmake
```

然后运行“nmake install”来安装。


```
nmake install
```

必须从提升权限的命令提示符运行 nmake 安装。如果您之前从未提升权限的命令提示符构建了 OpenSSL，请启动提升权限的命令提示符，用 cd 命令切换到 c:\git\openssl，然后在运行 nmake install 前再次调用上文所述的 vcvarsall.bat 文件。

安装 OpenSSL 文档期间可能有一些错误。但这不影响您构建 cppcryptfs 的过程。

RapidJSON
------

RapidJSON 是用于解析配置文件 gocryptfs.conf。cppcryptfs 仅使用 RapidJSON 中的头文件，因此无需单独构建 RapidJSON。

```
c:
cd \git
git clone https://github.com/Tencent/rapidjson.git
```

cppcryptfs
----------
首先，克隆（clone） cppcryptfs 项目。

```
c:
cd \git
git clone https://github.com/bailey27/cppcryptfs.git
```

然后在 Windows 资源管理器中打开 c：\\git\\cppcryptfs 目录，双击 cppcryptfs.sln。这样项目就将在 Visual Studio 中加载。

然后将构建配置更改为“发布”，将目标平台更改为“x64”。如果要构建 32 位版本，选择“x86”。

下面是一个屏幕截图，显示了在何处设置构建配置和目标平台（参阅红色下划线）。

[Visual Studio 构建配置和目标平台的屏幕截图](/screenshots/build_config_and_target.png?raw=true)

然后点击"构建->构建解决方案"，或者直接按 F7 键。

您可能会在 atlenc.h 中遇到一个编译错误。此文件来自微软。当您阅读本文时，他们可能已经修正了该问题。

如果在 atlenc.h 的第 726 行遇到编译错误，需要以管理员身份启动一个文本编辑器并编辑该文件。

在第 726 行将

```
char* tmp = '\0';

```

更改为

```
char* tmp = nullptr;

```

并再次构建。



cppcryptfs 没有安装程序。只需要将 cppcryptfs.exe（例如 C:\\git\\cppcryptfs\\x64\\Release\\cppcryptfs.exe）复制到您需要的位置（例如桌面）。


每次 Dokany 发布新版本时，安装程序会将其头（include）和库文件安装到一个名字+版本号的位置。因此，如果 cppcryptfs 使用的版本与您所用的当前 Dokany 版本不符，您将需要更改 cppcryptfs 的 Visual Studio 项目中的包含和库路径。

为了在 Visual Studio 中更改包含路径，请右击“解决方案资源管理器”窗格中的“cppcryptfs”。然后选择“属性”并转到“C/C++”，选择“常规”。然后编辑“额外包含目录”，使 Dokany 头文件所在的当前的 Dokany 版本构成的目录名称位于该路径框中。执行此操作时，先确保选中将要构建的“配置”和“平台”。

要更改库路径，转到“链接器”，然后转到“输入”并编辑“其他依赖项”。

以下是屏幕截图的链接：

[Visual Studio 中 include 路径的屏幕截图](/screenshots/include_paths.png?raw=true)

[Visual Studio 中库路径的屏幕截图](/screenshots/library_paths.png?raw=true)

截图是中的是 Visual Studio 2015，当时 cppcryptfs 预期使用的是 Dokany 1.0.2 版本，但安装了 Dokany 1.0.3。Visual Studio 2019 中更改这些内容的界面没有变化。



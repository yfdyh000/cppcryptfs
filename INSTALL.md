cppcryptfs �Ĺ��������軷��
--------------

���� cppcryptfs ��Ҫ���������**�����������**����

Microsoft Visual Studio 2019 �����桢perl��nasm �� git��git �ǿ�ѡ�ġ�


������Ҫ��װ Dokany��

����Ҫ�� Github ���� OpenSSL �� RapidJSON ��Ŀ��Դ���롣

ֻ�� OpenSSL ��Ҫ����������cppcryptfs ��ʹ�� RapidJSON ��ͷ�ļ�����˲���Ҫ���� RapidJSON��

������Ҫ Microsoft Visual Studio 2019��

Microsoft Visual Studio 2019 ������������㹻������������ѵġ�

https://www.visualstudio.com/vs/community/

�������ӵ�в�ʹ��רҵ�����ҵ�棬��Ӧ��Ҳû���⡣

����Ҫ����ȷ�ķ�ʽ��װ Visual Studio���Ա���Ա�����Ҫ Microsoft �����ࣨMFC��֧�ֵ� C++ Ӧ�ó���

��װ Visual Studio 2019 ʱ����ѡ�С�ʹ�� C++ �������濪��������ȷ��ͬʱѡ���� ATL �� MFC ֧�֡�

�·�����Ļ��ͼչʾ�˰�װ Visual Studio ʱ��Ҫѡ�е����ݡ�

[Visual Studio ��װ��Ļ��ͼ](/screenshots/visual_studio_2019_install.png?raw=true)

���⣬���� cppcryptfs �� Visual Studio ��Ŀ��ʹ�� /Qspectre ��־������ Spectre ©����Ϊ��ʹ�˹�����Ч��ʹ����������ɣ�����Ҫ��װ΢��� Spectre ����⡣��Щ������ڰ�װ Visual Studio 2019 ʱѡ�У�Ҳ�����ٴ����� Visual Studio 2019 ��װ��������װ��


[Visual Studio install Spectre-mitigated libraries screenshot 1](/screenshots/visual_studio_2019_spectre_libs1.png?raw=true)

[���¹����鿴��һ�Ž�ͼ�е�ѡ��]

[Visual Studio install Spectre-mitigated libraries screenshot 2](/screenshots/visual_studio_2019_spectre_libs2.png?raw=true)

Ϊ�˹��� OpenSSL���㻹��Ҫ perl �� nasm��

���� Perl��OpenSSL �ĵ�����ʹ����ѵ� ActiveState ActivePerl��

http://www.activestate.com/activeperl/downloads

nasm��The Netwide Assembler���ɴ� http://www.nasm.us/ ȡ�á�ҳ���м�Ӧ����һ��ָ�������ȶ��汾�����ӡ������ϣ����ȫ���ձ�����˵������������ʹ�� nasm ��װ����

ע�⣺��Ӧ������ͨ�û�������� nasm ��װ���򡣵�����ʾ���Թ���ԱȨ���������а�װ����ʱ��ֻ�谴ȷ����ok�������� nasm ���ܰ�װ�ڱ�˵���ĵ���������λ�ã���ǰ�û��ı��� appdata Ŀ¼�£���

Git �ɴ� https://git-scm.com/downloads ȡ��

cygwin ������ git Ҳ�����á�

������� Github ����Դ���� zip �ļ�������Ҫ git��ֻ�轫���ѹ����

��˵���ٶ�����ʹ�� git��ʹ�� git ����ӵ�� github �ʻ���


Dokany
------
�������뿪������� Dokany��������Ӧ�ôӴ˴���װ Dokany �����Ķ������ļ���

https://github.com/dokan-dev/dokany/releases

ʹ�� DokanSetup_redist.exe �����������׵�ѡ������ؽ��밲װ����ѡ�Ȼ��ѡ�񡰰�װ�����ļ���install development files������

OpenSSL
---------
cppcryptfs ʹ�� OpenSSL �����ݽ���ʵ�ʵļ��ܺͽ��ܡ�

������Ҫ���� OpenSSL ��Դ���롣

�����Щ˵������Ч��������� OpenSSL ���а��еġ�INSTALL���ļ���

��װ Visual Studio��nasm��git �� ActiveState perl �󣬴��µ� Windows ������ʾ����cmd.exe����

����Ҫ��һ������������ԱȨ�޵�������ʾ���������а�װ OpenSSL �����������Ҳ��������ͨ��������ʾ���¹�����

Ҫ�� Windows 10 ����������Ȩ�޵�������ʾ�����뵥����Ļ���½ǵ��������Ŵ󾵣�ͼ�꣬���롰cmd����Ȼ���Ҽ�������������ʾ������ѡ���Թ���Ա������С���

[�����������Ȩ�޵�������ʾ������Ļ��ͼ](/screenshots/cmd_as_administrator.png?raw=true)

�������Ƿ�ʹ�� git������㽫���ж��������� c:\git �У�һ�ж��ܸ����ס�

�� Github ��ȡ OpenSSL ��Ϊ���ṩ OpenSSL �����¿����汾�� ���ǣ�cppcryptfs �ķ����汾ʹ�õ��� OpenSSL Ŀǰ�� 1.1.1x ����֧�֣�LTS���汾����ǰΪ openssl-1.1.1m�������ɴ� https://www.openssl.org/source/ ȡ�á�Ҫʹ�����ǣ���Ҫ������ .tar.gz �ļ��������ѹ����һ��Ŀ¼�����������ȡ�� OpenSSL��������ʹ������˵������������

΢���Ѿ���������� Spectre ©������֮һ��һ�����ڱ������Ļ����ʩ����Ҫʹ����������Ҫʹ�� Visual Studio �� 15.5 ����߰汾����Ҫ�������ʩ�� OpenSSL ���ʹ�ã���Ҫ�� /Qspectre ��־��ӵ����������Ż���־��OpenSSL Ŀǰ��ʹ�ô˱�־�����⣬Ϊ�˸��Ӱ�ȫ������� /guard:cf����������������־��Ϊ��ʹ��������Ҫ�༭ c:\\git\openssl\\Configurations\\10-main.conf ���� "/O2" ����Ϊ "/O2 /Qspectre /guard:cf"��


���д������Խ� nasm ��������·���У�������ʹ���� nasm ��װ���򣩡�


```
set PATH=%LOCALAPPDATA%\bin\NASM;%PATH%
```


Ȼ������ Visual Studio �渽���������ļ������ļ������ô������н��б�������Ļ���������

```
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64

```

�����Ҫ���� 32 λ�汾��ʹ�á�x86�����桰amd64����

Visual Studio 2019 �е� vcvarsall.bat ������ Windows �� cmd.exe �����У������ʺ��ڵ������� shell �����С�


Ȼ�����У�ActiveState��perl ��Ϊ Visual Studio AMD64 / X86_64 ��̬�������� OpenSSL��

��������ڽ��� 32 λ������ʹ�á�VC-WIN32�������ǡ�VC-WIN64A����


```
perl Configure VC-WIN64A no-shared
```

Ȼ�����С�nmake�������� OpenSSL��


```
nmake
```

Ȼ�����С�nmake install������װ��


```
nmake install
```

���������Ȩ�޵�������ʾ������ nmake ��װ�������֮ǰ��δ����Ȩ�޵�������ʾ�������� OpenSSL������������Ȩ�޵�������ʾ������ cd �����л��� c:\git\openssl��Ȼ�������� nmake install ǰ�ٴε������������� vcvarsall.bat �ļ���

��װ OpenSSL �ĵ��ڼ������һЩ���󡣵��ⲻӰ�������� cppcryptfs �Ĺ��̡�

RapidJSON
------

RapidJSON �����ڽ��������ļ� gocryptfs.conf��cppcryptfs ��ʹ�� RapidJSON �е�ͷ�ļ���������赥������ RapidJSON��

```
c:
cd \git
git clone https://github.com/Tencent/rapidjson.git
```

cppcryptfs
----------
���ȣ���¡��clone�� cppcryptfs ��Ŀ��

```
c:
cd \git
git clone https://github.com/bailey27/cppcryptfs.git
```

Ȼ���� Windows ��Դ�������д� c��\\git\\cppcryptfs Ŀ¼��˫�� cppcryptfs.sln��������Ŀ�ͽ��� Visual Studio �м��ء�

Ȼ�󽫹������ø���Ϊ������������Ŀ��ƽ̨����Ϊ��x64�������Ҫ���� 32 λ�汾��ѡ��x86����

������һ����Ļ��ͼ����ʾ���ںδ����ù������ú�Ŀ��ƽ̨�����ĺ�ɫ�»��ߣ���

[Visual Studio �������ú�Ŀ��ƽ̨����Ļ��ͼ](/screenshots/build_config_and_target.png?raw=true)

Ȼ����"����->�����������"������ֱ�Ӱ� F7 ����

�����ܻ��� atlenc.h ������һ��������󡣴��ļ�����΢�������Ķ�����ʱ�����ǿ����Ѿ������˸����⡣

����� atlenc.h �ĵ� 726 ���������������Ҫ�Թ���Ա�������һ���ı��༭�����༭���ļ���

�ڵ� 726 �н�

```
char* tmp = '\0';

```

����Ϊ

```
char* tmp = nullptr;

```

���ٴι�����



cppcryptfs û�а�װ����ֻ��Ҫ�� cppcryptfs.exe������ C:\\git\\cppcryptfs\\x64\\Release\\cppcryptfs.exe�����Ƶ�����Ҫ��λ�ã��������棩��


ÿ�� Dokany �����°汾ʱ����װ����Ὣ��ͷ��include���Ϳ��ļ���װ��һ������+�汾�ŵ�λ�á���ˣ���� cppcryptfs ʹ�õİ汾�������õĵ�ǰ Dokany �汾������������Ҫ���� cppcryptfs �� Visual Studio ��Ŀ�еİ����Ϳ�·����

Ϊ���� Visual Studio �и��İ���·�������һ������������Դ�������������еġ�cppcryptfs����Ȼ��ѡ�����ԡ���ת����C/C++����ѡ�񡰳��桱��Ȼ��༭���������Ŀ¼����ʹ Dokany ͷ�ļ����ڵĵ�ǰ�� Dokany �汾���ɵ�Ŀ¼����λ�ڸ�·�����С�ִ�д˲���ʱ����ȷ��ѡ�н�Ҫ�����ġ����á��͡�ƽ̨����

Ҫ���Ŀ�·����ת��������������Ȼ��ת�������롱���༭�������������

��������Ļ��ͼ�����ӣ�

[Visual Studio �� include ·������Ļ��ͼ](/screenshots/include_paths.png?raw=true)

[Visual Studio �п�·������Ļ��ͼ](/screenshots/library_paths.png?raw=true)

��ͼ���е��� Visual Studio 2015����ʱ cppcryptfs Ԥ��ʹ�õ��� Dokany 1.0.2 �汾������װ�� Dokany 1.0.3��Visual Studio 2019 �и�����Щ���ݵĽ���û�б仯��



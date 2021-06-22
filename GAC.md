# GAC的主要功能

### 文件的完整性检查
### 内存完整性检查
### 作弊工具的字符串检测
### 反调试
    检测调试器的四种基本方法
* ``BOOL IsDebuggerPresent();``
* ``BOOL CheckRemoteDebuggerPresent(HANDLE hProcess,PBOOL  pbDebuggerPresent);``
* 检查PEB中的正在调试标志 
    ```cpp
    typedef struct _PEB
    {
        BOOLEAN InheritedAddressSpace; 
        BOOLEAN ReadImageFileExecOptions;
        BOOLEAN BeingDebugged; //0x3
        //etc... 
    }
    ```
    可通过读取FS寄存器偏移量0x30/0x60，得到PEB地址。
    ``` cpp
     __readfsdword(0x30); //x86 
     __readgsqword(0x60); //x64
    ```
   ***上述三种检测方法都是基于``PEB.BeingDebugged``,绕过只需将``PEB.BeingDebugged``标志覆盖为``0``。***

### 混淆
### 基于文件签名的检测
### 虚拟化检测
### 阻止进程访问令牌创建等的内核驱动程序
### DLL注入检测
### 线程注入检测
### 有害线程检测
### 虚拟内存代码注入检测
### 虚拟内存代码修改检测
### 虚拟内存模块完整性保护
### 虚拟内存挂钩和断点和转储保护
### 游戏内有害窗口检测
### 鼠标和键盘自动化检测
### 游戏内键盘劫持检测
### 软硬件宏检测
### 多客户端检测
### 检测/拒绝/分析游戏进程内存访问
### 检测/拒绝/分析游戏进程句柄访问
### 检测/拒绝内核和用户模式调试
### 基于硬件信息的封禁系统
### 启发式检测
### 常见检查；文件、驱动程序、句柄、堆、模块、系统对象、进程、虚拟内存部分、线程、窗口
### 启动界面
### 游戏特定保护方法
### 特殊的ring3访问保护



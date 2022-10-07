# Enterprise-WeChat-hook
企业微信hook,企业微信hook开源,企业微信hook教程,企业微信hook地址,企业微信hook 框架,企业微信hook 加好友,企业微信hook聊天记录,企业微信hook 电脑端,企业微信hook接受消息延迟,企业微信hook教程 百度网盘,企业微信hook接收消息
在介绍完 Inline Hook对本进程进行HOOK和对其他进程进行HOOK的实例。
1.	Hook MessageBoxA 函数本小节将完成一个HOOK本进程MessageBoxAO的程序，这个程序的目的是测试类是否封装成功，以便完成今后的程序。在VC6下创建一个控制台程序，添加好封装过的库，然后的键入下面代码：

＃include "ILHook.h"／／
创建一个全局的变量CILHook MsgHook;＃include <Windows.h>
intWINAPIMyMessageBoxA(HWND hWnd,LPCSTR 1pText,LPCSTR 1pCaption,UINT uType)
／／ 恢复 HOOKMsgHook. UnHook () ;MessageBox(hWnd, "Hook 流程＂， 1pCaption, uType);MessageBox (hWnd, 1pText, 1pCaption, uType);／／ 
重新 HOOKMsgHook. ReHook () ;

int main ()
／／ 不进行HOOK的MessageBoxMessageBox(NULL, "正常流程1", "test",MB_OK);／／ HOOK后的MessageBoxMsgHook. Hook ("User32.d11", "MessageBoxA", (PROC)MyMessageBoxA);MessageBox(NULL,"被HOOK了1", "test", MB_OK);MessageBox(NULL,"被HOOK了2", "test", MB_OK);MsgHook. UnHook () ;
MessageBox(NULL,"正常流程2","test", MB_OK);
return 0;

在主函数中调用了4次MessageBox(函数，每次弹出的内容分别是“正常流程1”“被HOOK了1”“被HOOK了2”和“正常流程2”。在MyMessageBoxAO函数中，分别调用两次MessageBox函数，并且分别输出“Hook流程”和MyMessageBoxA()函数的参数。从主函数的流程结构来看，并没有调用自己实现的MyMessageBoxA()函数。编译连接并运行自己的程序，从程序的执行结果来看，一共出现了6次由MessageBox(函数产生的对话框。这说明Inline Hook完成了。
注：在自己实现的Hook 函数中要调用原来的API函数，需要恢复Inline Hook,否则将是一个死循环。比如自己实现的MyMessageBoxA0是用来 HOOK MessageBoxA0函数的，在MyMessageBoxA0中调用MessageBoxA0函数时，需要恢复 MessageBoxA0不被Hook,否则对MessageBoxA0函数的调用一直会进入MyMessageBoxA(函数而无法弹出对话框。这里介绍了关于本进程的Inline Hook的例子，接下来要介绍的是其他进程 Inline Hadk的例子。由于每个进程的地址空间是隔离的，那么其他进程的Inline是需要用到DLL文件的。下面介绍如何使用DLL文件来完成对其他进程的Inline Hook的工作。2.Hook CreateProcessW函数Hook
2.	Hook CreateProcessW 函数在这个例子中，先写一个DLL,然后通过 DLL来 HOOK CreateProcessWO通费：Windows下，大部分应用程序都是由Explorer.exe进程来创建的。这里用“＂Process Explare工具来查看一下，如图7-6所示。
![image](https://user-images.githubusercontent.com/73727649/194449281-2e39f3ff-212d-468e-ab5e-fdbd8f6a1ba0.png)
从图7-6中可以看出，大部分应用程序都是由 Explorer.exe 进程创建的，那么只？Explorer.exe进程的CreateProcessWO函数HOOK住，就可以针对要完成的工作做很多事情了。比如，可以记录哪个应用程序被启动，也可以对应用程序进程进行拦截。这里的例子就是通过HOOK CreateProcessWO函数来显示被创建的进程名。

｝HOOK,并定义一个Hook函数就可以了。将这段代码编译连接，然后用第3章中编写的DL注入工具将这个DLL文件注入 explorer.exe中，如图7-7所示。将这个DLL注入 Explorer.exe进程后，运行一下IE浏览器，会弹出一个对话框，如图7-8所示。代码不是很长，Hook 功能是由前面封装过的类来完成的，只要使用封装好的类进行。

279编译连接这个程序，提示连接错误。原因是刚才编译连接的DLL文件正在被使用，所以无法对其修改。用DLL注入工具将刚才的DLL进行卸载，然后再次编译连接，这次就通过了。把新生成的DLL文件再次注入Explorer.exe进程中，然后启动记事本程序，如图7-9所示。单击“是”按钮，那么记事本程序被创建。如果单击“否”按钮，那么会提示“您启动的程序被拦截”，并且记事本程序没有被打开。单击“否”按钮，效果如图7-10所示。第7章 黑提示C|WINDOWS|system32\notepadexe"x
C: WINDOWSsystem32hotepad.exe
出现提示框，单击“确定”按钮以后，记事本程序没有被打开。再对IE浏览器、计算器、面图等程序进行测试。测试的结果都和记事本程序的结果是一样的，说明对应用程序创建的栏截功能已经成功。该例子程序完成了对其他进程的Inline Hook的操作，关于Inline Hook的内容还有一部分需要进行介绍。


个人微信
目前已经实现了很多有趣的功能，运行稳定，比如：发各种消息，
接收各种消息，群管，下载文件，加好友，检测僵尸粉，朋友圈等等功能，
可提供接口，方便各种语言二次开发，欢迎技术交流，Q：2645542961
，请勿用于商业用途。
![image](https://user-images.githubusercontent.com/73727649/194449382-36c71ecc-e88d-45e7-a37d-9db1f6c459cb.png)


企业微信：
目前已经实现了大部分功能，运行稳定，比如：发各种消息，
接收各种消息，外部群内部群管理，下载文件，加好友等等功能，
可提供接口，方便各种语言二次开发，欢迎技术交流。

# 函数调用混淆

Antivirus可以通过分析静态文件的PE结构获取导入表，根据导入表中引入的函数对比恶意软件调用函数库来进行初步木马 判断。

使用GetModuleHandle和GetProcAddress直接调用目标函数来隐藏导入表，对抗AV的静态分析

这样使用GetModuleHandle和GetProcAddress，会导致这两个敏感函数出现再导入表中，可以自己实现这两个功能来隐藏导入表。

具体实现在UserDefineApi.h



对于shellcode的加密使用了xor+rc4，先对生成的shellcode使用xor.py进行异或加密， 再使用rc4.cpp进行对称加密，就可以放入main.cpp进行使用了。
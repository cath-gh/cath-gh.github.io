---
title: 在vscode中使用pipenv环境运行jupyter
date: 2020-02-04 10:30:53
cover: https://s2.loli.net/2022/03/27/OF6YQM9Z3lWpGPC.png
thumbnail: https://s2.loli.net/2022/03/27/OF6YQM9Z3lWpGPC.png
categories:
- [旧文]
- [记录]
tags:
- 豆瓣日记
- vscode
- jupyter
---
每次配置都要重新搜索一遍，这回记录一下配置过程。

### 0. 准备
+ python、pipenv、vscode均安装完成，pipenv的环境变量已配置好，可以直接呼出。
+ 在公共环境下安装jupyter，确保可以正常运行

<!--more-->

### 1.  查看Pipenv的位置
__先激活Pipenv环境__ 

`pipenv shell`

![pipenv_jupyter_1.png](https://s2.loli.net/2022/03/27/KJ3vWA6Ca7VEolm.png)

__获取当前虚拟环境的位置__ 

`pipenv --venv` 

![pipenv_jupyter_2.png](https://s2.loli.net/2022/03/27/Qx6d82pSq9XZefT.png)

### 2. 打开setting.json配置文件
+ `Ctrl+Shift+P`，输入`settings`，选择`Open Settings(JSON)`
+ 将之前得到的Pipenv环境路径添加进去
`"python.venvPath": "C:\\Users\\Administrator\\.virtualenvs\\test_pipenv_jupyter-yZGS62vC"`
+ 如果存在多个虚拟环境，用逗号分隔

![pipenv_jupyter_3.png](https://s2.loli.net/2022/03/27/XtqK85pEHel9cFr.png)

### 3. 重启vscode
__选择对应环境__

![pipenv_jupyter_4.png](https://s2.loli.net/2022/03/27/5OAEJG8RUu7tfIB.png)

### 4. 安装ipykernel
__替换pipenv源为清华源，编辑pipfile文件的url字段__

![pipenv_jupyter_5.png](https://s2.loli.net/2022/03/27/WJwevPm4MXp3bn1.png)

国内其他源地址

+ 阿里云：http://mirrors.aliyun.com/pypi/simple/

+ 豆瓣：http://pypi.douban.com/simple/

+ 清华大学：https://pypi.tuna.tsinghua.edu.cn/simple/

+ 中国科学技术大学：https://pypi.mirrors.ustc.edu.cn/simple/

__启动pipenv环境，安装ipykernel__

`pipenv install ipykernel`

![pipenv_jupyter_6.png](https://s2.loli.net/2022/03/27/nl6AB3zw5omHWPL.png)

### 5. 测试jupyter文件
打开一个新建的.ipynb文件会自动切换成下图显示效果，右上角提示环境尚未启动。

![pipenv_jupyter_7.png](https://s2.loli.net/2022/03/27/NUPQnpXcj5mqkw3.png)

查看一下sys.path，可以发现引用环境已经挂载到了虚拟环境，右上角也提示了之前选择的环境名称。

![pipenv_jupyter_8.png](https://s2.loli.net/2022/03/27/MfzSd8pUTHnFXgy.png)

### 6. 最后
截止到当前版本，pywin32(v225 ~ v227)的坑已经被填平了，直接按照上述步骤配置即可正常使用。

其实也可以直接在pipenv环境下直接安装jupyter，只不过考虑安装包大小和安装时间，以及在非虚拟环境下也会用到jupyter进行工作，最后选择了这种折中的方式。在满足步骤0中的准备条件下，可以通过pipenv的配置文件实现快速重建环境。

### 7. 参考引用
 1. https://www.cnblogs.com/sikongji-yeshan/p/10492021.html 
 2. https://blog.csdn.net/jpch89/article/details/81952416 
 3. https://jakevdp.github.io/blog/2017/12/05/installing-python-packages-from-jupyter/ 
 4. https://stackoverflow.com/questions/47295871/is-there-a-way-to-use-pipenv-with-jupyter-notebook 
 5. https://github.com/jupyter/notebook/issues/4909 

> 版权归作者所有，任何形式转载请联系作者。  
> 作者：Cath（来自豆瓣）  
> 来源：[https://www.douban.com/note/750959014/](https://www.douban.com/note/750959014/)
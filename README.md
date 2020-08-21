# DolphinDB Jupyter Notebook 扩展插件

Jupyter Notebook是基于网页的用于交互计算的应用程序。用户可以直接通过浏览器编辑和交互式运行代码。DolphinDB database 提供了Jupyter Notebook的插件。

DolphinDB Jupyter Notebook 扩展插件提供以下功能：
- 为用户提供Jupyter Notebook连接DolphinDB Server的配置界面。
- 使Jupyter Notebook支持DolphinDB脚本语言的执行。

**1. 下载插件并安装**

- 使用pip安装

    `pip install dolphindb_notebook`

- 启用插件
    
   `jupyter nbextension enable dolphindb/main`

**2. 配置Jupyter Notebook工作路径**

Jupyter Notebook内核（kernels）是编程语言特定的进程，它们独立运行并与Jupyter应用程序及其用户界面进行交互。DolphinDB Jupyter Notebook 扩展插件提供了运行DolphinDB脚本的内核。用户需要通过以下步骤配置Jupyter Notebook的工作路径，以便在程序运行时DolphinDB内核的顺利导入。

- 通过命令行`jupyter kernelspec list`查看Jupyter Notebook内核的工作路径。
    - Linux系统
    ```Shell
    >jupyter kernelspec list
    Available kernels:
        dolphindb   /home/admin/.local/share/jupyter/kernels/dolphindb
        python3       /home/admin/.local/share/jupyter/kernels/python3
    ```
    将/home/admin/.local/share/jupyter/kernels复制下来，方便下一步配置时粘贴。
    - Windows系统
    ```Shell
    >jupyter kernelspec list
    Available kernels:
        dolphindb   C:\Users\admin\appdata\local\programs\python3\python37\share\jupyter\kernels\dolphindb
        python3       C:\Users\admin\appdata\local\programs\python3\python37\share\jupyter\kernels\python3
    ```    
    将 C:\Users\admin\appdata\local\programs\python3\python37\share\jupyter\kernels复制下来，方便下一步配置时粘贴。
    
- 通过命令行`jupyter notebook --generate-config`生成一个配置文件jupyter_notebook_config.py，打开这个配置文件，找到c.NotebookApp.notebook_dir选项，设为上一步复制下来的工作路径，并去掉注释#。
    注意：Windows系统需要将路径中的一个反斜杠\都替换成两个反斜杠\\\\，其中一个是转义字符。

**3. 连接DolphinDB Server**

- 在命令行输入`jupyter notebook`，启动Jupyter Notebook。
- 在Jupyter Notebook的页面右侧点击新建，选择DolphinDB，新建一个DolphinDB notebook。
- 点击notebook工具栏的Connect to DolphinDB Server按钮。选择相应的server，然后点击右下角Connect按钮，即与DolphinDB server建立连接（如果不需要该server，可以点击Delete按钮删除）。
- 也可以通过New按钮，输入新的server信息，然后点击Save & Connect按钮即与DolphinDB server建立连接，并保存该信息以便下次使用。

**4. 编辑和运行DolphinDB脚本**

连接DolphinDB Server后，在代码块区域编写DolphinDB脚本，点击运行即可运行相应代码块。

**5. 展示代码块运行结果**

每次运行DolphinDB脚本后，运行结果都会在相应的代码块下方展示。对于DolphinDB的绘图功能，以PNG展示结果。

**注意：**

- 对于一些数据量较大的结果，可能会出现IOPub数据率超出限制的问题，可以启用 Jupyter Notebook配置文件中的 c.NotebookApp.iopub_data_rate_limit 这一项，按需调高数值。
- 对于超出60行的表格，只显示前五行与后五行。






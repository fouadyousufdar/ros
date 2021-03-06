# 安装阿里云CLI {#task_2261616 .task}

资源编排服务（ROS）支持您通过阿里云CLI对资源栈进行创建、删除、更新、查看等操作。本文为您介绍如何安装阿里云CLI。

您可以通过下载安装包或者直接编译源码的方式来安装阿里云CLI。下面为您介绍下载安装包的方式，如需通过直接编码的方式安装阿里云CLI，请参见[../../SP\_525/DNICMS19101929/ZH-CN\_TP\_475354\_V1.dita\#task\_592879](../../SP_525/DNICMS19101929/ZH-CN_TP_475354_V1.dita#task_592879)。

阿里云CLI的使用场景包括：

-   无法使用阿里云控制台的场景。
-   API级别的开发和调试场景，例如查看资源栈、删除资源栈、查看资源类型等。

## 在Windows平台安装阿里云CLI {#section_1e0_1xo_hr8 .section}

1.  登录[官网](https://aliyuncli.alicdn.com/aliyun-cli-windows-3.0.16-amd64.zip)或者[GitHub](https://github.com/aliyun/aliyun-cli/releases)的下载页面，下载名为aliyun-cli-windows-3.0.16-amd64.zip的Windows终端安装包。
2.  解压aliyun-cli-windows-3.0.16-amd64.zip文件，获取名为aliyun.exe的可执行文件。
3.  将aliyun.exe文件所在目录的路径添加到Path环境变量中。 

    1.  在环境变量窗口中，选择用户变量下的**Path**变量，单击**编辑**。
    2.  在编辑环境变量窗口中，单击**新建**。
    3.  在编辑环境变量窗口中，输入aliyun.exe文件所在目录的路径。
    4.  在编辑环境变量窗口中，单击**确定**。
    5.  在环境变量窗口中，单击**确定**。
    6.  在终端执行以下命令，查看环境变量是否配置成功： 
        -   CMD终端：[试用](https://api.aliyun.com/new#/tutorial?id=121510) 

            ``` {#codeblock_g0d_58s_blu .language-cmd}
            set path
            ```

        -   PowerShell终端：[试用](https://api.aliyun.com/new#/tutorial?id=121510) 

            ``` {#codeblock_hvq_hfv_kdw .language-powershell}
            env:path
            ```

    7.  在终端执行以下命令，验证阿里云CLI是否安装成功。[试用](https://api.aliyun.com/new#/tutorial?id=121510) 

        ``` {#codeblock_ef0_2ft_0wd .language-powershell}
        aliyun version
        ```

    如果系统显示类似如下的阿里云CLI当前版本号，则表示安装成功。

    ``` {#codeblock_vg8_5yz_5j4 .language-powershell}
    3.0.16
    ```


## 在Linux平台安装阿里云CLI {#section_g7y_8o1_erm .section}

1.  登录[官网](https://aliyuncli.alicdn.com/aliyun-cli-windows-3.0.16-amd64.zip)或者[GitHub](https://github.com/aliyun/aliyun-cli/releases)的下载页面，下载名为aliyun-cli-linux-3.0.16-amd64.tgz的Linux终端安装包。
2.  执行以下命令，解压aliyun-cli-linux-3.0.16-amd64.tgz文件，获取名为aliyun.exe的可执行文件。 

    ``` {#codeblock_qbk_etj_g85 .language-bash}
    cd $HOME/aliyun
    tar xzvf aliyun-cli-linux-3.0.16-amd64.tgz
    ```

    **说明：** 此处假设您已经下载到了$HOME/aliyun目录中，并解压到此目录下。

3.  执行以下命令，将aliyun程序移至/usr/local/bin目录中。 [试用](https://api.aliyun.com/new#/tutorial?id=121541) 

    ``` {#codeblock_pr5_uu9_059 .language-bash}
    sudo cp aliyun /usr/local/bin
    ```

    **说明：** 如果您是root用户，请移除sudo命令。


## 在MacOS平台安装阿里云CLI {#section_1a2_vxx_gzq .section}

1.  登录[官网](https://aliyuncli.alicdn.com/aliyun-cli-windows-3.0.16-amd64.zip)或者[GitHub](https://github.com/aliyun/aliyun-cli/releases)的下载页面，下载名为aliyun-cli-macosx-3.0.16-amd64.tgz的MacOS终端安装包。
2.  执行以下命令，解压aliyun-cli-macosx-3.0.16-amd64.tgz文件，获取名为aliyun.exe的可执行文件。 

    ``` {#codeblock_4x2_7sb_xkl .language-bash}
    cd $HOME/aliyun
    tar xzvf aliyun-cli-macosx-3.0.16-amd64.tgz
    ```

    **说明：** 此处假设您已经下载到了$HOME/aliyun目录中，并解压到此目录下。

3.  执行以下命令，将aliyun程序移至/usr/local/bin目录中。[试用](https://api.aliyun.com/new#/tutorial?id=121544) 

    ``` {#codeblock_sne_8xl_kgt .language-bash}
    sudo cp aliyun /usr/local/bin
    ```

    **说明：** 如果您是root用户，请移除sudo命令。



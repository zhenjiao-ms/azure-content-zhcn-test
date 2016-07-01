<properties
	pageTitle="在 Azure 门户中创建运行 Linux 的 Azure 虚拟机"
	description="在 Azure 门户中使用 Azure 资源组创建运行 Linux 的 Azure 虚拟机 (VM)。"
	services="virtual-machines"
	documentationCenter=""
	authors="squillace"
	manager="timlt"
	editor="tysonn"
	tags="azure-resource-management"/>

<tags ms.service="virtual-machines"
	ms.date="10/21/2015"
	wacn.date="02/17/2015"/>

# 使用 Azure 门户创建运行 Linux 的虚拟机

创建运行 Linux 的 Azure 虚拟机 (VM) 是一项很简单的操作。本教程演示如何使用 Azure 门户快速创建一个虚拟机，并使用SSH公钥文件来保护到 VM 的 **SSH** 连接。你也可以[将自己的映像作为模板](/documentation/articles/virtual-machines-linux-create-upload-vhd)来创建 Linux VM。

> [AZURE.NOTE]本教程创建的 Azure 虚拟机将由 Azure 资源组 API 管理，有关详细信息，请参阅 [Azure 资源组概述](/documentation/articles/resource-group-overview)。关于SSH公钥的用法请参阅[如何在 Azure 上通过 Linux 使用 SSH](/documentation/articles/virtual-machines-linux-use-ssh-key)。

[AZURE.INCLUDE [free-trial-note](../includes/free-trial-note.md)]

## 选择映像

1. 登录[Azure 管理门户](https://manage.windowsazure.cn)。

2. 在窗口底部的命令栏上，单击“新建”。

3. 在“计算”下，单击“虚拟机”，然后单击“从库中”，在随后出现的映像列表中选择“Ubuntu Server 14.04 LTS”。

	![选择 VM 映像](./media/virtual-machines-linux-tutorial-portal-rm/chooseubuntuvm.png)

## 创建虚拟机

选择映像后，可以对大多数配置使用 Azure 的默认设置并快速创建 VM。

1. 在虚拟机配置的“基本信息”中，输入虚拟机的“名称”，上传公钥文件并采用 [pem](/documentation/articles/virtual-machines-linux-use-ssh-key)封装的格式）。

	![](./media/virtual-machines-linux-tutorial-portal-rm/step-1-thebasics.png)

	> [AZURE.NOTE]如果不想使用公钥和私钥交换来保护 **ssh** 会话的安全，你还可以在此处选择用户名/密码身份验证并输入该信息。

2. 单击“大小”并选择适合你需要的 VM 大小。每种大小都指定了计算核心的数量、内存以及其他功能，比如对高级存储的支持，这将对价格产生影响。根据所选的映像，Azure 将自动推荐特定的大小。完成后，单击 ![选择按钮](./media/virtual-machines-linux-tutorial-portal-rm/selectbutton-size.png)。

	>[AZURE.NOTE]某些地区的 DS 系列虚拟机提供高级存储。高级存储是数据密集型工作负荷（如数据库）的最佳存储选项。

3. 单击下一步按钮以查看新 VM 的存储和网络设置。对于第一个 VM，一般可以接受默认设置。

	![](./media/virtual-machines-linux-tutorial-portal-rm/step-3-settings.png)

4. 当 Azure 创建 VM 时，你可以在窗口底部“状态栏”中查看进度。当 Azure 创建 VM 后，你将在已创建的虚拟机列表中看到它。

## 使用 **ssh** 连接到你的 Azure Linux VM

现在可以使用 **ssh** 以标准方式连接到 Ubuntu VM。你可以通过单击“虚拟机”，然后选择你创建的 VM,找到并复制下图所示的“公共 IP 地址”的值。

![成功创建的摘要](./media/virtual-machines-linux-tutorial-portal-rm/successresultwithip.png)

现在一切准备就绪，你可以使用 **ssh** 连接到你的 Azure VM 了。

	ssh ops@42.159.233.50 -p 22
	The authenticity of host '42.159.233.50 (42.159.233.50)' can't be established.
	ECDSA key fingerprint is bc:ee:50:2b:ca:67:b0:1a:24:2f:8a:cb:42:00:42:55.
	Are you sure you want to continue connecting (yes/no)? yes
	Warning: Permanently added '23.96.106.1' (ECDSA) to the list of known hosts.
	Welcome to Ubuntu 14.04.2 LTS (GNU/Linux 3.16.0-43-generic x86_64)

	 * Documentation:  https://help.ubuntu.com/

	  System information as of Mon Jul 13 21:36:28 UTC 2015

	  System load: 0.31              Memory usage: 5%   Processes:       208
	  Usage of /:  42.1% of 1.94GB   Swap usage:   0%   Users logged in: 0

	  Graph this data and manage this system at:
	    https://landscape.canonical.com/

	  Get cloud support with Ubuntu Advantage Cloud Guest:
	    http://www.ubuntu.com/business/services/cloud

	0 packages can be updated.
	0 updates are security updates.

	The programs included with the Ubuntu system are free software;
	the exact distribution terms for each program are described in the
	individual files in /usr/share/doc/*/copyright.

	Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
	applicable law.

	ops@ubuntuvm:~$


## 后续步骤

若要了解有关 Azure 上的 Linux 的详细信息，请参阅：

- [Azure 上的 Linux 和开源计算](/documentation/articles/virtual-machines-linux-opensource)

- [使用适用于 Linux 的 Azure CustomScript 扩展部署 LAMP 应用程序](/documentation/articles/virtual-machines-linux-script-lamp)

- [Azure 上用于 Linux 的 Docker 虚拟机扩展](/documentation/articles/virtual-machines-docker-vm-extension)

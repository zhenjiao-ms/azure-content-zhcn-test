<properties
	pageTitle="使用 TSQL 创建 SQL 数据仓库 | Azure"
	description="了解如何使用 TSQL 创建 Azure SQL 数据仓库"
	services="sql-data-warehouse"
	documentationCenter="NA"
	authors="lodipalm"
	manager="barbkess"
	editor=""
	tags="azure-sql-data-warehouse"/>

<tags
   ms.service="sql-data-warehouse"
   ms.date="10/21/2015"
   wacn.date="01/20/2016"/>

# 使用 Transact-SQL (TSQL) 创建 SQL 数据仓库数据库

> [AZURE.SELECTOR]
- [TSQL](/documentation/articles/sql-data-warehouse-get-started-create-database-tsql)
- [PowerShell](/documentation/articles/sql-data-warehouse-get-started-provision-powershell)

本文说明如何使用 Transact-SQL (TSQL) 创建 SQL 数据仓库数据库。

## 开始之前

若要完成本文中的步骤，你需要以下各项：

- Azure 订阅。如果你需要 Azure 订阅，只需单击本页顶部的“试用”，然后再回来完成本文的相关操作即可。
- Visual Studio。如需 Visual Studio 的免费副本，请参阅 [Visual Studio 下载](https://www.visualstudio.com/downloads/download-visual-studio-vs)页。
- 一个 V12 逻辑服务器。你将需要使用 V12 SQL 服务器来创建 SQL 数据仓库。

## 使用 Visual Studio 创建数据库

本文未介绍如何使用 Visual Studio 正确完成设置和连接。有关此操作的完整说明，请参阅[连接和查询][]文档。若要开始，请在 Visual Studio 中打开 SQL Server 对象资源管理器，并连接到要用于创建 SQL 数据仓库数据库的服务器。完成此操作后，你可以针对 Master 数据库运行以下命令来创建 SQL 数据仓库：

        CREATE DATABASE <Name> (EDITION='datawarehouse', SERVICE_OBJECTIVE = '<Compute Size - DW####>', MAXSIZE= <Storage Size - #### GB>);

## 使用 sqlcmd 创建数据库

还可以通过打开命令行并运行以下命令来创建 SQL 数据仓库：
```
 sqlcmd -S <Server Name>.database.chinacloudapi.cn -I -U <User> -P <Password> -Q "CREATE DATABASE <Name> (EDITION='datawarehouse', SERVICE_OBJECTIVE = '<Compute Size - DW####>', MAXSIZE= <Storage Size - #### GB>)"
```
运行上述 TSQL 语句时，请记下 MAXSIZE 和 SERVICE\_OBJECTIVE 参数，这些参数指定了初始存储大小，以及分配给数据仓库实例的计算资源。MAXSIZE 接受以下大小，我们建议选择较大的大小，以便为将来的增长留出空间：250 GB、500 GB、750 GB、1024 GB、5120 GB、10240 GB、20480 GB、30720 GB、40960 GB、51200 GB。

SERVICE\_OBJECTIVE 指示启动实例时使用的 DWU 数目，接受以下值：DW100、DW200、DW300、DW400、DW500、DW600、DW1000、DW1200、DW1500、DW2000。有关这些参数的计费影响信息，请参阅我们的[定价页][]。

## 后续步骤
完成预配 SQL 数据仓库之后，你可以[加载示例数据][]或了解如何[开发][]、[加载][]，或[迁移][]数据。

[Azure 经典门户教程]: /documentation/articles/sql-data-warehouse-get-started-provision
[连接和查询]: /documentation/articles/sql-data-warehouse-get-started-connect
[迁移]: /documentation/articles/sql-data-warehouse-overview-migrate
[开发]: /documentation/articles/sql-data-warehouse-overview-develop
[加载]: /documentation/articles/sql-data-warehouse-overview-load
[加载示例数据]: /documentation/articles/sql-data-warehouse-get-started-manually-load-samples
[定价页]: /home/features/sql-data-warehouse/#price

<!---HONumber=Mooncake_1207_2015-->

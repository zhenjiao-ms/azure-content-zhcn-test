<properties
   pageTitle="SQL 数据仓库预览版的预期功能 | Windows Azure"
   description="SQL 数据仓库公共预览版功能摘要，以及正式版的目标。"
   services="sql-data-warehouse"
   documentationCenter="NA"
   authors="lvargas"
   manager="tonypet"
   editor=""/>

<tags
   ms.service="sql-data-warehouse"
   ms.date="09/22/2015"
   wacn.date="01/20/2016"/>

# SQL 数据仓库预览版的预期功能

本文介绍 SQL 数据仓库预览版的功能，以及正式版 (GA) 的服务目标。在增强公共预览版功能的过程中，我们将不断更新本文中的信息。

我们的 SQL 数据仓库目标：

- 可预测的性能以及 PB 量级数据的线性缩放性。
- 所有数据仓库操作的高度可靠性，有服务级别协议 (SLA) 提供保障。

在 SQL 数据仓库正式版 (GA) 推出之前，我们将持续努力，争取实现这些目标。

## 可预测且可缩放的性能

Azure SQL 数据仓库引入了数据仓库单位 (DWU) 作为度量数据仓库可用计算资源（CPU、内存、存储 I/O）的方法。增加 DWU 数目可增加资源。当 DWU 数目增加时，SQL 数据仓库操作（例如数据加载或查询）可跨越更多分布式资源并行运行。这可减少延迟并改善性能。

任一数据仓库都有 2 个基本性能指标：

- 加载速率。每秒可载入数据仓库的记录数量。我们会专门度量可通过 PolyBase 从 Azure Blob 存储导入包含群集列存储索引的表中的记录数量。 
- 扫描速率。每秒可从数据仓库依序检索的记录数量。我们会专门度量查询从包含群集列存储索引中返回的记录数量。


我们正在度量一些重要的性能增强功能，不久就能分享预期的速率。在预览期，我们将持续增强服务质量（例如提高压缩和缓存）以提高这些速率，并确保能够以可预测的方式调整这些速率。


## SLA 保障的高度可靠性

### 数据保护 

SQL 数据仓库使用异地冗余 Blob，将所有数据存储在 Azure 存储空间中。将在本地 Azure 区域维护数据的三个同步副本，确保在发生局部故障（例如存储驱动器故障）时能够保证提供透明的数据保护。此外，还会在远程 Azure 区域维护三个异步副本，以确保在发生区域性故障时能够保证提供数据保护（灾难恢复）。将局部和远程区域配对可以保持可接受的同步延迟（例如在中国东部和北部）。


### 备份

Azure SQL 数据仓库使用 Azure 存储空间快照，每隔 8 小时备份所有数据至少一次。这些快照将保留 7 天。这样，在生成最新快照前的 7 天内，至少有 21 个时间点可用于还原数据。可以使用 PowerShell 或 REST API 从快照还原数据。

快照以异步复制到远程 Azure 区域，以便在发生区域性故障时提高恢复能力（灾难恢复）。


### 完成查询 

SQL 数据仓库将数据存储在一个或多个计算节点上，每个节点可存储某些用户数据以及控制该数据的查询执行。在大规模并行处理 (MPP) 体系结构中，查询以并行方式跨计算节点运行。SQL 数据仓库可自动检测并缓解计算节点故障。但是，在预览期，操作（例如数据加载或查询）可能由于单个节点故障而失败。在预览期，我们将持续增强，使节点故障不会影响到操作的成功完成。

根据遥测数据，我们评估当前的 Azure SQL 数据仓库可靠性为 98%。这意味着，在 100 次查询中，平均有 2 次查询可能因系统错误而失败。实际的 SLA 并不是这样。查询失败的几率随着执行时间的延长而增大。例如，运行时间大于 2 小时的查询，其失败几率高于运行时间小于 10 分钟的查询。在预览期，我们将持续改善可靠性，确保操作无论执行时间长短都能提供相同级别的可靠性。我们将通过发布这些增强功能更新预期的可靠性。正式版推出后，可靠性将有 SLA 提供保障。

### 服务正常运行时间

Azure SQL 数据仓库每个月都可能有高达 4 个维护事件，以便安装关键的修复程序。每个事件可能导致长达 2 小时的查询失败。该时间取决于分配给服务的 DWU 数量。


## 后续步骤

公共预览版[入门][]。

<!--Image references-->

<!--Article references-->
[入门]: /documentation/articles/sql-data-warehouse-get-started-provision

<!--MSDN references-->

<!--Other Web references-->

<!---HONumber=Mooncake_1207_2015-->
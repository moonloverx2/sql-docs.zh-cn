---
title: R 和 Python 机器学习 SQL Server 中的服务 |Microsoft Docs
description: 在 SQL Server 和 Python 在 SQL Server 中，与用于数据科学和统计建模、 机器学习模型，预测分析、 数据可视化效果和的详细信息的关系数据集成的 R。
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/06/2018
ms.topic: overview
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0768ae40b110bbb2b85890f0a8b4eff0339cedde
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269700"
---
# <a name="machine-learning-services-r-python-in-sql-server-2017"></a>SQL Server 2017 中机器学习服务 （R、 Python）
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server 2017 机器学习服务是用于 SQL 服务器上执行的 R 和 Python 代码的数据库引擎实例的附加内容。 独立于核心引擎进程，但完全可用于关系数据作为存储过程、 包含 R 或 Python 语句的 T-SQL 脚本或包含的 T-SQL 的 R 或 Python 代码，代码中的可扩展性框架，运行。 

如果以前使用过[SQL Server 2016 R Services](r/sql-server-r-services.md)、 SQL Server 2017 中的机器学习服务是与更新版本的基本 R，RevoScaleR，MicrosoftML，R 支持，下一代和 2016 版本中引入的其他库。 

如果您以前使用过SQL Server 2016 R服务(r/sql-server-r-services.md)，那么SQL Server 2017中的机器学习服务就是下一代R支持，在2016年引入了base R、RevoScaleR、MicrosoftML等库的更新版本。

Azure SQL 数据库中[机器学习服务 （使用 R)]((https://docs.microsoft.com/azure/sql-database/sql-database-connect-query-r))目前处于公共预览状态。

机器学习服务的关键价值主张是其企业 R 和 Python 包的强大功能提供高级的分析大规模和能够将计算和处理到数据所在的位置，从而无需在提取数据在网络中。

## <a name="components"></a>组件

SQL Server 2017 支持 R 和 Python。 下表介绍的组件。

| 组件 | Description |
|-----------|-------------|
| SQL Server 快速启动板服务 | 用于管理外部的 R 和 Python 运行时和数据库引擎实例之间的通信的服务。 |
| R 包 | [**RevoScaleR** ](r/revoscaler-overview.md)是主库的此库中的可缩放。 函数是最广泛使用。 这些库中找到数据转换和操作、 统计汇总、 可视化和建模和分析多种形式。 此外，这些库中的函数会自动将工作负荷分散到以便并行处理，能够工作的协调和管理计算引擎的数据块上的可用内核。  <br/>[**MicrosoftML (R)** ](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)添加机器学习算法来创建自定义文本分析、 图像分析和情绪分析模型。 <br/>[**sqlRUtils** ](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)用于 R 脚本置于 T-SQL 存储过程、 向数据库注册存储的过程和从 R 开发环境运行存储的过程提供帮助器函数。<br/>[**olapR** ](r/how-to-create-mdx-queries-using-olapr.md)是用于构建还是在 R 脚本中执行 MDX 查询。|
| Microsoft R Open (MRO) | [**MRO** ](https://mran.microsoft.com/open)是 Microsoft 的开放源代码分发的。包含包和解释器。 始终使用 MRO 由安装程序安装的版本。 |
| R 工具 | R 控制台窗口和命令提示中的 R 分发版的标准工具。  |
| R 示例和脚本 |  开放源代码 R 和 RevoScaleR 包包括内置的数据集，以便您可以创建和运行脚本使用预安装的数据。 |
| Python 包 | [**revoscalepy** ](python/what-is-revoscalepy.md)用于具有可实现数据操作、 转换、 可视化和分析功能的可缩放 Python 是主库。 <br/>[**microsoftml (Python)** ](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package)添加机器学习算法来创建自定义文本分析、 图像分析和情绪分析模型。  |
| Python 工具 | 内置的 Python 命令行工具可用于临时测试和任务。  |
| Anaconda | Anaconda 是开放源代码的 Python 和基本包的发行版本。 |
| Python 示例和脚本 | 如使用 R、 Python 包含内置的数据集和脚本。  |
| R 和 Python 中预先训练的模型 | 预先训练的模型创建的特定用例和在 Microsoft 数据科学工程团队维护的。 可以使用预先训练的模型作为-是正负情绪评分中的文本，或在映像中，使用你提供的新数据输入检测功能。 模型在机器学习服务中运行，但不能通过 SQL Server 安装程序安装。 有关详细信息，请参阅[安装预先定型的机器学习模型的 SQL Server](install/sql-pretrained-models-install.md)。 |

## <a name="using-sql-mls"></a>使用 SQL MLS

开发人员和分析师通常具有在本地 SQL Server 实例上运行的代码。 通过添加机器学习服务并启用外部脚本执行，便能够在 SQL 服务器模式中运行 R 和 Python 代码： 包装存储过程中的脚本、 存储模型中的 SQL Server 表，或结合使用 T-SQL 和 R 或 Python 函数在查询中。

脚本执行的数据安全模型的范围内仍： 关系数据库的权限是在脚本中的数据访问的基础。 运行 R 或 Python 脚本的用户应不能使用 SQL 查询中的该用户无法访问任何数据。 需要标准数据库读取和写入权限，以及要运行外部脚本的其他权限。 模型和关系数据的编写的代码是包装在存储过程，或为二进制格式序列化和存储在表中，或如果序列化到文件的原始字节流从磁盘加载。

数据库内分析的最常见方法是使用[sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)，传递 R 或 Python 脚本作为输入参数。

经典的客户端-服务器交互是另一种方法。 从任何客户端工作站上具有一个 IDE，可以安装[Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)或[Python 库](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)，然后编写将推送执行的代码 (称为*远程计算上下文*) 对数据和到远程 SQL Server 的操作。 

最后，如果使用的[独立服务器](r/r-server-standalone.md)和 Developer edition 中，你可以构建解决方案，客户端工作站上使用相同的库和解释器，并随后部署生产代码中的对 SQL Server 机器学习服务 （数据库内）。 

## <a name="how-to-get-started"></a>如何开始

### <a name="step-1-install-the-software"></a>步骤 1： 安装软件

+ [SQL Server 机器学习服务 （数据库内）](install/sql-machine-learning-services-windows-install.md)
 
### <a name="step-2-configure-a-development-tool"></a>步骤 2： 配置开发工具

数据科研人员通常在自己的笔记本电脑或开发工作站上使用 R 或 Python 来研究数据并生成和调整预测模型，直到生成效果良好的预测模型。 使用 SQL Server 中的数据库内分析，没有必要更改此过程。 安装完成后，您可以在 SQL Server 上运行 R 或 Python 代码，本地和远程。

![rsql_keyscenario2](r/media/rsql-keyscenario2.png) 

+ **使用喜欢的 IDE**。 你可以链接到所选的开发工具的 R 和 Python 库。 有关详细信息，请参阅[设置的 R 工具](r/set-up-a-data-science-client.md)并[设置 Python 工具](python/setup-python-client-tools-sql.md)。  

+ **处理远程或本地**。 数据科研人员可以像平时一样连接到 SQL Server，然后将数据取回到客户端进行本地分析。 但是，更好的解决方案是使用**RevoScaleR**或**revoscalepy** Api 将计算推送到 SQL Server 计算机，避免成本高昂且不安全的数据移动。

+ **在 SQL Server 存储过程中嵌入 R 或 Python 脚本**。 代码充分优化后，将其封装在一个存储过程中，以避免不必要的数据移动和优化数据处理任务。

### <a name="step-3-write-your-first-script"></a>第 3 步： 编写第一个脚本

调用 R 或 Python 中的函数从 T-SQL 脚本：

+ [： 了解使用 R 的数据库内分析](tutorials/sqldev-in-database-r-for-sql-developers.md)
+ [： 使用 R 的端到端演练](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
+ [Python：使用 T-SQL 运行 Python](tutorials/run-python-using-t-sql.md)
+ [Python： 了解数据库内分析使用 Python](tutorials/sqldev-in-database-python-for-sql-developers.md)

选择该任务的最佳语言。 使用 SQL 难以实现统计计算，但适合使用 R 来实现。 对于基于集的操作数据，利用 SQL Server 的强大功能实现最佳性能。 对列进行快速计算时，可使用内存数据库引擎。

### <a name="step-4-optimize-your-solution"></a>步骤 4： 优化你的解决方案

准备好根据企业数据缩放模型时，数据科研人员通常会与 DBA 或 SQL 开发人员一起优化以下流程非常有效：

+ 特征工程
+ 数据引入和数据转换
+ 计分

传统上，数据科学家使用 R 已与性能和规模，问题，尤其是在使用大型数据集。 因为通用运行时实现是单线程的，只能适应可装入本地计算机上可用内存的数据集。 与 SQL Server 机器学习服务集成提供多种功能，更好的性能，更多的数据：

+ **RevoScaleR**： 此 R 包包含部分最常用 R 函数，可提供并行度与伸缩性重新设计的实现实现。 包还包括函数来进一步提升性能和规模，通过将计算推送到通常具有大得多的内存和计算能力的 SQL Server 计算机。

+ **revoscalepy**。 例如远程计算上下文中 RevoScaleR，此 Python 库实现最常用的函数和许多算法支持的分布式处理。

有关性能的详细信息，请参阅此[性能案例研究](r/performance-case-study-r-services.md)并[R 和数据优化](r/r-and-data-optimization-r-services.md)。

### <a name="step-5-deploy-and-consume"></a>步骤 5： 部署和使用

准备好进行生产环境中使用的脚本或模型后，数据库开发人员可能会嵌入代码或模型中的存储过程，以便可以从应用程序调用的已保存的 R 或 Python 代码。 存储和从 SQL Server 中运行 R 代码可带来诸多好处： 可以使用方便的 SQL Server 界面中，且所有计算都发生在数据库中，从而避免不必要的数据移动。

![rsql_keyscenario1](r/media/rsql-keyscenario1.png)

+ **安全且可扩展**。 SQL Server 使用新的可扩展性体系结构，可在数据库引擎的安全并隔离 R 和 Python 的会话。 你还可以控制用户可以执行脚本，并可以指定的代码可以访问哪些数据库。 您可以控制分配给运行时，以防止海量计算降低服务器的整体性能的资源量。

+ **计划和审核**。 在 SQL Server 中运行外部脚本作业时，可以控制和审核数据研究人员使用的数据。 与计划其他任何 T-SQL 作业和存储过程一样，用户还可以计划作业和创作包含外部 R 或 Python 脚本的工作流。

若要充分利用资源管理和安全功能的 SQL Server 中，部署过程可能会包括这些任务：

+ 将你的代码转换为可以在存储过程中以最佳方式运行的函数
+ 设置安全性并锁定使用某个特定任务的包
+ （需要企业版） 启用资源调控

有关详细信息，请参阅[R 的资源调控](r/resource-governance-for-r-services.md)并[SQL Server 的 R 包管理](r/install-additional-r-packages-on-sql-server.md)。

## <a name="version-history"></a>版本历史记录

SQL Server 2017 机器学习服务是新一代的 SQL Server 2016 R Services，增强，其中包括 Python。 下表是所有产品版本中，从开始到当前版本的完整列表。 

| 产品名称 | 引擎版本 | 发布日期 |
|--------------|---------|--------------|
| SQL Server 2017 机器学习服务 （数据库内） | R Server 9.2.1 <br/> Python 服务器 9.2 | 2017 年 10 月 |
| SQL Server 2017 机器学习服务器 （独立版） | R Server 9.2.1 <br/> Python 服务器 9.2 | 2017 年 10 月 |
| SQL Server 2016 R Services （数据库内） | R Server 9.1  | 2017 年 7 月  |
| SQL Server 2016 R Server （独立版）  |  R Server 9.1 | 2017 年 7 月 |

有关版本的包版本，请参阅中的映射的版本[升级 R 和 Python 组件](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md#version-map)。

## <a name="portability-and-related-products"></a>可移植性及相关的产品

通过包分发和解释器内置于多个产品，自定义 R 和 Python 代码的可移植性将得到解决。 在 SQL Server 中提供的相同包也会出现在多个其他 Microsoft 产品和服务，包括一个名为非 SQL 版本[Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/)。 

免费包含我们 R 和 Python 解释器的客户端[Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)并[Python 库](https://docs.microsoft.com/machine-learning-server/install/python-libraries-interpreter)。

在 Azure 上，Microsoft 的 R 和 Python 包，以及解释器提供了 Azure 机器学习和 Azure 服务，如[HDInsight](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-on-azure-hdinsight)，并[Azure 虚拟机](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-azure-vm-on-linux)。 [数据科学虚拟机](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/)包括从多个供应商并将库的工具和来自 Microsoft 的解释器的完全配备的开发工作站。

## <a name="see-also"></a>请参阅

[安装 SQL Server 机器学习服务](install/sql-machine-learning-services-windows-install.md)

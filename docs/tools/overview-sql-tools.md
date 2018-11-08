---
title: SQL 工具和实用程序的 SQL Server、 Azure SQL 数据库和 Azure SQL 数据仓库 |Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ''
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 359144187de1b1a780ba3d866f4a4881c2444442
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49643935"
---
# <a name="sql-tools-and-utilities-for-sql-server-azure-sql-database-and-azure-sql-data-warehouse"></a>SQL 工具和实用程序的 SQL Server、 Azure SQL 数据库和 Azure SQL 数据仓库
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

若要管理 （查询、 监视器等） 您需要使用工具的数据库。 虽然您的数据库可以在云中，Windows上或Linux上运行，但您的工具不需要在与数据库相同的平台上运行。

有许多数据库工具，因此本文提供了说明和指针的一些可用工具的 SQL 数据库使用。 如果需要帮助确定哪种工具所需，请参阅[应使用哪种工具？](#which-tool-should-i-choose)。


## <a name="gui-tools-to-manage-databases"></a>GUI 工具来管理数据库  

下面是主要的图形用户界面 (GUI) 工具：

| 工具 | 描述 | 在上运行 |
|:--|:--|:--|
| [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md) | [!INCLUDE[name-sos](../includes/name-sos-short.md)] 是免费的轻型工具，用于管理数据库，无论在哪里它们正在运行。 此预览版本中提供数据库管理功能，包括扩展的 TRANSACT-SQL 编辑器和操作状态的数据库的可自定义见解。 | **[!INCLUDE[name-sos](../includes/name-sos-short.md)] 在 Windows、 macOS 和 Linux 上运行**。|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | 使用 SQL Server Management Studio (SSMS) 来查询、 设计和管理 SQL Server、 Azure SQL 数据库和 Azure SQL 数据仓库。 | **SSMS 在 Windows 上运行**。|
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | 将 Visual Studio 变成功能强大的开发环境的 SQL Server、 Azure SQL 数据库和 Azure SQL 数据仓库。| **在 Windows 上运行 SSDT**。|
| [Visual Studio Code](https://code.visualstudio.com/)| 在安装 Visual Studio Code 之后, 安装[mssql 扩展](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)用于开发 Microsoft SQL Server、 Azure SQL 数据库和 SQL 数据仓库。| **Visual Studio Code 在 Windows、 macOS 和 Linux 上运行**。|


## <a name="command-line-tools-to-manage-databases"></a>命令行工具来管理数据库

下面是主要的命令行工具：

| 工具 | 描述 | 在上运行 |
|:--|:--|:--|
|[**mssql-cli（预览版）**](mssql-cli.md)|**mssql cli**是交互式的命令行工具，用于查询 SQL Server。 | Windows、 macOS 和 Linux|
| [**sqlpackage**](sqlpackage.md) |**sqlpackage**是一个命令行实用工具，可以自动执行多个数据库开发任务。 macOS 和 Linux 版本的 sqlpackage 目前处于预览状态。 | Windows、 macOS 和 Linux|
|[**SQL Server PowerShell**](../powershell/sql-server-powershell.md)| **SQL Server PowerShell**提供 cmdlet 用于处理 SQL| Windows、 macOS 和 Linux|
| [**sqlcmd**](sqlcmd-utility.md) |**sqlcmd**实用工具，可以输入 TRANSACT-SQL 语句、 系统过程和脚本文件的命令提示符处。 | Windows、 macOS 和 Linux|
|[**bcp**](../2014/tools/bcp-utility.md)|大容量复制程序实用工具 (bcp) 可以在 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例和用户指定格式的数据文件间大容量复制数据。|Windows、 macOS 和 Linux|
|[**mssql 脚本编写器 （预览版）**](https://github.com/Microsoft/mssql-scripter)|**mssql 脚本专家**是多平台命令行体验，用于编写脚本的 SQL Server 数据库|Windows、 macOS 和 Linux|
|[**mssql-conf**](../linux/sql-server-linux-configure-mssql-conf.md)|**mssql conf**配置 Linux 上运行的 SQL Server。|Linux|



## <a name="which-tool-should-i-choose"></a>应该选择哪种工具？

- 若要管理 SQL Server 实例或数据库，在 Windows、 Linux 或 Mac 上的轻型编辑器吗？ 请选择 [[!INCLUDE[name-sos](../includes/name-sos.md)]](../sql-operations-studio/download.md)
- 若要管理 SQL Server 实例或具有 GUI 的完全支持在 Windows 上的数据库吗？ 请选择 [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)
- 执行你想要创建或维护数据库代码，包括编译时验证，重构和设计器支持在 Windows 上？ 请选择 [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
- 你想要使用命令行工具，它的 IntelliSense、 语法高-照明，查询 SQL Server 和的详细信息？ 选择[mssql cli](mssql-cli.md)
- 你是否想要在 Windows、 Linux 或 Mac 上的轻型编辑器中编写 T-SQL 脚本？ 选择[Visual Studio Code](https://code.visualstudio.com/)和[mssql 扩展](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql)



## <a name="additional-tools"></a>其他工具

| 工具 | 描述 |
|:--|:--|
| [配置管理器](../tools/configuration-manager/sql-server-configuration-manager-help.md) | 使用 SQL Server 配置管理器来配置 SQL Server 服务并配置网络连接。 在 Windows 上运行 configuration Manager|
| [SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md) | 使用 SQL Server Migration Assistant 自动将数据库从 Microsoft Access、DB2、MySQL、Oracle 和 Sybase 迁移到 SQL Server。|
| [数据库实验助手](../dea/database-experimentation-assistant-overview.md) | 使用数据库实验助手来评估给定工作负荷的目标的 SQL 版本。 |
| [Distributed Replay](../tools/distributed-replay/install-distributed-replay-overview.md) | 使用 Distributed Replay 功能来帮助您评估将来的 SQL Server 升级的影响。 此外使用 Distributed Replay 来帮助评估硬件和操作系统升级和 SQL Server 优化的影响。 |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | Ssbdiagnose 实用工具可报告 Service Broker 对话或 Service Broker 服务的配置中的问题。 |

如果您正在寻找在此页上未提及的其他工具，请参阅[SQL 命令提示实用工具](command-prompt-utility-reference-database-engine.md)。


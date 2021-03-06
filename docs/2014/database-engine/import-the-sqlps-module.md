---
title: 导入 SQLPS 模块 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e687fd8c7fcd7c21f8aac9b546492a8f9bd4a644
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077233"
---
# <a name="import-the-sqlps-module"></a>导入 SQLPS 模块
  从 PowerShell 管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的建议的方法是将 `sqlps` 模块导入到 Windows PowerShell 2.0 环境中。 该模块将加载并注册 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 管理单元和可管理性程序集。  
  
1.  **开始之前：**  [安全性](#Security)  
  
2.  **若要加载模块，请执行以下操作：**  [加载 sqlps 模块](#LoadSqlps)  
  
## <a name="before-you-begin"></a>开始之前  
 在将 `sqlps` 模块导入到 Windows PowerShell 后，您可以：  
  
-   以交互方式运行 Windows PowerShell 命令。  
  
-   运行 Windows PowerShell 脚本文件。  
  
-   运行 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet。  
  
-   使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 提供程序路径可以浏览 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象的层次结构。  
  
-   使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 可管理性对象模型（例如 Microsoft.SqlServer.Management.Smo）管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 对象。  
  
> [!NOTE]  
>  在两个 SQL Server cmdlet（`Encode-Sqlname` 和 `Decode-Sqlname`）的名称中使用的动词与 Windows PowerShell 2.0 的批准的动词不匹配。 这没有任何影响对其操作，但 Windows PowerShell 将引发警告时`sqlps`模块导入到会话。  
  
###  <a name="Security"></a> 安全性  
 默认情况下，Windows PowerShell 会在脚本执行策略设置为 **Restricted**（即，禁止运行任何 Windows PowerShell 脚本）的情况下运行。 若要加载 `sqlps` 模块，您可以使用 `Set-ExecutionPolicy` cmdlet 来运行已签名脚本或任意脚本。 请仅运行来自受信任源的脚本，并通过使用适当的 NTFS 权限来保证所有输入和输出文件的安全。 有关启用 Windows PowerShell 脚本的详细信息，请参阅 [Running Windows PowerShell Scripts](http://www.microsoft.com/technet/scriptcenter/topics/winpsh/manual/run.mspx)（运行 Windows PowerShell 脚本）。  
  
##  <a name="LoadSqlps"></a> 加载 sqlps 模块  
 **加载 Windows PowerShell 中的 sqlps 模块**  
  
1.  使用`Set-ExecutionPolicy`cmdlet 设置相应的脚本执行策略。  
  
2.  使用`Import-Module`cmdlet 导入 sqlps 模块。 指定`DisableNameChecking`参数，如果你想要禁止显示警告，有关`Encode-Sqlname`和`Decode-Sqlname`。  
  
### <a name="example-powershell"></a>示例 (PowerShell)  
 此示例加载 `sqlps` 模块并且禁用了名称检查。  
  
```  
## Import the SQL Server Module.  
  
Import-Module “sqlps” -DisableNameChecking  
  
```  
  

  
## <a name="see-also"></a>请参阅  
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)   
 [SQL Server PowerShell Provider](../powershell/sql-server-powershell-provider.md)   
 [使用数据库引擎 cmdlet](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
  
  

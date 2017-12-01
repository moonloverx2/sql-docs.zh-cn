---
title: "sys.change_tracking_databases (TRANSACT-SQL) |Microsoft 文档"
ms.custom: 
ms.date: 08/08/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- change_tracking_databases
- sys.change_tracking_databases_TSQL
- sys.change_tracking_databases
- change_tracking_databases_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sys.change_tracking_databases
- change tracking [SQL Server], sys.change_tracking_databases
ms.assetid: bb233baa-2991-4904-a0eb-3772b81121a4
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f2eb40072144b58a09c107f2f9c56a9342ed72e9
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2017
---
# <a name="change-tracking-catalog-views---syschangetrackingdatabases"></a>更改跟踪目录视图-sys.change_tracking_databases
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  为每个启用更改跟踪的数据库返回一行。  

|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|数据库 ID。 它在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中是唯一的。|  
|is_auto_cleanup_on|**bit**|指示在经过配置的保持期后是否自动清除更改跟踪数据：<br /><br /> 0 = Off<br /><br /> 1 = On|  
|retention_period|**int**|如果使用自动清除，保持期将指定在数据库中保留更改跟踪数据的时间长度。|  
|retention_period_units_desc|**nvarchar(60)**|指定保持期的说明：<br /><br /> Minutes<br /><br /> Hours<br /><br /> Days|  
|retention_period_units|**tinyint**|保持期的时间单位：<br /><br /> 1 = Minutes<br /><br /> 2 = Hours<br /><br /> 3 = Days|  
  
## <a name="permissions"></a>Permissions  
 对 sys.change_tracking_databases 进行的权限检查与对 sys.databases 所做的权限检查相同。 如果 sys.change_tracking_databases 的调用方不是数据库的所有者，查看相应行所需的最低权限为 ALTER ANY DATABASE 或 VIEW ANY DATABASE 服务器级权限，或者是 master 数据库或当前数据库中的 CREATE DATABASE 权限。  
  
## <a name="see-also"></a>另请参阅  
 [更改跟踪目录视图 &#40;Transact SQL &#41;](http://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [跟踪数据更改 (SQL Server)](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
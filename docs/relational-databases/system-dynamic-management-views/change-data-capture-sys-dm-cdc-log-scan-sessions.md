---
title: sys.dm_cdc_log_scan_sessions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cdc_log_scan_sessions
- dm_cdc_log_scan_sessions_TSQL
- sys.dm_cdc_log_scan_sessions_TSQL
- sys.dm_cdc_log_scan_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], log scan reporting
- sys.dm_cdc_log_scan_sessions dynamic management view
ms.assetid: d337e9d0-78b1-4a07-8820-2027d0b9f87c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d789ec1dd936b7eb40ecae56226a5879754a2260
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47698585"
---
# <a name="change-data-capture---sysdmcdclogscansessions"></a>变更数据捕获-sys.dm_cdc_log_scan_sessions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  针对当前数据库中的每个日志扫描会话返回一行。 返回的最后一行表示当前会话。 您可以使用此视图返回有关当前日志扫描会话的状态信息，或有关自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上次启动以来所有会话的聚合信息。  
   
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|会话的 ID。<br /><br /> 0 = 此行中返回的数据是自 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例上次启动以来所有会话的聚合。|  
|**start_time**|**datetime**|会话的开始时间。<br /><br /> 当**session_id** = 0 时，聚合的数据收集的开始时间的时间。|  
|**end_time**|**datetime**|会话已结束的时间。<br /><br /> NULL = 会话处于活动状态。<br /><br /> 当**session_id** = 0，最后一个会话已结束的时间。|  
|**duration**|**bigint**|会话的持续时间（以秒为单位）。<br /><br /> 0 = 会话不包含变更数据捕获事务。<br /><br /> 当**session_id** = 0 时，与变更数据捕获事务的所有会话的持续时间 （以秒为单位） 的总和。|  
|**scan_phase**|**nvarchar(200)**|会话的当前阶段。 以下是可能的值和及其说明：<br /><br /> 1： 正在读取配置<br />2： 第一次扫描，生成哈希表<br />3： 第二个扫描<br />4： 第二个扫描<br />5： 第二个扫描<br />6： 架构版本控制<br />7： 最后一次扫描<br />8： 完成<br /><br /> 当**session_id** = 0 时，此值始终为"Aggregate"。|  
|**error_count**|**int**|遇到的错误数。<br /><br /> 当**session_id** = 0 时，在所有会话中的错误总数。|  
|**start_lsn**|**nvarchar(23)**|会话的起始 LSN。<br /><br /> 当**session_id** = 0 时，为最后一个会话的起始 LSN。|  
|**current_lsn**|**nvarchar(23)**|当前正在扫描的 LSN。<br /><br /> 当**session_id** = 0 时，当前 LSN 为 0。|  
|**end_lsn**|**nvarchar(23)**|会话的结束 LSN。<br /><br /> NULL = 会话处于活动状态。<br /><br /> 当**session_id** = 0 时，为最后一个会话的结束 LSN。|  
|**tran_count**|**bigint**|已处理的变更数据捕获事务数。 此计数器在第 2 阶段中填充。<br /><br /> 当**session_id** = 0 时，在所有会话中处理的事务数。|  
|**last_commit_lsn**|**nvarchar(23)**|已处理的最后一个提交日志记录的 LSN。<br /><br /> 当**session_id** = 0 时，为任意会话的最后一个提交日志记录 LSN。|  
|**last_commit_time**|**datetime**|最后一个提交日志记录的处理时间。<br /><br /> 当**session_id** = 0 时，为任意会话的最后一个提交日志记录的时间。|  
|**log_record_count**|**bigint**|扫描的日志记录数。<br /><br /> 当**session_id** = 0 时，所有会话的扫描记录数。|  
|**schema_change_count**|**int**|检测到的数据定义语言 (DDL) 操作数。 此计数器在第 6 阶段填充。<br /><br /> 当**session_id** = 0 时，所有会话中已处理的 DDL 操作的数目。|  
|**command_count**|**bigint**|已处理的命令数。<br /><br /> 当**session_id** = 0 时，所有会话中处理的命令数。|  
|**first_begin_cdc_lsn**|**nvarchar(23)**|包含变更数据捕获事务的第一个 LSN。<br /><br /> 当**session_id** = 0 时，包含变更数据捕获事务的第一个 LSN。|  
|**last_commit_cdc_lsn**|**nvarchar(23)**|包含变更数据捕获事务的最后一个提交日志记录的 LSN。<br /><br /> 当**session_id** = 0，最后一个提交日志记录的 LSN 的任何会话包含变更数据捕获事务|  
|**last_commit_cdc_time**|**datetime**|包含变更数据捕获事务的最后一个提交日志记录的处理时间。<br /><br /> 当**session_id** = 0，最后一个提交日志记录的任何会话包含变更数据捕获事务的时间。|  
|**延迟**|**int**|差异，以秒为单位，之间**end_time**并**last_commit_cdc_time**会话中。 此计数器在第 7 阶段的最后填充。<br /><br /> 当**session_id** = 0 时，由某个会话记录的最后一个非零滞后值。|  
|**empty_scan_count**|**int**|不包含变更数据捕获事务的连续会话数。|  
|**failed_sessions_count**|**int**|失败的会话数。|  
  
## <a name="remarks"></a>备注  
 只要启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例，就会重置此动态管理视图中的值。  
  
## <a name="permissions"></a>Permissions  
 需要 VIEW DATABASE STATE 权限到查询**sys.dm_cdc_log_scan_sessions**动态管理视图。 动态管理视图权限的详细信息，请参阅[动态管理视图和函数&#40;TRANSACT-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)。  
  
## <a name="examples"></a>示例  
 下例返回最新会话的信息。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT session_id, start_time, end_time, duration, scan_phase  
    error_count, start_lsn, current_lsn, end_lsn, tran_count  
    last_commit_lsn, last_commit_time, log_record_count, schema_change_count  
    command_count, first_begin_cdc_lsn, last_commit_cdc_lsn,   
    last_commit_cdc_time, latency, empty_scan_count, failed_sessions_count  
FROM sys.dm_cdc_log_scan_sessions  
WHERE session_id = (SELECT MAX(b.session_id) FROM sys.dm_cdc_log_scan_sessions AS b);  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [sys.dm_cdc_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-errors.md)  
  
  


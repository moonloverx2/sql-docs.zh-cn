---
title: sys.availability_replicas (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_replicas_TSQL
- availability_replicas
- sys.availability_replicas
- sys.availability_replicas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_replicas catalog view
ms.assetid: 0a06e9b6-a1e4-4293-867b-5c3f5a8ff62c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4562a87cdf037a14588cdfca419448531e477204
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47797445"
---
# <a name="sysavailabilityreplicas-transact-sql"></a>sys.availability_replicas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

为每个属于 WSFC 故障转移群集中任何 Always On 可用性组的可用性副本返回一行。  
  
如果本地服务器实例无法与 WSFC 故障转移群集联系，例如由于群集关闭或丢失了仲裁，则仅返回本地可用性副本的行。 这些行将仅包含在元数据中本地缓存的数据列。  
  
 
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|副本的唯一 ID。|  
|**group_id**|**uniqueidentifier**|副本所属于的可用性组的唯一 ID。|  
|**replica_metadata_id**|**int**|数据库引擎中可用性副本的本地元数据对象的 ID。|  
|**replica_server_name**|**nvarchar(256)**|承载此副本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的服务器名称；对于非默认实例，则为其实例名称。|  
|**owner_sid**|**varbinary(85)**|为此可用性副本的外部所有者向此服务器实例注册的安全标识符 (SID)。<br /><br /> 对于非本地可用性副本则为 NULL。|  
|**endpoint_url**|**nvarchar(128)**|用户指定的数据库镜像端点的字符串表示形式，该数据库镜像端点由用于数据同步的主副本和辅助副本之间的连接使用。 有关这些端点 URL 语法的信息，请参阅[在添加或修改可用性副本时指定端点 URL (SQL Server)](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)。<br /><br /> NULL = 无法联系 WSFC 故障转移群集。<br /><br /> 若要更改此终结点，请使用 ENDPOINT_URL 选项[ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]语句。|  
|**availability_mode**|**tinyint**|副本的可用性模式，可为下列值之一：<br /><br /> 0&#124;异步提交。 主副本可以不必等待辅助副本将日志写入磁盘，即可提交事务。<br /><br /> 1&#124;同步提交。 主副本等待提交给定的事务，直到辅助副本将事务写入磁盘。<br /><br />4&#124;仅配置。 主副本同步发送到副本的可用性组配置元数据。 用户数据不会传输到副本。 可在 SQL Server 2017 CU1 及更高版本。<br /><br /> 有关详细信息，请参阅 [可用性模式（AlwaysOn 可用性组）](../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md)。|  
|**availability_mode_desc**|**nvarchar(60)**|说明**可用性\_模式**、 一个的：<br /><br /> 异步\_提交<br /><br /> 同步\_提交<br /><br /> 配置\_仅<br /><br /> 若要更改此设置可用性副本的可用性模式，使用的 AVAILABILITY_MODE 选项[ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]语句。<br/><br>不能将副本的可用性模式更改为配置\_仅。 不能更改配置\_仅副本添加到辅助或主副本。 |  
|**故障转移\_模式**|**tinyint**|[故障转移模式](../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)可用性副本之一的：<br /><br /> 0&#124;手动故障转移。 设置为手动故障转移的向辅助副本的故障转移必须由数据库管理员手动启动。 要执行的故障转移的类型将依赖于是否同步辅助副本，如下所示：<br /><br /> 如果可用性副本未同步或者仍在同步，则只能发生强制故障转移（可能会丢失数据）。<br /><br /> 如果设置为同步提交可用性模式 (**可用性\_模式**= 1) 和该可用性副本当前是已同步、 手动故障转移不会发生数据丢失。<br /><br /> 1&#124;自动故障转移。 副本是自动故障转移的潜在目标。  可用性模式设置为同步提交，才支持自动故障转移 (**可用性\_模式**= 1) 并且可用性副本当前已同步。<br /><br /> 若要查看可用性副本中的每个可用性数据库的数据库同步运行状况的汇总，请使用**同步\_运行状况**并**同步\_运行状况\_desc**的列[sys.dm_hadr_availability_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql.md)动态管理视图。 此汇总信息考虑每个可用性数据库的同步状态和其可用性副本的可用性模式。<br /><br /> **注意：** 若要查看给定的可用性数据库的同步运行状况，请查询**同步\_状态**并**同步\_运行状况**列[sys.dm_hadr_database_replica_states](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)动态管理视图。|  
|**故障转移\_模式下\_desc**|**nvarchar(60)**|说明**故障转移\_模式**、 一个的：<br /><br /> MANUAL<br /><br /> AUTOMATIC<br /><br /> 若要更改的故障转移模式，请使用故障转移\_模式的选项[ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]语句。|  
|**session\_timeout**|**int**|超时期限（秒）。 超时期限是指副本接收来自其他副本的消息而等待的最长时间，超过此时间，将主副本和辅助副本之间的连接视为已失败。 会话超时检测辅助副本是否与主副本相连接。<br /><br /> 在检测到与辅助副本连接失败时，主副本将辅助副本不是\_已同步。 在检测到与辅助副本的连接失败时，辅助副本只会尝试重新连接。<br /><br /> **注意：** 会话超时不会导致自动故障转移。<br /><br /> 若要更改此值，使用的 SESSION_TIMEOUT 选项[ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]语句。|  
|**主\_角色\_允许\_连接**|**tinyint**|可用性是允许所有连接还是仅允许读写连接，其中：<br /><br /> 2 = 所有（默认值）<br /><br /> 3 = 读写|  
|**primary\_role\_allow\_connections\_desc**|**nvarchar(60)**|说明**主\_角色\_允许\_连接**、 一个的：<br /><br /> ALL<br /><br /> 读取\_编写|  
|**辅助\_角色\_允许\_连接**|**tinyint**|正在履行辅助角色的可用性副本（也就是辅助副本）是否可以接受来自客户端的连接，可为下列值之一：<br /><br /> 0 = 否。 不允许连接到辅助副本中的数据库，且不支持读取这些数据库。 这是默认设置。<br /><br /> 1 = 只读。 仅允许针对辅助副本中的数据库进行只读连接。 副本中的所有数据库都可用于读访问。<br /><br /> 2 = 全部。 允许针对辅助副本中的数据库的所有连接进行只读访问。<br /><br /> 有关详细信息，请参阅 [活动辅助副本：可读辅助副本（AlwaysOn 可用性组）](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)概念。|  
|**secondary_role_allow_connections_desc**|**nvarchar(60)**|说明**secondary_role_allow_connections**、 一个的：<br /><br /> 是<br /><br /> READ_ONLY<br /><br /> ALL|  
|**create_date**|**datetime**|副本的创建日期。<br /><br /> NULL = 副本不位于此服务器实例上。|  
|**modify_date**|**datetime**|上次修改副本的日期。<br /><br /> NULL = 副本不位于此服务器实例上。|  
|**backup_priority**|**int**|表示相对于同一可用性组中的其他副本，在此副本上执行备份的用户指定的优先级。 该值是范围 0..100 中的整数。<br /><br /> 有关详细信息，请参阅 [活动辅助副本：辅助副本备份（AlwaysOn 可用性组）](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)概念。|  
|**read_only_routing_url**|**nvarchar(256)**|只读可用性副本的连接端点 (URL)。 有关详细信息，请参阅 [为可用性组配置只读路由 (SQL Server)](../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)。|  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>Permissions  
 要求具有服务器实例的 VIEW ANY DEFINITION 权限。  
  
## <a name="see-also"></a>请参阅  
 [sys.availability_groups (Transact-SQL)](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [AlwaysOn 可用性组概述 (SQL Server)](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 可用性组 (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [监视可用性组 (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [监视可用性组 (Transact-SQL)](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  

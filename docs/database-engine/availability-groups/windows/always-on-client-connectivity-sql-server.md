---
title: AlwaysOn 客户端连接 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ee9f18e30c19ed1318f28bb4ae97bf137ec679c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47753865"
---
# <a name="always-on-client-connectivity-sql-server"></a>AlwaysOn 客户端连接 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  本主题介绍与 AlwaysOn 可用性组进行客户端连接时的注意事项，包括针对客户端配置和设置的先决条件、限制和建议。  
  
 **本主题内容：**  
  
-   [客户端连接支持](#ClientConnSupport)  
  
-   [相关任务](#RelatedTasks)  
  
##  <a name="ClientConnSupport"></a> 客户端连接支持  
 以下部分提供有关对客户端连接的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 支持的信息。  
  
 **驱动程序支持**  
  
 下表概述了 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]的驱动程序支持：  
  
|驱动程序|多子网故障转移|应用程序意向|只读路由|多子网故障转移：更快的单子网端点故障转移|多子网故障转移：SQL 群集实例的命名实例解析|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|用户帐户控制|是|是|是|用户帐户控制|  
|SQL Native Client 11.0 OLEDB|否|是|是|否|否|  
|ADO.NET（结合使用 .NET Framework 4.0 和连接性修补程序）*|用户帐户控制|是|是|是|用户帐户控制|  
|ADO.NET（结合使用 .NET Framework 3.5 SP1 和连接性修补程序）**|用户帐户控制|是|是|是|用户帐户控制|  
|Microsoft JDBC driver 4.0 for SQL Server|用户帐户控制|是|是|是|用户帐户控制| 
|适用于 SQL Server 的 Microsoft OLE DB 驱动程序|用户帐户控制|是|是|是|用户帐户控制| 
  
 * 下载 ADO .NET（结合使用 .NET Framework 4.0）的连接性修补程序：[http://support.microsoft.com/kb/2600211](http://support.microsoft.com/kb/2600211)。  
  
 ** 下载 ADO .NET（结合使用 .NET Framework 3.5 SP1）的连接性修补程序：[http://support.microsoft.com/kb/2654347](http://support.microsoft.com/kb/2654347)。  
 
 *为 SQL Server 下载新的 Microsoft OLE DB 驱动程序：[https://www.microsoft.com/en-us/download/details.aspx?id=56730 ](https://www.microsoft.com/en-us/download/details.aspx?id=56730)。  

> [!IMPORTANT]  
>  要连接到一个可用性组侦听器，客户端必须使用 TCP 连接字符串。  
  
##  <a name="RelatedTasks"></a> 相关任务  
  
-   [创建和配置可用性组 (SQL Server)](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [创建或配置可用性组侦听程序 (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
## <a name="see-also"></a>另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [故障转移群集和 AlwaysOn 可用性组 (SQL Server)](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)   
 [可用性组侦听程序、客户端连接和应用程序故障转移 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)   
 [关于对可用性副本的客户端连接访问 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/about-client-connection-access-to-availability-replicas-sql-server.md)   
 [用于高可用性和灾难恢复的 Microsoft SQL Server AlwaysOn 解决方案指南](http://go.microsoft.com/fwlink/?LinkId=227600)   
 [SQL Server AlwaysOn 团队博客：SQL Server AlwaysOn 团队官方博客](https://blogs.msdn.microsoft.com/sqlalwayson/)   
 [从运行 Windows Server 2003、Windows Vista、Windows Server 2008、Windows 7 或 Windows Server 2008 R2 的计算机重新建立 IPSec 连接时出现长时间延迟](http://support.microsoft.com/kb/980915)   
 [群集服务需要大约 30 秒对 Windows Server 2008 R2 中的 IPv6 IP 地址进行故障转移](http://support.microsoft.com/kb/2578113)   
 [如果群集与应用程序服务器之间不存在路由器，则故障转移操作的速度会很慢](http://support.microsoft.com/kb/2582281)  
  
  

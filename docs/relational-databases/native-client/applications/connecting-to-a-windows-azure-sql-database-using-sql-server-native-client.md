---
title: 连接到 Windows Azure SQL 数据库使用 SQL Server 本机客户端 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d555596fd9a15f985b8b75fe4b56d89d377191f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47720225"
---
# <a name="connecting-to-a-windows-azure-sql-database-using-sql-server-native-client"></a>使用 SQL Server Native Client 连接到 Windows Azure SQL Database
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  有关示例，演示如何连接到[!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)]使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client，请参阅[开发： 操作指南主题 （Windows Azure SQL 数据库）](http://msdn.microsoft.com/library/ee621787.aspx)。  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>连接到 SQL Database 时的已知问题  
 以下是使用 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client 连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 时的一些已知问题：  
  
-   使用建立的连接**SQLBrowseConnect**可能会被拒绝**SQLBrowseConnect**阶段中使用。  例如，如果在第一次调用中发送驱动程序名称，在第二次调用中发送服务器和凭据（用户名和密码），建立连接，然后在第三次调用中发送数据库名称和语言。  第三次调用将导致 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 发出 USE 语句来更改数据库。 但是，在 [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] 中不支持 USE 语句，因此生成以下错误：  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>请参阅  
 [使用 SQL Server Native Client 生成应用程序](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  

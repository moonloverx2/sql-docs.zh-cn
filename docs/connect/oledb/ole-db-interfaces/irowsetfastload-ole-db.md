---
title: IRowsetFastLoad (OLE DB) |Microsoft Docs
description: IRowsetFastLoad (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IRowsetFastLoad interface
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 722437a9d9c093dd91562aae2a9bf0b1bb5cb5b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611093"
---
# <a name="irowsetfastload-ole-db"></a>IRowsetFastLoad (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  IRowsetFastLoad 接口公开了对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 基于内存的大容量复制操作的支持。 OLE DB 驱动程序对于 SQL Server 使用者使用的界面快速将数据添加到现有[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]表。  
  
 如果将会话的 SSPROP_ENABLEFASTLOAD 设置为 VARIANT_TRUE，则无法读取后续从该会话返回的行集中的数据。 将 SSPROP_ENABLEFASTLOAD 设置为 VARIANT_TRUE 时，在会话上创建的所有行集将属于 IRowsetFastLoad 类型。 IRowsetFastLoad 行集不支持行集提取功能，因此无法读取这些行集中的数据。  
  
## <a name="in-this-section"></a>本节内容  
  
|方法|描述|  
|------------|-----------------|  
|[Irowsetfastload:: Commit &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md)|标记一批插入的行的末尾并将这些行写入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表。|  
|[Irowsetfastload:: Insertrow &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-insertrow-ole-db.md)|将行添加到大容量复制行集中。|  
  
## <a name="see-also"></a>另请参阅  
 [接口&#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)   
 [使用 IRowsetFastLoad 大容量复制数据 (OLE DB)](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md)   
 [使用 IROWSETFASTLOAD 和 ISEQUENTIALSTREAM 将 BLOB 数据发送到 SQL SERVER (OLE DB)](../../oledb/ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
  

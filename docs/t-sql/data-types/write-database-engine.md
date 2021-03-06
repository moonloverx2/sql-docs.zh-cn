---
title: Write（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs:
- TSQL
helpviewer_keywords:
- Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8767ac33fc1f24f266e45d6eac45de9dcfc65e18
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830275"
---
# <a name="write-database-engine"></a>Write（数据库引擎）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Write 将 SqlHierarchyId 的二进制表示形式写出到传入的 BinaryWriter 中。 无法通过使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 来调用 Write。 请改为使用 CAST 或 CONVERT。
  
## <a name="syntax"></a>语法  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>参数  
*w*  
一个 BinaryWriter 对象，此 hierarchyid 节点的二进制表示形式将写在该对象中。
  
## <a name="return-types"></a>返回类型  
CLR 返回类型：void
  
## <a name="remarks"></a>Remarks  
必要时（例如，从 hierarchyid 列加载数据时），[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将在内部使用 Write。 在 hierarchyid 和 varbinary 之间进行转换时，也将在内部调用 Write。
  
## <a name="examples"></a>示例  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>另请参阅
[Read（数据库引擎）](../../t-sql/data-types/read-database-engine.md)  
[ToString（数据库引擎）](../../t-sql/data-types/tostring-database-engine.md)  
[CAST 和 CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[hierarchyid 数据类型方法引用](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  

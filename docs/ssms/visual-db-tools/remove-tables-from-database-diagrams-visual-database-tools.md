---
title: 从数据库关系图中移除表 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
ms.assetid: 11afcfa1-816b-419c-9bc7-3abf366f4c3c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cdd5407b13719451d960be51321f47bcc0dc4754
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50100048"
---
# <a name="remove-tables-from-database-diagrams-visual-database-tools"></a>从数据库关系图中移除表 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
您可以从数据库关系图中移除表。 移除表不会更改数据库。 该表及其与其他表的关系将继续存在于数据库中。  
  
### <a name="to-remove-a-table-from-a-database-diagram"></a>从数据库关系图中移除表  
  
1.  在数据库关系图中，选择要移除的表。  
  
2.  右键单击该表，然后从快捷菜单中选择“从关系图中删除表”。  
  
    -或 -  
  
    按 Esc 键。  
  
    如果该表有未保存的更改（由于您在数据库关系图中编辑过它），则在移除该表之前，会显示一条消息，提示您保存该表。  
  
此时，已从关系图中移除了该表，但它会继续存在于数据库中。  
  
## <a name="see-also"></a>另请参阅  
[使用数据库关系图 (Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[如何从数据库中删除表 (Visual Database Tools)](http://msdn.microsoft.com/ca6aa3e9-9885-44c3-bafc-aec441fd97ec)  
  

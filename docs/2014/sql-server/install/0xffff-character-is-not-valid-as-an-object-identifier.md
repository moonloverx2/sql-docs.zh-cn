---
title: 0xFFFF 字符不是有效的对象标识符 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- 0xFFFF character [SQL Server]
ms.assetid: b2c9c8cf-9194-45e0-be6b-2d5ec52e8153
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7a91a64358ccd23e923d30a291b044800ce710ae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48112769"
---
# <a name="0xffff-character-is-not-valid-as-an-object-identifier"></a>0xFFFF 字符不能用作对象标识符
  升级顾问在对象标识符中检测到 0xFFFF 字符。 在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本中，当数据库兼容模式设置为 90 或更高时，不能引用或重命名标识符中包含该字符的对象（如数据库、表和列）。 升级到 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 时，用户数据库将保持其兼容模式。 在将数据库兼容模式更改为 90 或更高之前，请重命名包含 0xFFFF 字符的对象。  
  
 有关标识符的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“标识符”。 有关数据库兼容模式的详细信息，请参阅 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中的“sp_dbcmptlevel”。  
  
## <a name="component"></a>组件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="see-also"></a>请参阅  
 [数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 升级顾问&#91;新&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  

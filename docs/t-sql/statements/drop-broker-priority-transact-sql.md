---
title: "删除 BROKER 优先级 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_BROKER_PRIORITY_TSQL
- DROP BROKER PRIORITY
dev_langs:
- TSQL
helpviewer_keywords:
- DROP BROKER PRIORITY statement
ms.assetid: 09ee6c5b-af94-4a4b-a0e2-f9eac50e43aa
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 254914f3b92289faf19a37b4651e7c95804ac791
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="drop-broker-priority-transact-sql"></a>DROP BROKER PRIORITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  从当前数据库中删除一个会话优先级。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
DROP BROKER PRIORITY ConversationPriorityName  
[;]  
```  
  
## <a name="arguments"></a>参数  
 *ConversationPriorityName*  
 指定要删除的会话优先级的名称。  
  
## <a name="remarks"></a>注释  
 删除会话优先级时，现有会话将继续使用由该会话优先级分配的优先级来运行。  
  
## <a name="permissions"></a>Permissions  
 用于创建会话优先级的权限默认授予 db_ddladmin 或 db_owner 固定数据库角色以及 sysadmin 固定服务器角色的成员。 需要对数据库拥有 ALTER 权限。  
  
## <a name="examples"></a>示例  
 下例删除名为 `InitiatorAToTargetPriority` 的会话优先级。  
  
```  
DROP BROKER PRIORITY InitiatorAToTargetPriority;  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [ALTER BROKER 优先级 &#40;Transact SQL &#41;](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [创建 BROKER 优先级 &#40;Transact SQL &#41;](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [sys.conversation_priorities &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-conversation-priorities-transact-sql.md)  
  
  
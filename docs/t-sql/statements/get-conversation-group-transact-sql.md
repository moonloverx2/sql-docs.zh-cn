---
title: "获取会话组 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GET
- CONVERSATION_GROUP_TSQL
- GET_TSQL
- GET_CONVERSATION_GROUP_TSQL
- GET CONVERSATION GROUP
- CONVERSATION GROUP
- GET CONVERSATION
- GET_CONVERSATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GET CONVERSATION GROUP statement
- conversations [Service Broker], groups
ms.assetid: 4da8a855-33c0-43b2-a49d-527487cb3b5c
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5cf1bd19e9ccc290c2c822ab59f00be75d447ba1
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="get-conversation-group-transact-sql"></a>GET CONVERSATION GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  为下一个要收到的消息返回会话组标识符，并锁定包含消息的会话的会话组。 会话组标识符可用于在检索消息本身之前检索会话状态信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
[ WAITFOR ( ]  
   GET CONVERSATION GROUP @conversation_group_id  
      FROM <queue>  
[ ) ] [ , TIMEOUT timeout ]  
[ ; ]  
  
<queue> ::=  
{  
    [ database_name . [ schema_name ] . | schema_name . ] queue_name  
}  
```  
  
## <a name="arguments"></a>参数  
 WAITFOR  
 指定如果当前没有消息，则 GET CONVERSATION GROUP 语句将等待消息到达队列。  
  
 *@conversation_group_id*  
 用于存储 GET CONVERSATION GROUP 语句返回的会话组 ID 的变量。 变量必须为类型**uniqueidentifier**。 如果没有可用的会话组，则该变量设置为 NULL。  
  
 FROM  
 指定要从中获取会话组的队列。  
  
 *database_name*  
 包含从中获取会话组的队列的数据库的名称。 如果没有*database_name*提供，则默认为当前数据库。  
  
 *schema_name*  
 拥有从中获取会话组的队列的架构的名称。 如果没有*schema_name*提供，则默认为当前用户的默认架构。  
  
 *queue_name*  
 要从中获取会话组的队列的名称。  
  
 超时*超时*  
 指定 Service Broker 等待消息到达队列的时间（毫秒）。 该子句只能与 WAITFOR 子句一起使用。 如果使用 WAITFOR 语句不包含此子句或*超时*为-1，则等待时间没有限制。 如果在超时到期，GET CONVERSATION GROUP 设置 *@conversation_group_id* 变量为 NULL。  
  
## <a name="remarks"></a>注释  
  
> [!IMPORTANT]  
>  如果 GET CONVERSATION GROUP 语句不是在批处理或存储的过程的第一个语句，必须以分号结尾前面的语句 (**;**)，则[!INCLUDE[tsql](../../includes/tsql-md.md)]语句终止符。  
  
 如果 GET CONVERSATION GROUP 语句中指定的队列不可用，则该语句将失败，并返回一个 [!INCLUDE[tsql](../../includes/tsql-md.md)] 错误。  
  
 该语句返回满足以下所有条件的下一个会话组：  
  
-   可以成功锁定该会话组。  
  
-   该会话组在队列中有可用的消息。  
  
-   在满足上述条件的所有会话组中，该会话组具有最高的优先级。 会话组的优先级是分配给属于该组的成员并且在队列中具有消息的任何会话的最高优先级。  
  
 在相同事务中连续调用 GET CONVERSATION GROUP 可锁定多个会话组。 如果没有可用的会话组，则该语句返回 NULL 作为会话组标识符。  
  
 指定 WAITFOR 子句后，该语句将等待指定的超时时间，或等到会话组可用为止。 如果在语句等待期间删除队列，则语句会立即返回一个错误。  
  
 GET CONVERSATION GROUP 在用户定义函数中无效。  
  
## <a name="permissions"></a>Permissions  
 若要从队列中获取会话组标识符，则当前用户必须具有对队列的 RECEIVE 权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-getting-a-conversation-group-waiting-indefinitely"></a>A. 获取会话组，无限期等待  
 下例将 `@conversation_group_id` 设置为 `ExpenseQueue` 中下一个可用消息的会话组标识符。 该命令将等到消息变得可用为止。  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
WAITFOR (  
 GET CONVERSATION GROUP @conversation_group_id  
     FROM ExpenseQueue  
) ;  
```  
  
### <a name="b-getting-a-conversation-group-waiting-one-minute"></a>B. 获取会话组，等待一分钟  
 下例将 `@conversation_group_id` 设置为 `ExpenseQueue` 中下一个可用消息的会话组标识符。 如果在一分钟内没有出现任何可用消息，GET CONVERSATION GROUP 将直接返回而不更改 `@conversation_group_id` 的值。  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER  
  
WAITFOR (  
    GET CONVERSATION GROUP @conversation_group_id   
    FROM ExpenseQueue ),  
TIMEOUT 60000 ;  
```  
  
### <a name="c-getting-a-conversation-group-returning-immediately"></a>C. 获取会话组，立即返回  
 下例将 `@conversation_group_id` 设置为 `ExpenseQueue` 中下一个可用消息的会话组标识符。 如果没有任何可用的消息，`GET CONVERSATION GROUP` 将立即返回而不更改 `@conversation_group_id`。  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
GET CONVERSATION GROUP @conversation_group_id  
FROM AdventureWorks.dbo.ExpenseQueue ;  
```  
  
## <a name="see-also"></a>另请参阅  
 [BEGIN DIALOG CONVERSATION &#40;Transact SQL &#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [移动对话 &#40;Transact SQL &#41;](../../t-sql/statements/move-conversation-transact-sql.md)  
  
  

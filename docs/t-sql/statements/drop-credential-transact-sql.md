---
title: DROP CREDENTIAL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/19/2015
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP CREDENTIAL
- DROP_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing credentials
- DROP CREDENTIAL statement
- credentials [SQL Server], DROP CREDENTIAL statement
- authentication [SQL Server], credentials
- deleting credentials
- dropping credentials
ms.assetid: df22c826-317d-45a6-b078-186acb65f71e
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: dcf4a0d7492e36432ecec80778a49fa5ba37a7d2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47711385"
---
# <a name="drop-credential-transact-sql"></a>DROP CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  从服务器中删除凭据。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
DROP CREDENTIAL credential_name  
```  
  
## <a name="arguments"></a>参数  
 credential_name  
 要从服务器中删除的凭据的名称。  
  
## <a name="remarks"></a>Remarks  
 若要删除与凭据关联的机密内容而不删除凭据本身，请使用 [ALTER CREDENTIAL](../../t-sql/statements/alter-credential-transact-sql.md)。  
  
 可以在 **sys.credentials** 目录视图中查看有关凭据的信息。  
  
> [!WARNING]  
>  代理与凭据关联。 删除代理使用的凭据会让关联的代理处于不可用状态。 删除代理使用的凭据时，请使用 [sp_delete_proxy (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md) 删除代理并使用 [sp_add_proxy (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md) 重新创建关联的代理。  
  
## <a name="permissions"></a>Permissions  
 需要 ALTER ANY CREDENTIAL 权限。 如果要删除系统凭据，则要求具有 CONTROL SERVER 权限。  
  
## <a name="examples"></a>示例  
 以下示例删除名为 `Saddles` 的凭据。  
  
```  
DROP CREDENTIAL Saddles;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [凭据（数据库引擎）](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [ALTER CREDENTIAL (Transact-SQL)](../../t-sql/statements/alter-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

---
title: "ALTER DATABASE （Azure SQL 数据仓库） |Microsoft 文档"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 03/03/2017
ms.prod: 
ms.reviewer: 
ms.service: sql-warehouse
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: da712a46-5f8a-4888-9d33-773e828ba845
caps.latest.revision: 20
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b5e328da952c853409437f7c3a4993f17022de22
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-azure-sql-data-warehouse"></a>ALTER DATABASE （Azure SQL 数据仓库）
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx_md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

修改名称、 最大大小或数据库的服务目标。  
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for Azure SQL Data Warehouse  
  
ALTER DATABASE database_name  

  MODIFY NAME = new_database_name  
| MODIFY ( <edition_option> [, ... n] )  
  
<edition_option> ::=   
      MAXSIZE = { 250 | 500 | 750 | 1024 | 5120 | 10240 | 20480 | 30720 | 40960 | 51200 | 61440 | 71680 | 81920 | 92160 | 102400 | 153600 | 204800 | 245760 } GB  
    | SERVICE_OBJECTIVE = { 'DW100' | 'DW200' | 'DW300' | 'DW400' | 'DW500' | 'DW600' | 'DW1000' | 'DW1200' | 'DW1500' | 'DW2000' | 'DW3000' | 'DW6000'}  
```  
  
## <a name="arguments"></a>参数  
*database_name*  
指定要修改数据库的名称。  

MODIFY NAME = *new_database_name*  
重命名数据库名称指定为*new_database_name*。  
  
MAXSIZE  
数据库可能会增长到最大大小。 设置此值禁止除大小组以外的数据库大小的增长。 默认值*MAXSIZE*时未指定为 10240 GB (10 TB)。 其他可能的值范围为 250 GB 达 240 TB。  
  
SERVICE_OBJECTIVE  
指定性能级别。 有关服务目标的详细信息[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]，请参阅[SQL 数据仓库上的缩放性能](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-manage-compute-overview/)。  
  
## <a name="permissions"></a>Permissions  
需要以下权限：  
  
-   服务器级别主体登录名 （由设置过程创建的一个），或  
  
-   成员`dbmanager`数据库角色。  
  
数据库的所有者不能更改数据库，除非所有者为属于`dbmanager`角色。  
  
## <a name="general-remarks"></a>一般备注  
当前数据库必须是不同的数据库，而如果变更，因此**连接到 master 数据库时，必须运行 ALTER**。  
  
SQL 数据仓库设置为 COMPATIBILITY_LEVEL 130，并且不能更改。 有关更多详细信息，请参阅[与 Azure SQL 数据库中的兼容性级别 130 改进查询性能](https://azure.microsoft.com/documentation/articles/sql-database-compatibility-level-query-performance-130/)。
  
若要减小数据库大小，使用[DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)。  
  
## <a name="limitations-and-restrictions"></a>限制和局限  
若要运行 ALTER DATABASE，数据库必须处于联机状态，并不能处于暂停状态。  
  
ALTER DATABASE 语句必须在自动提交模式，这是默认事务管理模式下运行。 此项设置中的连接设置。  
  
ALTER DATABASE 语句不能为用户定义的事务的一部分。

无法更改数据库排序规则。  
  
## <a name="examples"></a>示例  
在运行这些示例之前，请确保你更改该数据库不是当前数据库。 当前数据库必须是不同的数据库，而如果变更，因此**连接到 master 数据库时，必须运行 ALTER**。  

### <a name="a-change-the-name-of-the-database"></a>A. 更改数据库的名称  

```  
ALTER DATABASE AdventureWorks2012  
MODIFY NAME = Northwind;  
```  
  
### <a name="b-change-max-size-for-the-database"></a>B. 更改数据库的最大大小  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB );  
```  
  
### <a name="c-change-the-performance-level"></a>C. 更改性能级别  
  
```  
ALTER DATABASE dw1 MODIFY ( SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
### <a name="d-change-the-max-size-and-the-performance-level"></a>D. 更改的最大大小和性能级别  
  
```  
ALTER DATABASE dw1 MODIFY ( MAXSIZE=10240 GB, SERVICE_OBJECTIVE= 'DW1200' );  
```  
  
## <a name="see-also"></a>另请参阅  
[CREATE DATABASE （Azure SQL 数据仓库）](../../t-sql/statements/create-database-azure-sql-data-warehouse.md)
[SQL 数据仓库的参考主题的列表](https://azure.microsoft.com/en-us/documentation/articles/sql-data-warehouse-overview-reference/)  
  
---
title: "getURL 方法 (java.lang.String) |Microsoft 文档"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerCallableStatement.getURL (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb709f6b-64e1-4d0c-a704-290891627dd7
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1c3acee5de06e6f8ac611ce2a3deaa4f6c3ed9a1
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="geturl-method-javalangstring"></a>getURL 方法 (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  作为给定参数名称的 Java 编程语言中的 URL 对象中检索指定参数的值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.net.URL getURL(java.lang.String s)  
```  
  
#### <a name="parameters"></a>Parameters  
 *s*  
  
 A**字符串**，其中包含参数名称。  
  
## <a name="return-value"></a>返回值  
 一个 URL。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>注释  
 由 java.sql.CallableStatement 接口中的 getURL 方法指定此 getURL 方法。  
  
## <a name="see-also"></a>另请参阅  
 [getURL 方法 &#40;SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/geturl-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成员](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 类](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
---
title: setPortNumber 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setPortNumber
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 59c5fa23-bc1a-4142-af17-70e275f0b833
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15e0ff764637869428945ab3eb4b6c44b055b436
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728195"
---
# <a name="setportnumber-method-sqlserverdatasource"></a>setPortNumber 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  设置用于与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 通信的端口号。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void setPortNumber(int portNumber)  
```  
  
#### <a name="parameters"></a>Parameters  
 *portNumber*  
  
 一个 int 值，此值包含端口号。  
  
## <a name="remarks"></a>Remarks  
 此端口号是打开与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的套接字连接时使用的 TCP/IP 端口号。 如果未设置 portNumber 属性，[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md) 方法将返回默认值 1433。  
  
> [!NOTE]  
>  SetPortNumber 方法不对进行任何范围检查传入的端口值。 可以传递无效，如 99999，而不引发错误的端口号。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDataSource 成员](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 类](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

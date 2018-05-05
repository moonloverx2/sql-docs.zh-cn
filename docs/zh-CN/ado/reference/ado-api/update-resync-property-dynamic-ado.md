---
title: 更新重新同步属性的动态 (ADO) |Microsoft 文档
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Update Resync property [ADO]
ms.assetid: 8a3bb608-66d7-4128-a3ef-84cb0556de0d
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 854ddd7136c6200a6783ef2ecdb2b1c2f2abf7e7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="update-resync-property-dynamic-ado"></a>更新重新同步属性的动态 (ADO)
指定是否[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)方法后跟一种隐式[重新同步](../../../ado/reference/ado-api/resync-method.md)方法操作，如果是，该操作的作用域。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回一个或多个[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)值。  
  
## <a name="remarks"></a>注释  
 可能合并 ADCPROP_UPDATERESYNC_ENUM 的值，但已表示值的其余部分的组合的 adResyncAll 除外。  
  
 常量**adResyncConflicts**存储的重新同步值作为基础值，但不会覆盖挂起的更改。  
  
 **更新重新同步**动态属性追加到[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象[属性](../../../ado/reference/ado-api/properties-collection-ado.md)集合时[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)属性设置为**adUseClient**。  
  
## <a name="applies-to"></a>适用范围  
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
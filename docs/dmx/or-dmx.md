---
title: 或者 (DMX) |Microsoft 文档
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4a57d0b1c7f1fa75504e786712029326fc958135
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2018
ms.locfileid: "38023845"
---
# <a name="or-dmx"></a>OR (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  一个逻辑运算符，用于对两个数值表达式执行逻辑或运算。  
  
## <a name="syntax"></a>语法  
  
```  
  
Expression1 OR Expression2  
```  
  
#### <a name="parameters"></a>Parameters  
 *Expression1*  
 一个返回数值的有效数据挖掘扩展 (DMX) 表达式。  
  
 *Expression2*  
 一个返回数值的有效 DMX 表达式。  
  
## <a name="return-value"></a>返回值  
 如果任意一个参数或两个参数的计算结果为 TRUE，则返回 TRUE 布尔值；否则将返回 FALSE。  
  
## <a name="remarks"></a>Remarks  
 在运算符执行逻辑或运算之前，两个参数均被视为布尔值（0 为 FALSE；否则为 TRUE）。 如果任何一个参数或两个参数的计算结果均为 TRUE，则该运算符将返回 TRUE。 如果*Expression1*计算结果为 TRUE 并*Expression2*计算结果为 FALSE，运算符将返回 TRUE。  
  
 下表阐释了执行逻辑或运算的方式。  
  
|如果 Expression1 为|如果 Expression2 为|则返回值为|  
|-----------------------|-----------------------|---------------------|  
|TRUE|TRUE|TRUE|  
|TRUE|FALSE|TRUE|  
|FALSE|TRUE|TRUE|  
|FALSE|FALSE|FALSE|  
  
## <a name="see-also"></a>请参阅  
 [数据挖掘扩展插件&#40;DMX&#41;运算符参考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [逻辑运算符&#40;DMX&#41;](../dmx/operators-logical.md)   
 [运算符&#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  

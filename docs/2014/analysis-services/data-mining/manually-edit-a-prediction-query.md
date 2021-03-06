---
title: 手动编辑预测查询 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying prediction queries
- Mining Model Prediction [Analysis Services], modifying prediction queries
- manual prediction query modification [Analysis Services]
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d8b561e7bfd1e791dee90d8076fef68f81d2ca8f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48065532"
---
# <a name="manually-edit-a-prediction-query"></a>手动编辑预测查询
  在使用预测查询生成器设计查询后，可通过在数据挖掘设计器的 **“挖掘模型预测”** 选项卡上切换到“查询文本”视图来修改查询。 屏幕的底部会出现文本编辑器，显示查询生成器创建的查询。  
  
 切换到“查询文本”视图对向查询中添加内容非常有用。 例如，可以添加 WHERE 子句或 ORDER BY 子句。  
  
 使用预测查询生成器中的网格可插入对象和列的名称，并设置单个预测函数的语法，然后切换到手动编辑模式以更改参数值。  
  
> [!NOTE]  
>  如果从“查询文本”视图切换回“设计”视图，则会丢失在“查询文本”视图中所做的任何更改。  
  
### <a name="modify-a-query"></a>修改查询  
  
1.  在 **中数据挖掘设计器的** “挖掘模型预测” [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]选项卡上，单击 **SQL**。  
  
     屏幕底部的网格将替换为包含查询的文本编辑器。 可以在此编辑器中键入对查询的更改。  
  
2.  若要运行查询，请在 **“挖掘模型”** 菜单上选择 **“结果”**，或者单击此按钮切换到查询结果。  
  
    > [!NOTE]  
    >  如果您创建的查询无效，则“结果”窗口将不会显示错误，也不会显示任何结果。 单击 **“设计”** 按钮，或者从 **“挖掘模型”** 菜单中选择 **“设计”** 或 **“查询”** 以解决问题并再次运行查询。  
  
## <a name="see-also"></a>请参阅  
 [数据挖掘查询](data-mining-queries.md)   
 [预测查询生成器&#40;数据挖掘&#41;](../prediction-query-builder-data-mining.md)   
 [第 6 课： 创建和使用预测&#40;数据挖掘基础教程&#41;](../../tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
  

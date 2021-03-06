---
title: 层次结构 (SSAS 表格) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: e3e50e89-f85d-485b-a271-1e0550520212
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2301f57d97c42ef2887824d2acd092e2a78aee7a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2018
ms.locfileid: "48133437"
---
# <a name="hierarchies-ssas-tabular"></a>层次结构（SSAS 表格）
  在表格模型中，层次结构是定义表中两个或更多列之间的关系的元数据。 层次结构可与报表客户端字段列表中的其他列单独出现，使客户端用户可以更方便地在报表中导航和包含数据。  
  
 本主题的内容：  
  
-   [优势](#bkmk_benefits)  
  
-   [定义层次结构](#bkmk_define)  
  
-   [相关任务](#bkmk_related_tasks)  
  
##  <a name="bkmk_benefits"></a> 优势  
 表可以包括几十甚至数百个其名称不寻常并且没有明显顺序的列。 这可能导致报表客户端字段列表显得未排序，从而使用户很难找到报表中的数据和在报表中包含数据。 层次结构可以提供复杂数据结构的简单、直观的视图。  
  
 例如，在日期表中，您可以创建日历层次结构。 日历年用作最顶层的父级，月、周和日作为子级包括（日历年->月->周->日）。 此层次结构显示了从日历年到日的逻辑关系。 然后，客户端用户可以从字段列表中选择“日历年”，以便包含某一数据透视表中的所有级别；或者展开层次结构，并且仅选择要在该数据透视表中包含的特定级别。  
  
 因为层次结构中的每个级别都表示表中的一个列，所以可对其进行重命名。 尽管并非层次结构所独有（任何列都可以在表格模型中重命名），但重命名层次结构级别可使用户更轻松地找到报表中的级别和在报表中包含级别。 重命名一个级别并不重命名该级别引用的列；重命名只是使级别更容易识别。 以我们的“日历年”层次结构为例，在数据视图的日期表中，列 CalendarYear、CalendarMonth、CalendarWeek 和 CalendarDay 已重命名为“日历年”、“月”、“周”和“日”，以使它们更易于识别。 重命名级别还带来另外一个好处，即在报表中提供一致性，因为用户不太可能需要更改列名以使它们在数据透视表、图表等中可读性更强。  
  
 层次结构可包括在透视中。 透视定义某一模型的可查看子集，借此您可以将注意力集中在该模型中的特定业务或特定应用上。 例如，透视可以向用户提供仅由满足其特定报表要求所需的数据项构成的可查看列表（层次结构）。 有关详细信息，请参阅[透视表（SSAS 表格）](perspectives-ssas-tabular.md)。  
  
 层次结构的用途不是为了作为一种安全机制，而是作为一个可为用户提供更好体验的工具。 特定层次结构的所有安全性都从基础模型继承。 层次结构无法让用户访问该用户尚未拥有访问权的模型对象。 必须先解决模型数据库的安全性，然后才能通过层次结构访问模型中的对象。 安全角色可用于保护模型元数据和数据。 有关详细信息，请参阅[角色（SSAS 表格）](roles-ssas-tabular.md)。  
  
##  <a name="bkmk_define"></a> 定义层次结构  
 可以通过在关系图视图中使用模型设计器来创建和管理层次结构。 在数据视图的模型设计器中不支持创建和管理层次结构。 若要在“关系图视图”中查看模型设计器，请单击 **“模型”** 菜单，然后指向 **“模型视图”**，再单击 **“关系图视图”**。  
  
 若要创建某一层次结构，请在要指定为父级别的列上右键单击，然后单击“创建层次结构”。 您可以多选要包含的任何数目的列（在单个表内），或者可在以后通过单击列并将列拖到父级别，将列作为子级别添加。 当选择多个列时，列会基于基数自动按某一顺序放置。 您可以通过单击并将某一列（级别）拖动到其他顺序，或者通过使用上下文菜单中的向上和向下导航控件，更改该顺序。 在将列作为子级别添加时，您可以通过将该列拖放到父级别，使用自动检测。  
  
 一个列可以出现在多个层次结构中。 层次结构中不能包含度量值或 KPI 之类的非列对象。 层次结构可以仅基于来自单个表内的列。 如果多选度量值以及一个或多个列，或者如果从多个表中选择列，则在上下文菜单中将禁用“创建层次结构”命令。 若要从不同表中添加列，请使用 RELATED DAX 函数添加引用来自相关表的列的计算列。 该函数使用以下语法： `=RELATED(TableName[ColumnName])`。 有关详细信息，请参阅 RELATED 函数。  
  
 默认情况下，新的层次结构将命名为 hierarchy1、hierarchy2，依此类推。您应更改层次结构名称以便反映父子关系的特性，使其更易于为用户识别。  
  
 创建层次结构后，可以使用“在 Excel 中分析”功能来测试其效能。 有关详细信息，请参阅[在 Excel 中分析（SSAS 表格）](analyze-in-excel-ssas-tabular.md)。  
  
##  <a name="bkmk_related_tasks"></a> 相关任务  
  
|任务|Description|  
|----------|-----------------|  
|[创建和管理层次结构&#40;SSAS 表格&#41;](hierarchies-ssas-tabular.md)|介绍如何通过在关系图视图中使用模型设计器来创建和管理层次结构。|  
  
## <a name="see-also"></a>请参阅  
 [表格模型设计器&#40;SSAS 表格&#41;](../tabular-model-designer-ssas-tabular.md)   
 [透视&#40;SSAS 表格&#41;](perspectives-ssas-tabular.md)   
 [角色&#40;SSAS 表格&#41;](roles-ssas-tabular.md)  
  
  

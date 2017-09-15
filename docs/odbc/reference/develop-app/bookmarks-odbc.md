---
title: "书签 (ODBC) |Microsoft 文档"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: 1d7cccc5-f847-4321-b240-28570854ee5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 791350c93e2570ad8615e5b378e9979870e02acf
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="bookmarks-odbc"></a>书签 (ODBC)
书签是用于标识数据行的值。 只有驱动程序或数据源才知道书签值的含义。 例如，书签可能与行号一样简单，也可能与磁盘地址一样复杂。 ODBC 中的书签会稍有不同从真实丛书中的书签。 在实际簿中，读取器将书签放置在特定页，然后查找该书签以返回到页。 在 ODBC 中，应用程序为特定行请求书签，存储该书签，并将其传回到游标以返回到该行。 因此，ODBC 中的书签是类似于读取器写下页号，请记住，，然后再次查看页面。  
  
 若要确定的书签的驱动程序的支持，应用程序调用**SQLGetInfo** SQL_BOOKMARK_PERSISTENCE 选项。 此值中的位描述什么操作书签后仍存在，例如书签是否仍然有效后关闭游标。  
  
 本部分包含以下主题。  
  
-   [书签类型](../../../odbc/reference/develop-app/bookmark-types.md)  
  
-   [检索书签](../../../odbc/reference/develop-app/retrieving-bookmarks.md)  
  
-   [按书签滚动](../../../odbc/reference/develop-app/scrolling-by-bookmark.md)  
  
-   [更新、 删除或按书签提取](../../../odbc/reference/develop-app/updating-deleting-or-fetching-by-bookmark.md)  
  
-   [比较的书签](../../../odbc/reference/develop-app/comparing-bookmarks.md)
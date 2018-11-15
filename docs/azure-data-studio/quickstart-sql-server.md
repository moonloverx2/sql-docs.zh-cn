---
title: 快速入门：使用Azure Data Studio连接和查询SQL Server |Microsoft Docs
description: 本快速入门介绍如何使用 Azure Data Studio 来连接到 SQL Server 并运行查询
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 6ad52b466c15ad81515e954cf8fa3fa5a727100f
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356088"
---
# <a name="quickstart-connect-and-query-sql-server-using-includename-sosincludesname-sos-shortmd"></a>快速入门： 使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]连接和查询 SQL Server 
本快速入门显示如何使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]连接到SQL Server，然后使用Transact-SQL（T-SQL）语句创建[!INCLUDE[name-sos](../includes/name-sos-short.md)]教程中使用的*TutorialDB*。

## <a name="prerequisites"></a>必要条件

要完成此快速入门，您需要[!INCLUDE[name-sos](../includes/name-sos-short.md)]并访问SQL Server。

- [安装[!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md)。

如果您无权访问SQL Server，请从以下链接中选择您的平台（确保记住您的SQL登录名和密码！）：
- [Windows - 下载 SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [macOS - 在 Docker 上下载 SQL Server 2017](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)
- [Linux-下载 SQL Server 2017 Developer Edition](https://docs.microsoft.com/sql/linux/sql-server-linux-overview#install) -您只需按照创建和查询数据的步骤进行操作即可。


## <a name="connect-to-a-sql-server"></a>连接到 SQL Server

   
1. 启动**[!INCLUDE[name-sos](../includes/name-sos-short.md)]**。
2. 第一次运行[!INCLUDE[name-sos](../includes/name-sos-short.md)]时，将打开**连接**对话框。如果**连接**对话框未打开，请单击**服务器**页面中的**新的连接**图标：
   
   ![新的连接图标](media/quickstart-sql-server/new-connection-icon.png)

1. 本文使用*SQL 登录名*，但*Windows 身份验证*支持。 按如下所示填写字段：
 
    - **服务器名称：** localhost
    - **身份验证类型：** SQL 登录名  
    - **用户名：** SQL 服务器用户名  
    - **密码：** SQL 服务器的密码  
    - **数据库名称：** 将此字段留空 
    - **服务器组：** \<默认\>  

   ![新连接屏幕](media/quickstart-sql-server/new-connection-screen.png)



## <a name="create-a-database"></a>创建数据库

以下步骤创建名为**TutorialDB**的数据库:

1. 右键单击您的服务器上**localhost**，然后选择**新查询。**
1. 将以下代码片段粘贴到查询窗口： 

   ```sql
   USE master
   GO
   IF NOT EXISTS (
      SELECT name
      FROM sys.databases
      WHERE name = N'TutorialDB'
   )
   CREATE DATABASE [TutorialDB]
   GO

   ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
   GO
   ```
1. 若要执行查询时，请单击**运行**。

在查询完成后，新的**TutorialDB**将出现在数据库列表中。 如果看不到，请右击**数据库**节点，然后选择**刷新**。

## <a name="create-a-table"></a>创建表

查询编辑器仍然连接到master数据库，但我们想在*TutorialDB*数据库中创建一个表。

1. 将连接上下文更改为**TutorialDB**:

   ![更改上下文](media/quickstart-sql-server/change-context.png)



1. 将以下代码段粘贴到查询窗口中，然后单击**运行**：

   > [!NOTE]
   > 您可以将其追加到编辑器中，或者覆盖编辑器中的前一个查询。注意，单击**运行**只执行所选的查询。如果没有选择，单击**运行**执行编辑器中的所有查询。

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT    NOT NULL   PRIMARY KEY, -- primary key column
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```

在查询完成后，新**客户**表将出现在表的列表。 您可能需要右键单击**TutorialDB > 表**节点，然后选择**刷新**。

## <a name="insert-rows"></a>插入行

- 以下代码片段粘贴到查询窗口，然后单击**运行**:

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
   VALUES
      ( 1, N'Orlando', N'Australia', N''),
      ( 2, N'Keith', N'India', N'keith0@adventure-works.com'),
      ( 3, N'Donna', N'Germany', N'donna0@adventure-works.com'),
      ( 4, N'Janet', N'United States', N'janet1@adventure-works.com')
   GO
   ```



## <a name="view-the-data-returned-by-a-query"></a>查看由查询返回的数据
1. 以下代码片段粘贴到查询窗口，然后单击**运行**:

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. 显示查询的结果：

   ![选择结果](media/quickstart-sql-server/select-results.png)


## <a name="next-steps"></a>后续步骤
现在，你已成功连接到 SQL Server 并运行查询，尝试[代码编辑器教程](tutorial-sql-editor.md)。



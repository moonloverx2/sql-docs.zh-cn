---
title: 在 Azure Data Studio 中的 SQL Server 大数据群集上提交 Spark 作业
description: 在 Azure Data Studio 中的 SQL Server 大数据群集上提交 Spark 作业
services: SQL Server 2019 big data cluster spark
ms.service: SQL Server 2019 big data cluster spark
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.custom: ''
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 0787663b0c2eccfed33bf5c2cc681be4f2ef5edc
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050823"
---
# <a name="submit-spark-job-on-sql-server-big-data-clusters-in-azure-data-studio"></a>在 Azure Data Studio 中的 SQL Server 大数据群集上提交 Spark 作业

重要方案之一是能够为 SQL Server 2019 CTP 2.0 提交 Spark 作业。 Spark 作业提交功能，可提交本地 Jar 或上一年度文件与对 SQL Server 2019 大数据群集的引用。 它还可以执行 Jar 或上一年度文件，其中已存在于 HDFS 文件系统中。 

## <a name="prerequisite"></a>先决条件 
安装 SQL Server 用于大数据工具并连接到的大数据群集，然后才能提交 Spark 作业。 有关安装的详细信息，请将链接[部署大数据工具](deploy-big-data-tools.md)。

## <a name="open-spark-job-submission-dialog"></a>打开 Spark 作业提交对话框
有几种方法来打开 Spark 作业提交对话框。 方法包括仪表板中，在对象资源管理器和命令用于处理的上下文菜单。

+ 单击**新的 Spark 作业**在仪表板中打开 Spark 作业提交对话框。

    ![通过单击仪表板提交菜单 ](./media/submit-spark-job/new-spark-job.png)
 
+ 右键单击对象资源管理器中的群集，然后选择**提交 Spark 作业**从上下文菜单。 将打开 Spark 作业提交对话框。  
 
    ![通过右键单击群集提交菜单](./media/submit-spark-job/submit-spark-job.png)

+ 右键单击对象资源管理器中的 Jar/Py 文件并选择**提交 Spark 作业**从上下文菜单。 将打开与 Jar/Py 字段预填充的 Spark 作业提交对话框。 
 
    ![提交菜单上的，通过右键单击文件](./media/submit-spark-job/submit-spark-job-2.png)

+ 使用命令**提交 Spark 作业**从命令面板中通过键入 Ctrl + Shift + P （在 Windows) 和 Cmd + Shift + P （在 Mac)。

    ![提交在 windows 中的菜单命令面板](./media/submit-spark-job/submit-spark-job-3.png)

    ![提交的 mac 中的菜单命令面板](./media/submit-spark-job/submit-spark-job-4.png)
  
 
## <a name="submit-spark-job"></a>提交 Spark 作业 
Spark 作业提交对话框将显示如下所示。 输入作业名称、 JAR/Py 文件路径、 主类和其他字段。 该 jar 文件 / Py 文件源可以是从本地或从 HDFS。 如果的 Spark 作业引用的 Jar，Py 文件或其他文件，请单击**高级**选项卡并输入相应的文件路径。 单击**提交**提交 Spark 作业。
 
![新建的 spark 作业对话框](./media/submit-spark-job/submit-spark-job-section.png)

![高级的对话框](./media/submit-spark-job/submit-spark-job-section-1.png)

## <a name="monitor-spark-job-submission"></a>监视提交 Spark 作业
提交 Spark 作业后，Spark 作业提交和执行状态信息显示在左侧任务历史记录。 和的进度和日志的详细信息也会显示在**输出**底部窗口。
+ Spark 作业正在进行中时**任务历史记录**面板和**输出**窗口是刷新进度。

![监视正在进行中的 spark 作业](./media/submit-spark-job/monitor-spark-job-submission.png)

+ Spark 作业时成功完成，可以看到 Spark UI 和 Yarn UI 中的链接**输出**窗口。 可以单击链接的详细信息。

![在输出中的 Spark 作业链接](./media/submit-spark-job/monitor-spark-job-submission-2.png)

## <a name="next-steps"></a>后续步骤
SQL Server 大数据群集和相关的方案的详细信息，请参阅[什么是 SQL Server 大数据群集](big-data-cluster-overview.md)？


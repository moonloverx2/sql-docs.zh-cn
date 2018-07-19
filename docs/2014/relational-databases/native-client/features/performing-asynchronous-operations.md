---
title: 执行异步操作 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- initialization [SQL Server Native Client]
- database connections [SQL Server Native Client]
- data access [SQL Server Native Client], asynchronous operations
- connections [SQL Server Native Client]
- asynchronous operations [SQL Server Native Client]
- rowsets [SQL Server], initializing
- SQLNCLI, asynchronous operations
- SQL Server Native Client, asynchronous operations
ms.assetid: 8fbd84b4-69cb-4708-9f0f-bbdf69029bcc
caps.latest.revision: 45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 84d46265f1d057c805c4ad4dcb9463dc319c12a2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2018
ms.locfileid: "37407767"
---
# <a name="performing-asynchronous-operations"></a>执行异步操作
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 允许应用程序执行异步数据库操作。 异步处理将使方法能够立即返回，而不会阻塞调用线程。 这使得多线程机制能提供更强大的功能和灵活性，而不需要开发人员显式创建线程或处理同步。 应用程序将在初始化数据库连接时或初始化由执行命令所生成的结果时请求异步处理。  
  
## <a name="opening-and-closing-a-database-connection"></a>打开和关闭数据库连接  
 使用时[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序，用于以异步方式初始化数据源对象的应用程序可以设置 DBPROP_INIT_ASYNCH 属性，然后调用中的 DBPROPVAL_ASYNCH_INITIALIZE 位**Idbinitialize:: Initialize**。 提供程序立即时设置此属性，返回通过调用**初始化**如果立即完成该操作，则为 S_OK 或 DB_S_ASYNCHRONOUS，如果初始化正在以异步方式继续。 应用程序可以查询**IDBAsynchStatus**或[ISSAsynchStatus](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)接口的数据源对象，然后再调用**IDBAsynchStatus::GetStatus**或[Issasynchstatus:: Waitforasynchcompletion](../../native-client-ole-db-interfaces/issasynchstatus-waitforasynchcompletion-ole-db.md)若要获取的初始化状态。  
  
 此外，SSPROP_ISSAsynchStatus 属性已添加到 DBPROPSET_SQLSERVERROWSET 属性集。 支持的提供程序**ISSAsynchStatus**接口必须实现此属性与值为 VARIANT_TRUE。  
  
 **Idbasynchstatus:: Abort**或[issasynchstatus:: Abort](../../native-client-ole-db-interfaces/issasynchstatus-abort-ole-db.md)可以调用以进行取消异步**初始化**调用。 使用者必须显式请求异步数据源初始化。 否则为**idbinitialize:: Initialize**完全初始化的数据源对象才会返回。  
  
> [!NOTE]  
>  用于连接池的数据源对象不能调用**ISSAsynchStatus**接口中[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序。 **ISSAsynchStatus**没有共用的数据源对象公开的接口。  
>   
>  如果应用程序显式强制使用游标引擎**iopenrowset:: Openrowset**并**imultipleresults:: Getresult**将不支持异步处理。  
>   
>  此外，远程处理代理/存根 dll （在 MDAC 2.8) 不能调用**ISSAsynchStatus**接口中[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]本机客户端。 **ISSAsynchStatus**没有通过远程处理公开的接口。  
>   
>  服务组件不支持**ISSAsynchStatus**。  
  
## <a name="execution-and-rowset-initialization"></a>执行和行集初始化  
 被设计成以异步方式打开由执行命令所生成的结果的应用程序可以设置 DBPROP_ROWSET_ASYNCH 属性中的 DBPROPVAL_ASYNCH_INITIALIZE 位。 当调用之前设置该位**idbinitialize:: Initialize**， **icommand:: Execute**， **iopenrowset:: Openrowset**或**IMultipleResults::GetResult**，则*riid*参数必须设置为 IID_IDBAsynchStatus、 IID_ISSAsynchStatus 或 IID_IUnknown。  
  
 该方法将立即返回 S_OK 如果行集初始化完成立即或 DB_S_ASYNCHRONOUS，如果行集将继续以异步方式初始化与*ppRowset*上设置为所请求的接口行集。 有关[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供程序，此接口只能**IDBAsynchStatus**或**ISSAsynchStatus**。 直到完全初始化行集，该接口的行为如同在挂起的状态，并调用**QueryInterface**以外的接口**IID_IDBAsynchStatus**或**IID_ISSAsynchStatus**可能返回 E_NOINTERFACE。 除非使用者显式请求异步处理，否则行集将以同步方式执行初始化。 所有请求时，接口将用**idbasynchstaus:: Getstatus**或**issasynchstatus:: Waitforasynchcompletion**返回的异步操作已完成。 这不一定意味着行集已完全填充，但它是完整的，且功能齐全。  
  
 如果执行的命令不返回行集，它仍会立即返回支持的对象**IDBAsynchStatus**。  
  
 如果需要获得由异步命令执行所产生的多个结果，则应当：  
  
-   在执行命令之前，设置 DBPROP_ROWSET_ASYNCH 属性的 DBPROPVAL_ASYNCH_INITIALIZE 位。  
  
-   调用**icommand:: Execute**，并请求**IMultipleResults**。  
  
 **IDBAsynchStatus**并**ISSAsynchStatus**然后可以通过查询多个结果接口使用获取接口**QueryInterface**。  
  
 该命令完成后执行时， **IMultipleResults**可用作正常，并且从同步的情况下的一个例外： 可能返回 DB_S_ASYNCHRONOUS，在这种情况下**IDBAsynchStatus**或**ISSAsynchStatus**可用于确定何时完成该操作。  
  
## <a name="examples"></a>示例  
 在以下示例中，应用程序调用非阻止方法，执行一些其他处理，然后返回以处理结果。 **Issasynchstatus:: Waitforasynchcompletion**等待内部事件对象直到异步执行的操作完成或指定的时间量*dwMilisecTimeOut*传递。  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
  
DBPROPSET CmdPropset[1];  
DBPROP CmdProperties[1];  
  
CmdPropset[0].rgProperties = CmdProperties;  
CmdPropset[0].cProperties = 1;  
CmdPropset[0].guidPropertySet = DBPROPSET_ROWSET;  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
CmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
  
hr = pICommandProps->SetProperties(1, CmdPropset);  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if ( hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 **Issasynchstatus:: Waitforasynchcompletion**等待内部事件对象以异步方式执行的操作完成或*dwMilisecTimeOut*传递值。  
  
 以下示例显示有多个结果集的异步处理：  
  
```  
DBPROP CmdProperties[1];  
  
// Set asynch mode for command.  
CmdProperties[0].dwPropertyID = DBPROP_ROWSET_ASYNCH;  
CmdProperties[0].vValue.vt = VT_I4;  
CmdProperties[0].vValue.lVal = DBPROPVAL_ASYNCH_INITIALIZE;  
  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_IMultipleResults,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pIMultipleResults);  
  
// Use GetResults for ISSAsynchStatus.  
hr = pIMultipleResults->GetResult(IID_ISSAsynchStatus, (void **) &pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work here...  
  
   hr = pISSAsynchStatus->WaitForAsynchCompletion(dwMilisecTimeOut);  
   if (hr == S_OK)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
      pISSAsynchStatus->Release();  
   }  
}  
```  
  
 若要阻止阻塞，客户端可以检查异步操作的运行状态，如以下示例所示：  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);   
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   do{  
      // Do some work...  
      hr = pISSAsynchStatus->GetStatus(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN, NULL, NULL, &ulAsynchPhase, NULL);  
   }while (DBASYNCHPHASE_COMPLETE != ulAsynchPhase)  
   if SUCCEEDED(hr)  
   {  
      hr = pISSAsynchStatus->QueryInterface(IID_IRowset, (void**)&pRowset);  
   }  
   pIDBAsynchStatus->Release();  
}  
```  
  
 以下示例演示如何才能取消当前正在运行的异步操作：  
  
```  
// Set the DBPROPVAL_ASYNCH_INITIALIZE bit in the   
// DBPROP_ROWSET_ASYNCH property before calling Execute().  
hr = pICommand->Execute(  
   pUnkOuter,  
   IID_ISSAsynchStatus,  
   pParams,  
   pcRowsAffected,  
   (IUnknown**)&pISSAsynchStatus);  
  
if (hr == DB_S_ASYNCHRONOUS)  
{  
   // Do some work...  
   hr = pISSAsynchStatus->Abort(DB_NULL_HCHAPTER, DBASYNCHOP_OPEN);  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [SQL Server Native Client 功能](sql-server-native-client-features.md)   
 [行集属性和行为](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)   
 [ISSAsynchStatus &#40;OLE DB&#41;](../../native-client-ole-db-interfaces/issasynchstatus-ole-db.md)  
  
  
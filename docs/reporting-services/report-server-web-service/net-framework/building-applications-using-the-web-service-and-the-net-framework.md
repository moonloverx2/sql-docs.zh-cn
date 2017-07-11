---
title: "使用 Web 服务和.NET Framework 构建应用程序 |Microsoft 文档"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Report Server Web service, application building
- .NET Framework [Reporting Services]
- XML Web service [Reporting Services], client creation
- reports [Reporting Services], building
- Web service [Reporting Services], application building
- Report Server Web service, client creation
- client configuration [Reporting Services]
- XML Web service [Reporting Services], application building
- Web service [Reporting Services], client creation
ms.assetid: 92a9678c-bc4f-4d7a-ba44-85989bfe27ca
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 58588838e0e74b545290df5ff0e77dc68ad5e918
ms.contentlocale: zh-cn
ms.lasthandoff: 06/13/2017

---
# <a name="building-applications-using-the-web-service-and-the-net-framework"></a>Building Applications Using the Web Service and the .NET Framework
  与[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]，可以使用熟悉的编程构造，如方法，基元类型，并且要使用 Web 服务的用户定义的复杂类型。 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 包含可用来创建 Web 服务客户端的基础结构和工具，这些客户端可以调用任何符合万维网联盟 (W3C) 标准的 Web 服务。  
  
 报表服务器 Web 服务客户端是使用简单对象访问协议 (SOAP) 消息与报表服务器通信的任何组件或应用程序。  
  
 **若要创建使用.NET Framework 的报表服务器 Web 服务客户端，请执行以下基本步骤：**  
  
1.  创建 Web 服务的代理类。  
  
     为此，将代理类或 Web 引用添加到开发项目中，在客户端代码中引用代理类，并创建该代理的实例。 有关详细信息，请参阅[创建 Web 服务代理](../../../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md)。  
  
2.  针对报表服务器对 Web 服务客户端进行身份验证。  
  
     为此，将服务对象的 <xref:System.Web.Services.Protocols.WebClientProtocol.Credentials%2A> 属性设置为与报表服务器上经过身份验证的用户的凭据相同。 有关详细信息，请参阅[Web 服务身份验证](../../../reporting-services/report-server-web-service/net-framework/web-service-authentication.md)。  
  
3.  调用与您要调用的 Web 服务操作相对应的代理类的方法。  
  
     为此，调用 Web 服务方法并提供必需的参数。 有关 Web 服务方法的详细信息，请参阅[报表服务器 Web 服务方法](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)。 有关调用的详细信息，请参阅[调用 Web 服务方法](../../../reporting-services/report-server-web-service/net-framework/calling-web-service-methods.md)。  
  
## <a name="in-this-section"></a>本节内容  
  
|主题|Description|  
|-----------|-----------------|  
|[创建 Web 服务代理](../../../reporting-services/report-server-web-service/net-framework/creating-the-web-service-proxy.md)|描述如何将代理类添加到你的项目使用[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]。|  
|[Web 服务身份验证](../../../reporting-services/report-server-web-service/net-framework/web-service-authentication.md)|介绍如何对针对报表服务器 Web 服务的调用进行身份验证。|  
|[调用 Web 服务方法](../../../reporting-services/report-server-web-service/net-framework/calling-web-service-methods.md)|描述如何使用 SOAP API 调用中的 Web 服务方法[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]。|  
|[设置 Web 服务的 Url 属性](../../../reporting-services/report-server-web-service/net-framework/setting-the-url-property-of-the-web-service.md)|说明在创建 Web 引用之后，如何以编程方式将 Web 服务代理定向到新的服务器 URL。|  
|[提供 Web 服务方法自变量](../../../reporting-services/report-server-web-service/net-framework/supplying-web-service-method-arguments.md)|介绍如何调用 Web 服务方法并提供方法参数。|  
|[省略可选的 Web 服务对象的值](../../../reporting-services/report-server-web-service/net-framework/omitting-values-for-optional-web-service-objects.md)|介绍如何忽略可选 Web 服务对象的值。|  
|[使用安全的 Web 服务方法](../../../reporting-services/report-server-web-service/net-framework/using-secure-web-service-methods.md)|描述**SecureConnectionLevel**设置以及在其中会影响的 Reporting Services SOAP API 使用的方式。|  
|[将设备信息设置传递给呈现扩展插件](../../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)|介绍用于将报表呈现为不同格式的设备信息设置。|  
|[Reporting Services 传递扩展插件设置](../../../reporting-services/report-server-web-service/net-framework/reporting-services-delivery-extension-settings.md)|介绍用于通过报表服务器电子邮件传递报表的设置。|  
|[使用 Reporting Services SOAP 标头](../../../reporting-services/report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)|说明如何在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中使用 SOAP 标头。|  
|[引入了 Reporting Services 中的异常处理](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)|提供有关 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 处理错误时所用方法的信息。|  
  
## <a name="see-also"></a>另请参阅  
 [报表服务器 Web 服务](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [技术参考 &#40;SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
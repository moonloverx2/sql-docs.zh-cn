---
title: '记录 （Visual c + + 语法索引与 #import） |Microsoft 文档'
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
dev_langs:
- C++
helpviewer_keywords:
- 'Record collection [ADO], Visual C++ syntax index with #import'
ms.assetid: ba6dd186-9552-4b6c-960b-3ee6cd589afd
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a7673415aa274f8443ba0198f9dab22864356d2d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="record-visual-c-syntax-index-with-import"></a>记录 （Visual c + + 语法索引与 #import）
## <a name="methods"></a>方法  
  
```  
HRESULT Cancel( );  
  
HRESULT Close( );  
  
_bstr_t CopyRecord( _bstr_t Source, _bstr_t Destination,  
    _bstr_t     UserName, _bstr_t Password, enum CopyRecordOptionsEnum  
    Options,     VARIANT_BOOL Async );  
  
HRESULT DeleteRecord( _bstr_t Source, VARIANT_BOOL Async );  
  
_RecordsetPtr GetChildren( );  
  
_bstr_t MoveRecord( _bstr_t Source, _bstr_t Destination,  
    _bstr_t     UserName, _bstr_t Password, enum MoveRecordOptionsEnum  
    Options,     VARIANT_BOOL Async );  
  
HRESULT Open( const _variant_t & Source, const _variant_t  
&     ActiveConnection, enum ConnectModeEnum Mode, enum  
    RecordCreateOptionsEnum CreateOptions, enum RecordOpenOptionsEnum  
    Options, _bstr_t UserName, _bstr_t Password );  
```  
  
## <a name="properties"></a>属性  
  
```  
_variant_t GetActiveConnection( );  
void PutActiveConnection( _bstr_t pvar );  
void PutRefActiveConnection( struct _Connection * pvar );  
  
FieldsPtr GetFields( );  
__declspec(property(get=GetFields)) FieldsPtr Fields;  
  
enum ConnectModeEnum GetMode( );  
void PutMode( enum ConnectModeEnum pMode );  
__declspec(property(get=GetMode,put=PutMode)) enum ConnectModeEnum Mode;  
  
_bstr_t GetParentURL( );  
__declspec(property(get=GetParentURL)) _bstr_t ParentURL;  
  
enum RecordTypeEnum GetRecordType( );  
__declspec(property(get=GetRecordType)) enum RecordTypeEnum  
    RecordType;  
  
_variant_t GetSource( );  
void PutSource( _bstr_t pvar );  
void PutRefSource( IDispatch * pvar );  
  
enum ObjectStateEnum GetState( );  
__declspec(property(get=GetState)) enum ObjectStateEnum State;  
```  
  
## <a name="see-also"></a>另请参阅  
 [记录对象 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
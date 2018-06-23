---
title: OLE DB テーブル値パラメーターの型のサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4b6416715cc6226766773d3f1d630dc2e42e1e37
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163841"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>OLE DB テーブル値パラメーターの型のサポート
  このトピックでは、テーブル値パラメーターに対する OLE DB 型のサポートについて説明します。  
  
## <a name="table-valued-parameter-rowset-object"></a>テーブル値パラメーターの行セット オブジェクト  
 テーブル値パラメーターの特殊な行セット オブジェクトを作成できます。 ITableDefinitionWithConstraints::CreateTableWithConstraints または iopenrowset::openrowset を使用して、テーブル値パラメーター行セット オブジェクトを作成します。 これを行うには、設定、 *eKind*のメンバー、 *pTableID*パラメーターに dbkind_guid_name を設定し、clsid_rowset_inmemory として、 *guid*メンバー。 テーブル値パラメーターのサーバーの種類名を指定する必要があります、 *pwszName*のメンバー *pTableID* iopenrowset::openrowset を使用する場合。 テーブル値パラメーターの行セット オブジェクトは、標準の SQL Server Native Client OLE DB プロバイダー オブジェクトと同様に動作します。  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtypetable"></a>DBTYPE_TABLE  
 新しい型 DBTYPE_TABLE はテーブル型を表します。 この型は、DBTYPE を必要とするさまざまな OLE DB インターフェイスのテーブル値パラメーターを示します。  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 DBTYPE_TABLE の形式は、DBTYPE_IUNKNOWN と同じです。 これは、データ バッファー内のオブジェクトへのポインターです。 バインドで完全な仕様にコンシューマー、DBOBJECT バッファーでいっぱい*iid*行セット オブジェクト インターフェイス (IID_IRowset) のいずれかに設定します。 DBOBJECT がバインドで指定されていない、IID_IRowset が想定されます。  
  
 DBTYPE_TABLE とその他の型との間の変換はサポートされません。 IConvertType::CanConvert はへの変換 DBTYPE_TABLE 以外の要求の変換でサポートされていない S_FALSE を返します。 Command オブジェクトの DBCONVERTFLAGS_PARAMETER を想定しています。  
  
## <a name="methods"></a>メソッド  
 テーブル値パラメーターをサポートする OLE DB メソッドについては、次を参照してください。 [OLE DB Table-Valued パラメーター型をサポート&#40;メソッド&#41;](ole-db-table-valued-parameter-type-support-methods.md)です。  
  
## <a name="properties"></a>[プロパティ]  
 詳細についてはテーブル値パラメーターをサポートする OLE DB プロパティ、次を参照してください。 [OLE DB Table-Valued パラメーター型をサポート&#40;プロパティ&#41;](ole-db-table-valued-parameter-type-support-properties.md)です。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターを使用して&#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
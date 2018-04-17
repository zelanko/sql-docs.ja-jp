---
title: OLE DB テーブル値パラメーターの型のサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8ca6098b630ba9c8b2550f1caf6d4804f6b73d0f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ole-db-table-valued-parameter-type-support"></a>OLE DB テーブル値パラメーターの型のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

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
 テーブル値パラメーターをサポートする OLE DB メソッドについては、次を参照してください。 [OLE DB Table-Valued パラメーター型をサポート&#40;メソッド&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)です。  
  
## <a name="properties"></a>プロパティ  
 詳細についてはテーブル値パラメーターをサポートする OLE DB プロパティ、次を参照してください。 [OLE DB Table-Valued パラメーター型をサポート&#40;プロパティ&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)です。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用してテーブル値パラメーター (&) #40 です。 OLE DB (&) #41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

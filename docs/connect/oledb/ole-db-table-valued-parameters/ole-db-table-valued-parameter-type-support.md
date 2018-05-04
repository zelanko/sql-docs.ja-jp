---
title: OLE DB テーブル値パラメーターの型のサポート |Microsoft ドキュメント
description: OLE DB Table-Valued パラメーター型のサポート
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: eae201b0adc19f08034893cb4a54a47371f9485f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-table-valued-parameter-type-support"></a>OLE DB テーブル値パラメーターの型のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  この記事では、テーブル値パラメーターに対する OLE DB 型のサポートについて説明します。  
  
## <a name="table-valued-parameter-rowset-object"></a>テーブル値パラメーターの行セット オブジェクト  
 テーブル値パラメーターの特殊な行セット オブジェクトを作成できます。 ITableDefinitionWithConstraints::CreateTableWithConstraints または iopenrowset::openrowset を使用して、テーブル値パラメーター行セット オブジェクトを作成します。 これを行うには、設定、 *eKind*のメンバー、 *pTableID*パラメーターに dbkind_guid_name を設定し、clsid_rowset_inmemory として、 *guid*メンバー。 テーブル値パラメーターのサーバーの種類名を指定する必要があります、 *pwszName*のメンバー *pTableID* iopenrowset::openrowset を使用する場合。 テーブル値パラメーター行セット オブジェクトは、正規 OLE DB Driver for SQL Server オブジェクトと同様に動作します。  
  
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
  
 その他の型と DBTYPE_TABLE からの変換はサポートされません。 IConvertType::CanConvert はへの変換 DBTYPE_TABLE 以外の要求の変換でサポートされていない S_FALSE を返します。 Command オブジェクトの DBCONVERTFLAGS_PARAMETER を想定しています。  
  
## <a name="methods"></a>メソッド  
 テーブル値パラメーターをサポートする OLE DB メソッドについては、次を参照してください。 [OLE DB Table-Valued パラメーター型をサポート&#40;メソッド&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)です。  
  
## <a name="properties"></a>プロパティ  
 テーブル値パラメーターをサポートする OLE DB プロパティについては、次を参照してください。 [OLE DB Table-Valued パラメーター型をサポート&#40;プロパティ&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)です。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用してテーブル値パラメーター (&) #40 です。 OLE DB (&) #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

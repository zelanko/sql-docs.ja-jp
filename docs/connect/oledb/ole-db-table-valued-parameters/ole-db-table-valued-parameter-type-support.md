---
title: OLE DB テーブル値パラメーターの型のサポート | Microsoft Docs
description: OLE DB テーブル値パラメーターの型のサポート
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 6491e8b81efbd70a69fdd7a7e7541b4262ede7dd
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2018
ms.locfileid: "39106988"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>OLE DB テーブル値パラメーターの型のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  この記事では、テーブル値パラメーターに対する OLE DB 型のサポートについて説明します。  
  
## <a name="table-valued-parameter-rowset-object"></a>テーブル値パラメーターの行セット オブジェクト  
 テーブル値パラメーターの特殊な行セット オブジェクトを作成できます。 ITableDefinitionWithConstraints::CreateTableWithConstraints または iopenrowset::openrowset を使用して、テーブル値パラメーター行セット オブジェクトを作成します。 そのためには、*pTableID* パラメーターの *eKind* メンバーに DBKIND_GUID_NAME を設定し、CLSID_ROWSET_INMEMORY を *guid* メンバーとして指定します。 テーブル値パラメーターのサーバーの型名を指定する必要があります、 *pwszName*のメンバー *pTableID* iopenrowset::openrowset を使用する場合。 テーブル値パラメーター行セット オブジェクトは、標準 OLE DB Driver for SQL Server オブジェクトのように動作します。  
  
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
  
 DBTYPE_TABLE の形式は、DBTYPE_IUNKNOWN と同じです。 これは、データ バッファー内のオブジェクトへのポインターです。 バインドでの完全な指定のため、コンシューマーは、行セット オブジェクト インターフェイス (IID_IRowset) の 1 つに *iid* を設定して、DBOBJECT バッファーをいっぱいにします。 DBOBJECT がバインドで指定されない場合は、IID_IRowset が想定されます。  
  
 DBTYPE_TABLE とその他の型との間の変換はサポートされません。 IConvertType::CanConvert は、DBTYPE_TABLE から DBTYPE_TABLE への変換以外の要求に対するサポートされない変換について、S_FALSE を返します。 これは、Command オブジェクトの DBCONVERTFLAGS_PARAMETER を想定します。  
  
## <a name="methods"></a>メソッド  
 テーブル値パラメーターをサポートする OLE DB メソッドについては、次を参照してください。 [OLE DB Table-Valued パラメーター型のサポート&#40;メソッド&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)します。  
  
## <a name="properties"></a>[プロパティ]  
 テーブル値パラメーターをサポートする OLE DB プロパティについては、次を参照してください。 [OLE DB Table-Valued パラメーター型のサポート&#40;プロパティ&#41;](../../oledb/ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)します。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターの使用 &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  

---
title: スキーマ行セットでの分散クエリのサポート | Microsoft Docs
description: スキーマ行セットでの分散クエリのサポート
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_SQLSERVERSESSION property
- schema rowsets [OLE DB]
- distributed queries [SQL Server], OLE DB Driver for SQL Server
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- rowsets [OLE DB], schema
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 139186d64d2b7df6aca883a253e1f9fe3f062214
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67993886"
---
# <a name="schema-rowsets---distributed-query-support"></a>スキーマ行セット - 分散クエリのサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]IDBSchemaRowset **インターフェイスは、** 分散クエリをサポートするため、リンク サーバー上のメタデータを返します。  
  
 DBPROPSET_SQLSERVERSESSION の SSPROP_QUOTEDCATALOGNAMES プロパティが VARIANT_TRUE の場合、カタログ名には引用符で囲んだ識別子 ("my.catalog" など) を指定できます。 OLE DB Driver for SQL Server では、スキーマ行セットの出力をカタログで制限するときに、リンク サーバーとカタログ名を含む 2 部構成の名前が認識されます。 次の表のスキーマ行セットでは、2 部構成のカタログ名を _linked\_server_ **.** _catalog_ の形式で指定することで、名前の付いたリンク サーバーの適切なカタログに出力が制限されます。  
  
|スキーマ行セット|カタログの制限|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMNS|TABLE_CATALOG|  
|DBSCHEMA_PRIMARY_KEYS|TABLE_CATALOG|  
|DBSCHEMA_TABLES|TABLE_CATALOG|  
|DBSCHEMA_FOREIGN_KEYS|PK_TABLE_CATALOG FK_TABLE_CATALOG|  
|DBSCHEMA_INDEXES|TABLE_CATALOG|  
|DBSCHEMA_COLUMN_PRIVILEGES|TABLE_CATALOG|  
|DBSCHEMA_TABLE_PRIVILEGES|TABLE_CATALOG|  
  
> [!NOTE]  
>  スキーマ行セットをリンク サーバーのすべてのカタログに制限するには、*linked_server* 構文を使用します (アンダースコアを区切り文字として名前を指定します)。 この構文は、カタログ名の制限で NULL を指定する場合と同じで、カタログをサポートしないデータ ソースをリンク サーバーが示している場合にも使用されます。  
 
 OLE DB Driver for SQL Server は、LINKEDSERVERS スキーマ行セットを定義し、リンク サーバーとして登録された OLE DB データ ソースの一覧を返します。  
  
## <a name="see-also"></a>参照  
 [スキーマ行セットのサポート &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowset-support-ole-db.md)   
 [LINKEDSERVERS 行セット &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
  

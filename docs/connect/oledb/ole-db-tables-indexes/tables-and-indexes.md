---
title: テーブルとパーティション インデックス |Microsoft Docs
description: 作成、変更、および落としたりのテーブルとパーティション インデックスの SQL Server 用の OLE DB ドライバーの使用
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- OLE DB Driver for SQL Server, tables
- OLE DB Driver for SQL Server, indexes
- indexes [OLE DB]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 73b79c036f528a1ce507f76a617ad1ee1d823f96
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032114"
---
# <a name="tables-and-indexes"></a>テーブルとインデックス
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server では、**IIndexDefinition** インターフェイスと **ITableDefinition** インターフェイスが公開されます。コンシューマーは、これらのインターフェイスにより [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のテーブルとインデックスを作成、変更、および削除できます。 有効なテーブルやインデックスの定義は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のバージョンによって異なります。  
  
 テーブルやインデックスを作成または削除できるかどうかは、コンシューマー アプリケーション ユーザーの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アクセス権によって決まります。 テーブルの削除は、宣言参照整合性制約やその他の要因の指定によってさらに制約できます。  
  
 対象とするほとんどのアプリケーション[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インターフェイスの SQL Server のこの OLE DB ドライバーではなく、SQL-DMO を使用します。 SQL-DMO は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のすべての管理機能をサポートする OLE オートメーション オブジェクトの集まりです。 複数の OLE DB プロバイダーを対象とするアプリケーションでは、さまざまな OLE DB プロバイダーでサポートされる、これらの汎用 OLE DB インターフェイスを使用します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、プロバイダー固有の DBPROPSET_SQLSERVERCOLUMN プロパティ セットで、次のプロパティを定義しています。  
  
|プロパティ ID|[説明]|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|型 : VT_BSTR<br /><br /> R/W: 書き込み<br /><br /> 既定値 : NULL<br /><br /> 説明 : このプロパティは、**ITableDefinition** でのみ使用します。 このプロパティに指定した文字列は、[CREATE TABLE](../../../t-sql/statements/create-table-transact-sql.md) ステートメントの作成時に<br /><br /> ステートメントの使用などがあります。|  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Server テーブルの作成](../../oledb/ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [SQL Server テーブルへの列の追加](../../oledb/ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [SQL Server テーブルからの列の削除](../../oledb/ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [SQL Server テーブルの削除](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [SQL Server インデックスの作成](../../oledb/ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [SQL Server インデックスの削除](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server のプログラミング](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  

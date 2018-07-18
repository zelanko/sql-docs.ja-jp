---
title: テーブルとパーティション インデックス |Microsoft ドキュメント
description: 作成、変更、および落としたりのテーブルとパーティション インデックスの SQL Server の OLE DB Driver を使用します。
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
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 962efa70c583bdb9aa9537826800c1c166350dc4
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689345"
---
# <a name="tables-and-indexes"></a>テーブルとインデックス
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server を公開、 **IIndexDefinition**と**ITableDefinition**インターフェイス、コンシューマーを作成するには、変更、および削除[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブルとインデックス。 有効なテーブルやインデックスの定義は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のバージョンによって異なります。  
  
 テーブルやインデックスを作成または削除できるかどうかは、コンシューマー アプリケーション ユーザーの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アクセス権によって決まります。 テーブルの削除は、宣言参照整合性制約やその他の要因の指定によってさらに制約できます。  
  
 対象とするほとんどのアプリケーション[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インターフェイスを SQL Server のこの OLE DB Driver ではなく、SQL-DMO を使用します。 SQL-DMO は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のすべての管理機能をサポートする OLE オートメーション オブジェクトの集まりです。 複数の OLE DB プロバイダーを対象とするアプリケーションでは、さまざまな OLE DB プロバイダーでサポートされる、これらの汎用 OLE DB インターフェイスを使用します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、プロバイダー固有の DBPROPSET_SQLSERVERCOLUMN プロパティ セットで、次のプロパティを定義しています。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|型 : VT_BSTR<br /><br /> R/W: 書き込み<br /><br /> 既定値 : NULL<br /><br /> 説明: このプロパティでのみ使用が**ITableDefinition**です。 作成するときに、このプロパティで指定した文字列が使用される、[テーブルの作成](../../../t-sql/statements/create-table-transact-sql.md)<br /><br /> ステートメントの使用などがあります。|  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Server テーブルの作成](../../oledb/ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [SQL Server テーブルへの列の追加](../../oledb/ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [SQL Server テーブルからの列の削除](../../oledb/ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [SQL Server テーブルの削除](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [SQL Server インデックスの作成](../../oledb/ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [SQL Server インデックスの削除](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server プログラミング用の OLE DB ドライバー](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [DROP TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  

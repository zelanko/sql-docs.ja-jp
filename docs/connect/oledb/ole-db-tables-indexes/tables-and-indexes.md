---
title: テーブルとパーティション インデックス |Microsoft ドキュメント
description: 作成、変更、および落としたりのテーブルとパーティション インデックスの SQL Server の OLE DB Driver を使用します。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
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
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 821355c800f2b162665b29cfcadd7d9b776a1fc6
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="tables-and-indexes"></a>テーブルとインデックス
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server を公開、 **IIndexDefinition**と**ITableDefinition**インターフェイス、コンシューマーを作成するには、変更、および削除[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブルとインデックス。 有効なテーブルやインデックスの定義は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のバージョンによって異なります。  
  
 テーブルやインデックスを作成または削除できるかどうかは、コンシューマー アプリケーション ユーザーの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アクセス権によって決まります。 テーブルの削除は、宣言参照整合性制約やその他の要因の指定によってさらに制約できます。  
  
 対象とするほとんどのアプリケーション[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インターフェイスを SQL Server のこの OLE DB Driver ではなく、SQL-DMO を使用します。 SQL-DMO は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のすべての管理機能をサポートする OLE オートメーション オブジェクトの集まりです。 複数の OLE DB プロバイダーを対象とするアプリケーションでは、さまざまな OLE DB プロバイダーでサポートされる、これらの汎用 OLE DB インターフェイスを使用します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、プロバイダー固有の DBPROPSET_SQLSERVERCOLUMN プロパティ セットで、次のプロパティを定義しています。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|型 : VT_BSTR<br /><br /> R/W: 書き込み<br /><br /> 既定値 : NULL<br /><br /> 説明: このプロパティでのみ使用が**ITableDefinition**です。 作成するときに、このプロパティで指定した文字列が使用される、[テーブルの作成](../../../t-sql/statements/create-table-transact-sql.md)<br /><br /> ステートメントの使用などがあります。|  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Server テーブルを作成します。](../../oledb/ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [SQL Server テーブルに列を追加します。](../../oledb/ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [SQL Server テーブルから列を削除します。](../../oledb/ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [SQL Server テーブルを削除します。](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [SQL Server インデックスの作成](../../oledb/ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [SQL Server インデックスの削除](../../oledb/ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server &#40;OLE DB&#41;](../../oledb/ole-db/oledb-driver-for-sql-server-ole-db.md)   
 [DROP TABLE &#40;です。TRANSACT-SQL と #41 です。](../../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../../t-sql/statements/drop-index-transact-sql.md)  
  
  

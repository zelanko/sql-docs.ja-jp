---
title: "テーブルとパーティション インデックス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-tables-indexes
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- OLE DB, indexes
- OLE DB, tables
- ITableDefinition interface
- tables [OLE DB]
- IIndexDefinition interface
- SQL Server Native Client OLE DB provider, tables
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: 4217c6d8-8cd2-43dc-b36f-3cfd8a58fabc
caps.latest.revision: "30"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4b3f75c984e448bc82a33eb3a857e693ce7dba46
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="tables-and-indexes"></a>テーブルとインデックス
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを公開、 **IIndexDefinition**と**ITableDefinition**インターフェイス、コンシューマーを作成するには、変更、および削除[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルとインデックス。 有効なテーブルやインデックスの定義は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンによって異なります。  
  
 テーブルやインデックスを作成または削除できるかどうかは、コンシューマー アプリケーション ユーザーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] アクセス権によって決まります。 テーブルの削除は、宣言参照整合性制約やその他の要因の指定によってさらに制約できます。  
  
 対象とするほとんどのアプリケーション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]これらではなく、SQL-DMO を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーのインターフェイスです。 SQL-DMO は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべての管理機能をサポートする OLE オートメーション オブジェクトの集まりです。 複数の OLE DB プロバイダーを対象とするアプリケーションでは、さまざまな OLE DB プロバイダーでサポートされる、これらの汎用 OLE DB インターフェイスを使用します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、プロバイダー固有の DBPROPSET_SQLSERVERCOLUMN プロパティ セットで、次のプロパティを定義しています。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|SSPROP_COL_COLLATIONNAME|型 : VT_BSTR<br /><br /> R/W: 書き込み<br /><br /> 既定値 : NULL<br /><br /> 説明: このプロパティでのみ使用が**ITableDefinition**です。 作成するときに、このプロパティで指定した文字列が使用される、[テーブルの作成](../../t-sql/statements/create-table-transact-sql.md)<br /><br /> ステートメントの使用などがあります。|  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [SQL Server テーブルの作成](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-tables.md)  
  
-   [SQL Server テーブルへの列の追加](../../relational-databases/native-client-ole-db-tables-indexes/adding-a-column-to-a-sql-server-table.md)  
  
-   [SQL Server テーブルからの列の削除](../../relational-databases/native-client-ole-db-tables-indexes/removing-a-column-from-a-sql-server-table.md)  
  
-   [SQL Server テーブルの削除](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-table.md)  
  
-   [SQL Server インデックスの作成](../../relational-databases/native-client-ole-db-tables-indexes/creating-sql-server-indexes.md)  
  
-   [SQL Server インデックスの削除](../../relational-databases/native-client-ole-db-tables-indexes/dropping-a-sql-server-index.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [DROP TABLE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)  
  
  

---
title: 動的管理ビュー (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database scoped dynamic management objects [SQL Server]
- dynamic management objects [SQL Server], about dynamic management objects
- server state information [SQL Server]
- dynamic management functions [SQL Server]
- metadata [SQL Server], dynamic management objects
- dynamic management views [SQL Server]
- DMVs [SQL Server]
- functions [SQL Server], dynamic management
- server scoped dynamic management objects [SQL Server]
- dynamic management objects [SQL Server]
ms.assetid: cf893ecb-0bf6-4cbf-ac00-8a1099e405b1
caps.latest.revision: 41
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c60bf59bfb00e3f2803609de4c8e1b6199692b28
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43075022"
---
# <a name="system-dynamic-management-views"></a>システム動的管理ビュー
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  動的管理ビューと動的管理関数では、サーバーの状態情報が返されます。返された情報は、サーバー インスタンスのヘルス状態の監視、問題の診断、パフォーマンスのチューニングに使用できます。  
  
> [!IMPORTANT]  
>  動的管理ビューと動的管理関数では、実装固有の内部状態データが返されます。 これらのスキーマとデータを返す可能性があります将来のリリース変更の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 したがって、将来のリリースでは、このリリースの動的管理ビューおよび動的管理関数との互換性がなくなる場合があります。 たとえば、将来のリリース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Microsoft は、列リストの末尾に列を追加して、動的管理ビューの定義を拡張することがあります。 構文を使用してお勧め`SELECT * FROM dynamic_management_view_name`実稼働環境でコード列の数が返されるので可能性がありますを変更して、アプリケーションを中断します。  
  
 動的管理ビューと動的管理関数には次の 2 種類があります。  
  
-   サーバー スコープの動的管理ビューと動的管理関数。 これらには、サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
-   データベース スコープの動的管理ビューと動的管理関数。 これらには、データベースに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="querying-dynamic-management-views"></a>動的管理ビューのクエリ  
 動的管理ビューで参照できる[!INCLUDE[tsql](../../includes/tsql-md.md)]2 部、3 部または 4 部構成の名前を使用してステートメントです。 動的管理関数一方で参照できます[!INCLUDE[tsql](../../includes/tsql-md.md)]2 部または 3 つの部分のいずれかの名前を使用してステートメントです。 動的管理ビューおよび関数では参照できません[!INCLUDE[tsql](../../includes/tsql-md.md)]1 つの要素名を使用してステートメントです。  
  
 すべての動的管理ビューと動的管理関数は sys スキーマに含まれ、dm_* という名前付け規則に従います。 動的管理ビューまたは動的管理関数を使用するときには、sys スキーマを使用して、ビューまたは関数の名前にプレフィックスを付ける必要があります。 たとえば、動的管理ビュー dm_os_wait_stats をクエリするには、次のクエリを実行します。  
  
 ```sql
SELECT wait_type, wait_time_ms  
FROM sys.dm_os_wait_stats;  
```  
  
### <a name="required-permissions"></a>必要な権限  
 動的管理ビューまたは動的管理関数をクエリするには、オブジェクトに対する SELECT 権限と、VIEW SERVER STATE または VIEW DATABASE STATE 権限が必要です。 これらの権限を使用することにより、動的管理ビューと動的管理関数に対するユーザーまたはログインのアクセスを選択的に制限できます。 これを行うには、まず master にユーザーを作成し、次にアクセスを禁止する動的管理ビューまたは動的管理関数に対するユーザーの SELECT 権限を拒否します。 これで、このユーザーはデータベース コンテキストに関係なく、設定された動的管理ビューまたは動的管理関数を選択できなくなります。  
  
> [!NOTE]  
>  DENY は優先されるため、ユーザーに VIEW SERVER STATE 権限が許可され、VIEW DATABASE STATE 権限が拒否されている場合、そのユーザーはサーバー レベルの情報は参照できますが、データベース レベルの情報は参照できません。  
  
## <a name="in-this-section"></a>このセクションの内容  
 動的管理ビューと動的管理関数は次のカテゴリに分類されています。  
  
|||  
|-|-|  
|[Always On 可用性グループの動的管理ビューおよび関数 (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)|[メモリ最適化テーブルの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)|  
|[変更データ キャプチャに関連した動的管理ビュー &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/2a771d7d-693a-4f56-9227-02cd00e0e200)|[オブジェクト関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/object-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[変更の追跡関連の動的管理ビュー](http://msdn.microsoft.com/library/dc8a0af9-fcd8-4c34-9453-5132717c9bdb)|[通知関連の動的管理ビューに対してクエリを&#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/92eb22d8-33f3-4c17-b32e-e23acdfbd8f4)|  
|[共通言語ランタイム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)|[レプリケーション関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/replication-related-dynamic-management-views-transact-sql.md)|  
|[データベース ミラーリング関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/04fb21de-1b5e-4a8e-9ca6-1b78ad278db1)|[リソース ガバナー関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md)|  
|[データベース関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)|[セキュリティ関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[実行関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)|[サーバー関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/server-related-dynamic-management-views-and-functions-transact-sql.md)|  
|[拡張イベントの動的管理ビュー](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)|[Service Broker 関連の動的管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)|  
|[Filestream および FileTable 動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)|[空間データ関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/c542ac38-451f-43a5-bf8c-4edd38bb738e)|  
|[フルテキスト検索とセマンティック検索の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)|[SQL Data Warehouse と Parallel Data Warehouse の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)|  
|[地理的レプリケーション動的管理ビューおよび関数&#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)|[SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)|  
|[インデックス関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)|[Stretch Database の動的管理ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/1193efce-a105-49a9-a8b8-26b063485567)|  
|[O 関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)|[トランザクション関連の動的管理ビューおよび関数  &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/transaction-related-dynamic-management-views-and-functions-transact-sql.md)|  

  
## <a name="see-also"></a>参照  
 [アクセス許可の付与 Server &#40;TRANSACT-SQL&#41;](../../t-sql/statements/grant-server-permissions-transact-sql.md)   
 [GRANT (データベースの権限の許可) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-permissions-transact-sql.md)   
 [システム ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)  
  
  

---
title: カタログ ビュー (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sql13.SysViewExpandPortal.f1
dev_langs:
- TSQL
helpviewer_keywords:
- catalog metadata [SQL Server]
- system views [SQL Server], catalog
- metadata [SQL Server], views
- catalogs [SQL Server], metadata
- catalog views [SQL Server]
- Database Engine [SQL Server], metadata
- catalog views [SQL Server], about catalog views
ms.assetid: 13bccc2f-ed3c-4b58-abd0-ca8bf34a66b8
caps.latest.revision: 45
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: fc5a3c84b171a3cd0cf6353462b0de4b69ad2e0a
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34708610"
---
# <a name="system-catalog-views-transact-sql"></a>システム カタログ ビュー (TRANSACT-SQL)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  カタログ ビューは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]によって使用される情報を返します。 カタログ ビューはカタログ メタデータへの最も一般的なインターフェイスであり、この情報を取得、変換、およびカスタマイズした形式で表示するための、最も効率的な方法となります。したがって、カタログ ビューを使用することをお勧めします。 ユーザーが利用できるすべてのカタログ メタデータがカタログ ビューを通じて公開されています。  
  
> [!NOTE]  
>  カタログ ビューには、レプリケーション、バックアップ、データベース メンテナンス プラン、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントなどのカタログ データに関する情報は含まれていません。  
  
 カタログ ビューの中には、他のカタログ ビューの行を継承するものもあります。 たとえば、 [sys.tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)カタログ ビューが継承、 [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)カタログ ビューです。 sys.objects カタログ ビューはベース ビューと呼ばれ、sys.tables ビューは派生ビューと呼ばれます。 sys.tables カタログ ビューではテーブルに固有の列のほか、sys.objects カタログ ビューで返されるすべての列が返されます。 sys.objects カタログ ビューでは、テーブル以外の、ストアド プロシージャやビューなどのオブジェクトの行が返されます。 テーブルの作成後は、両方のビューでテーブルのメタデータが返されます。 これら 2 つのカタログ ビューではテーブルに関する異なるレベルの情報が返されますが、このテーブルのメタデータ内のエントリは 1 つだけで、名前と object_id が、それぞれ 1 つだけ含まれています。 まとめると次のようになります。  
  
-   ベース ビューには列のサブセットと行のスーパーセットが含まれます。  
  
-   派生ビューには列のスーパーセットと行のサブセットが含まれます。  
  
> [!IMPORTANT]  
>  今後の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] のリリースでは、列のリストの末尾に列を追加することにより、システム カタログ ビューの定義が拡張される可能性があります。 SELECT 構文を使用して推奨\*FROM *sys.catalog_view_name*実稼働環境でコード列の数が返されるので可能性がありますを変更して、アプリケーションを中断します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のカタログ ビューは、次のカテゴリに分類されます。  
  
|||  
|-|-|  
|[Always On 可用性グループ カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)|[メッセージ&#40;エラー&#41;カタログ ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/8ac78c53-7b97-41b3-9cbd-5f97c179f1f2)|  
|[Azure SQL データベースのカタログ ビュー](../../relational-databases/system-catalog-views/azure-sql-database-catalog-views.md)|[オブジェクトのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)|  
|[変更の追跡カタログ ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)|[関数のカタログ ビューをパーティション分割&#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)|  
|[CLR アセンブリ カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)|[ポリシーベースの管理ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)|  
|[データ コレクターのビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)|[リソース ガバナーのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)|  
|[データ領域&#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)|[クエリ ストアのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)|  
|[データベース メール ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/database-mail-views-transact-sql.md)|[スカラー型カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)|  
|[データベース ミラーリングのミラーリング監視サーバーのカタログ ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/8a0c9053-5d76-4aa9-a18d-0ea1c514034d)|[スキーマ カタログ ビュー &#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/c516fb1c-b6ed-48ae-99c7-a78bc4336c8e)|  
|[データベースおよびファイルのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)|[セキュリティ カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)|  
|[エンドポイントのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)|[Service Broker カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql.md)|  
|[拡張イベント カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)|[サーバー全体の構成に関するカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)|  
|[拡張プロパティ カタログ ビュー &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/f39fd324-efd4-4468-884c-bf77ed1a026f)|[空間データのカタログ ビュー](../../relational-databases/system-catalog-views/spatial-data-catalog-views.md)|  
|[外部の処理カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/external-operations-catalog-views-transact-sql.md)|[SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)|  
|[Filestream および FileTable のカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)|[データベースのカタログ ビューを拡大&#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/bee78e39-e07d-4b0f-b8ad-09a01a5eb795)|  
|[フルテキスト検索およびセマンティック検索カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/full-text-search-and-semantic-search-catalog-views-transact-sql.md)|[XML スキーマ&#40;XML 型システム&#41;カタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)|  
|[リンク サーバーのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)||  
  
## <a name="see-also"></a>参照  
 [情報スキーマ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [システム テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)   
 [SQL Server システム カタログに対するクエリに関してよくあるご質問](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  

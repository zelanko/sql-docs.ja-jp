---
title: "ALTER FULLTEXT CATALOG (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_FULLEXT_CATALOG_TSQL
- ALTER FULLEXT CATALOG
dev_langs: TSQL
helpviewer_keywords:
- modifying full-text catalogs
- full-text catalogs [SQL Server], rebuilding
- accent sensitivity
- ALTER FULLTEXT CATALOG statement
- full-text catalogs [SQL Server], modifying
- full-text catalogs [SQL Server], reorganizing
ms.assetid: 31a47aaf-6c7f-48a4-a86a-d57aec66c9cb
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fa56a980fa5c5c74a1868f4c03ec791175022f76
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-fulltext-catalog-transact-sql"></a>ALTER FULLTEXT CATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト カタログのプロパティを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER FULLTEXT CATALOG catalog_name   
{ REBUILD [ WITH ACCENT_SENSITIVITY = { ON | OFF } ]  
| REORGANIZE  
| AS DEFAULT   
}  
```  
  
## <a name="arguments"></a>引数  
 *catalog_name*  
 変更するカタログの名前を指定します。 指定した名前のカタログが存在しない場合[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーが返され、ALTER 操作は実行されません。  
  
 REBUILD  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でカタログ全体を再構築することを指定します。 カタログの再構築では、既存のカタログが削除され、代わりに新しいカタログが作成されます。 フルテキスト インデックスの参照を持つすべてのテーブルが新しいカタログに関連付けられます。 再構築すると、データベース システム テーブル内のフルテキスト メタデータがリセットされます。  
  
 WITH ACCENT_SENSITIVITY = {ON|OFF}   
 変更するカタログのフルテキスト インデックス作成とクエリ処理において、アクセントを区別するかしないかを指定します。  
  
 フルテキスト カタログの現在のアクセントの区別に関するプロパティの設定を確認するのに、FULLTEXTCATALOGPROPERTY 関数を使用して、 **accentsensitivity**プロパティの値に対して*catalog_name*です。 この関数で '1' が返された場合、フルテキスト カタログではアクセントが区別され、'0' が返された場合、アクセントは区別されません。  
  
 アクセントの区別は、既定ではカタログとデータベースで同じになっています。  
  
 REORGANIZE  
 指示[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行する、*マスター マージ*、1 つの大きなインデックスにインデックス作成プロセスで作成された小さいインデックスをマージする必要があります。 フルテキスト インデックス フラグメントをマージ、パフォーマンスが向上し、ディスクとメモリ リソースを解放することができます。 フルテキスト カタログが頻繁に変更される場合は、このコマンドを定期的に使用して、フルテキスト カタログを再構成してください。  
  
 REORGANIZE では、内部のインデックスおよびカタログの構造を最適化する処理も行われます。  
  
 インデックスが設定されるデータの量によっては、マスター マージの完了までに時間がかかる場合があります。 マスター マージで大量のデータを処理すると、実行時間が長いトランザクションが発生し、チェックポイント時のログの切り捨てが遅れる場合があります。 この場合、完全復旧モデルでは、トランザクション ログが非常に大きくなることがあります。 完全復旧モデルを使用するデータベースで大きなフルテキスト インデックスを再編成する前に、実行時間が長いトランザクションのための十分な領域をトランザクション ログに割り当てることをお勧めします。 詳細については、「 [トランザクション ログ ファイルのサイズの管理](../../relational-databases/logs/manage-the-size-of-the-transaction-log-file.md)」を参照してください。  
  
 AS DEFAULT   
 このカタログが既定のカタログであることを指定します。 カタログを指定せずにフルテキスト インデックスを作成すると、既定のカタログが使用されます。 既定のフルテキスト カタログが既に存在する場合、このカタログを AS DEFAULT に設定すると、既定の設定が上書きされます。  
  
## <a name="permissions"></a>Permissions  
 ユーザーは、フルテキスト カタログに対する ALTER 権限を持っているかのメンバーである必要があります、 **db_owner**、 **db_ddladmin**固定データベース ロールまたは sysadmin 固定サーバー ロール。  
  
> [!NOTE]  
>  ALTER FULLTEXT CATALOG AS DEFAULT を使用するには、フルテキスト カタログに対する ALTER 権限およびデータベースに対する CREATE FULLTEXT CATALOG 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例の変更、`accentsensitivity`既定のフルテキスト カタログのプロパティ`ftCatalog`、これはアクセントを区別します。  
  
```  
--Change to accent insensitive  
USE AdventureWorks2012;  
GO  
ALTER FULLTEXT CATALOG ftCatalog   
REBUILD WITH ACCENT_SENSITIVITY=OFF;  
GO  
-- Check Accentsensitivity  
SELECT FULLTEXTCATALOGPROPERTY('ftCatalog', 'accentsensitivity');  
GO  
--Returned 0, which means the catalog is not accent sensitive.  
```  
  
## <a name="see-also"></a>参照  
 [sys.fulltext_catalogs &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [フルテキスト カタログ &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [DROP FULLTEXT CATALOG &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)  
  
  

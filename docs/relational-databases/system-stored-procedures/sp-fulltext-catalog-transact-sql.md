---
title: "sp_fulltext_catalog (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_fulltext_catalog_TSQL
- sp_fulltext_catalog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_catalog
ms.assetid: e49b98e4-d1f1-42b2-b16f-eb2fc7aa1cf5
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b3dc2f734fd22d937c403dd63071e17430742ab3
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="spfulltextcatalog-transact-sql"></a>sp_fulltext_catalog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト カタログの作成と削除、およびカタログのインデックス作成の開始と中止を行います。 データベースごとに複数のフルテキスト カタログを作成できます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用して[CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)、 [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)、および[DROP FULLTEXT CATALOG](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_fulltext_catalog [ @ftcat= ] 'fulltext_catalog_name' ,   
     [ @action= ] 'action'   
     [ , [ @path= ] 'root_directory' ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@ftcat=**] **'***fulltext_catalog_name***'**  
 フルテキスト カタログの名前を指定します。 カタログ名は各データベース内で一意である必要があります。 *fulltext_catalog_name* is **sysname**.  
  
 [  **@action=**] **'***アクション***'**  
 実行する操作を指定します。 *アクション*は**varchar (20)**、これらの値のいずれかを指定できます。  
  
> [!NOTE]  
>  フルテキスト カタログは必要に応じて作成、削除、修正できますが、 複数のカタログで同時にスキーマを変更することは避けてください。 使用してこれらの操作を実行することができます、 **sp_fulltext_table**ストアド プロシージャで、ことをお勧めします。  
  
|[値]|Description|  
|-----------|-----------------|  
|**作成**|ファイル システムに空の新しいフルテキスト カタログを作成し、内の関連する行を追加**sysfulltextcatalogs**で、 *fulltext_catalog_name*と*root_directory*、存在する場合は、次の値です。 *fulltext_catalog_name*データベース内で一意である必要があります。|  
|**Drop**|削除操作を行う*fulltext_catalog_name*ファイル システムから削除してに関連付けられている行を削除する**sysfulltextcatalogs**です。 このカタログに 1 つ以上のテーブルのインデックスが含まれている場合、このアクションは失敗します。 **sp_fulltext_table** '*table_name*', 'drop' should be executed to drop the tables from the catalog.<br /><br /> カタログが存在しない場合、エラーが表示されます。|  
|**start_incremental**|増分作成を開始*fulltext_catalog_name*です。 カタログが存在しない場合、エラーが表示されます。 フルテキスト インデックス作成が既にアクティブな場合、警告が表示され、作成は行われません。 増分作成で変更された行だけに取得されるフルテキスト インデックスの作成が存在する**タイムスタンプ**列、テーブル内のフルテキスト インデックスを作成します。|  
|**start_full**|完全作成を開始*fulltext_catalog_name*です。 既にインデックス作成が行われている場合でも、このフルテキスト カタログと関連するすべてのテーブルにあるすべての行が、フルテキスト インデックス作成用に取得されます。|  
|**[停止]**|インデックスの作成を停止する*fulltext_catalog_name*です。 カタログが存在しない場合、エラーが表示されます。 インデックスの作成を既に中止している場合、警告は表示されません。|  
|**[再構築]**|再構築*fulltext_catalog_name*です。 カタログの再構築では、既存のカタログが削除され、代わりに新しいカタログが作成されます。 フルテキスト インデックスの参照を持つすべてのテーブルが新しいカタログに関連付けられます。 再構築すると、データベース システム テーブル内のフルテキスト メタデータがリセットされます。<br /><br /> 変更の追跡がオフになっていると、再構築しても、新しく作成されたフルテキスト カタログにデータが再び追加されることはありません。 この場合は、再作成すると、次のように実行します。 **sp_fulltext_catalog**で、 **start_full**または**start_incremental**アクション。|  
  
 [ **@path=**] **'***root_directory***'**  
 ルート ディレクトリ (完全な物理パスではありません) は、**作成**アクション。 *ただし、物理的な*は**nvarchar (100)**あり、既定値は NULL の場合、セットアップで指定された既定の場所の使用を示します。 これは Mssql ディレクトリ内の Ftdata サブディレクトリをします。たとえば、C:\Program files \microsoft SQL Server\MSSQL13 です。MSSQLSERVER\MSSQL\FTData です。 指定するルート ディレクトリは、同じコンピューター上のドライブに存在している必要があります。ルート ディレクトリ名には、ドライブ文字だけを指定したり、相対パスを指定することはできません。 ネットワーク ドライブ、リムーバブル ドライブ、フロッピー ディスク、および UNC パスはサポートされていません。 インスタンスに関連付けられているローカル ハード ドライブ上のフルテキスト カタログを作成する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 **@path**有効な場合にのみ*アクション*は**作成**です。 以外のアクションの**作成**(**停止**、**を再構築**など)、  **@path**  NULL にする必要がありますか省略するとします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがクラスター内の仮想サーバーの場合、指定するカタログ ディレクトリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースが依存する共有ディスク ドライブ上にある必要があります。 場合@pathが指定されていない、既定のカタログ ディレクトリの場所が、共有ディスク ドライブに、仮想サーバーをインストールしたときに指定されたディレクトリにします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **Start_full**内のフルテキスト データの完全なスナップショットを作成するアクションが使用される*fulltext_catalog_name*です。 **Start_incremental**データベースで変更された行だけのインデックスを再作成するアクションを使用します。 テーブル型の列がある場合にのみ、増分作成を適用できる**タイムスタンプ**です。 フルテキスト カタログ内のテーブルには、型の列が含まれていない場合**タイムスタンプ**テーブルで完全作成が行われます。  
  
 フルテキスト カタログおよびインデックス データは、フルテキスト カタログ ディレクトリに作成したファイルに格納されます。 フルテキスト カタログ ディレクトリはディレクトリで指定したディレクトリのサブディレクトリとして作成 **@path** またはサーバーの既定のフルテキスト カタログ ディレクトリに場合 **@path** はありません指定します。 フルテキスト カタログ ディレクトリの名前は、サーバー上で一意になるように作成されます。 したがって、特定のサーバー上のすべてのフルテキスト カタログ ディレクトリで、同じパスを共有できます。  
  
## <a name="permissions"></a>権限  
 呼び出し元がのメンバーであるため、 **db_owner**ロール。 によって要求されたアクションを呼び出し元は拒否されていない ALTER または CONTROL 権限 (を**db_owner**が)、対象のフルテキスト カタログにします。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-create-a-full-text-catalog"></a>A. フルテキスト カタログを作成する  
 この例は、空のフルテキスト カタログを作成**Cat_Desc**で、 **AdventureWorks2012**データベース。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'create';  
GO  
```  
  
### <a name="b-to-rebuild-a-full-text-catalog"></a>B. フルテキスト カタログを再構築するには  
 この例は、既存のフルテキスト カタログを再構築**Cat_Desc**で、 **AdventureWorks2012**データベース。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'rebuild';  
GO  
```  
  
### <a name="c-start-the-population-of-a-full-text-catalog"></a>C. フルテキスト カタログの作成を開始する  
 この例の完全作成を開始する、 **Cat_Desc**カタログ。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'start_full';  
GO  
```  
  
### <a name="d-stop-the-population-of-a-full-text-catalog"></a>D. フルテキスト カタログの作成を中止する  
 この例の作成を停止する、 **Cat_Desc**カタログ。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'stop';  
GO  
```  
  
### <a name="e-to-remove-a-full-text-catalog"></a>E. フルテキスト カタログを削除する  
 この例は、 **Cat_Desc**カタログ。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'drop';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [FULLTEXTCATALOGPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql.md)   
 [sp_help_fulltext_catalogs および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_catalogs_cursor &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)  
  
  

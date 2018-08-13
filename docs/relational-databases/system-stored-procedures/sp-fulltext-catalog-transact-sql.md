---
title: sp_fulltext_catalog (Transact SQL) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fulltext_catalog_TSQL
- sp_fulltext_catalog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_catalog
ms.assetid: e49b98e4-d1f1-42b2-b16f-eb2fc7aa1cf5
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 7bd63fff2c2c395648a1ac8a61903db007cafc96
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39559772"
---
# <a name="spfulltextcatalog-transact-sql"></a>sp_fulltext_catalog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  フルテキスト カタログの作成と削除、およびカタログのインデックス作成の開始と中止を行います。 データベースごとに複数のフルテキスト カタログを作成できます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)、 [ALTER FULLTEXT CATALOG](../../t-sql/statements/alter-fulltext-catalog-transact-sql.md)、および[DROP FULLTEXT CATALOG](../../t-sql/statements/drop-fulltext-catalog-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_fulltext_catalog [ @ftcat= ] 'fulltext_catalog_name' ,   
     [ @action= ] 'action'   
     [ , [ @path= ] 'root_directory' ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@ftcat=**] **'***fulltext_catalog_name***'**  
 フルテキスト カタログの名前を指定します。 カタログ名は各データベース内で一意である必要があります。 *fulltext_catalog_name* 、 **sysname**。  
  
 [  **@action=**] **'***アクション***'**  
 実行する操作を指定します。 *アクション*は**varchar (20)**、これらの値のいずれかを指定できます。  
  
> [!NOTE]  
>  フルテキスト カタログは必要に応じて作成、削除、修正できますが、 複数のカタログで同時にスキーマを変更することは避けてください。 使用してこれらの操作を実行することができます、 **sp_fulltext_table**ストアド ・ プロシージャでは、推奨される方法であります。  
  
|値|説明|  
|-----------|-----------------|  
|**作成**|ファイル システムで、新しい空のフルテキスト カタログを作成しで、関連付けられている行を追加**sysfulltextcatalogs**と、 *fulltext_catalog_name*と*ただし、物理的な*、存在する場合は、次の値です。 *fulltext_catalog_name*データベース内で一意である必要があります。|  
|**Drop**|落下*fulltext_catalog_name*に関連付けられている行を削除するファイル ・ システムから削除することによって**sysfulltextcatalogs**。 このカタログに 1 つ以上のテーブルのインデックスが含まれている場合、このアクションは失敗します。 **sp_fulltext_table** '*table_name*'、'削除' を実行するカタログからテーブルを削除する必要があります。<br /><br /> カタログが存在しない場合、エラーが表示されます。|  
|**start_incremental**|カタログの増分作成を開始*fulltext_catalog_name*。 カタログが存在しない場合、エラーが表示されます。 フルテキスト インデックス作成が既にアクティブな場合、警告が表示され、作成は行われません。 存在が、変更された行だけをフルテキスト インデックス作成、取得するよう増分作成で、**タイムスタンプ**テーブル内の列、フルテキスト インデックスを作成します。|  
|**start_full**|全カタログの作成を開始*fulltext_catalog_name*。 既にインデックス作成が行われている場合でも、このフルテキスト カタログと関連するすべてのテーブルにあるすべての行が、フルテキスト インデックス作成用に取得されます。|  
|**[停止]**|インデックスのカタログ作成を停止する*fulltext_catalog_name*。 カタログが存在しない場合、エラーが表示されます。 インデックスの作成を既に中止している場合、警告は表示されません。|  
|**Rebuild**|再構築*fulltext_catalog_name*。 カタログの再構築では、既存のカタログが削除され、代わりに新しいカタログが作成されます。 フルテキスト インデックスの参照を持つすべてのテーブルが新しいカタログに関連付けられます。 再構築すると、データベース システム テーブル内のフルテキスト メタデータがリセットされます。<br /><br /> 変更の追跡がオフになっていると、再構築しても、新しく作成されたフルテキスト カタログにデータが再び追加されることはありません。 この例では、再作成すると、次のように実行します。 **sp_fulltext_catalog**と、 **start_full**または**start_incremental**アクション。|  
  
 [ **@path=**] **'***root_directory***'**  
 ルート ディレクトリ (、完全な物理パスではなく) は、**作成**アクション。 *ただし、物理的な*、 **nvarchar(100)** のセットアップ時に指定された既定の場所の使用を示す、NULL の既定値があるとします。 これは Mssql ディレクトリ内の Ftdata サブディレクトリをします。たとえば、C:\Program files \microsoft SQL Server\MSSQL13 です。MSSQLSERVER\MSSQL\FTData です。 指定するルート ディレクトリは、同じコンピューター上のドライブに存在している必要があります。ルート ディレクトリ名には、ドライブ文字だけを指定したり、相対パスを指定することはできません。 ネットワーク ドライブ、リムーバブル ドライブ、フロッピー ディスク、および UNC パスはサポートされていません。 インスタンスに関連付けられているローカルのハード ドライブ上のフルテキスト カタログを作成する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 **@path** 有効な場合にのみ*アクション*は**作成**です。 以外のアクションの**作成**(**停止**、**を再構築**など)、 **@path** NULL であるかを省略するとします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがクラスター内の仮想サーバーの場合、指定するカタログ ディレクトリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースが依存する共有ディスク ドライブ上にある必要があります。 場合@pathが指定されていない、既定のカタログ ディレクトリの場所が仮想サーバーのインストール時に指定されたディレクトリ内のディスク ドライブの共有。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **Start_full**のフル ・ テキスト ・ データの完全なスナップショットを作成するアクションが使用される*fulltext_catalog_name*。 **Start_incremental**アクションは、データベースで変更された行だけを再インデックス付けに使用します。 テーブル型の列がある場合にのみ、増分作成を適用できる**タイムスタンプ**します。 フルテキスト カタログ内のテーブルには、型の列が含まれていない場合**タイムスタンプ**テーブルには完全作成が行われます。  
  
 フルテキスト カタログおよびインデックス データは、フルテキスト カタログ ディレクトリに作成したファイルに格納されます。 フルテキスト カタログ ディレクトリで指定されたディレクトリのサブディレクトリとして作成**@path**またはサーバーの既定のフルテキスト カタログ ディレクトリに場合**@path**はありません指定します。 フルテキスト カタログ ディレクトリの名前は、サーバー上で一意になるように作成されます。 したがって、特定のサーバー上のすべてのフルテキスト カタログ ディレクトリで、同じパスを共有できます。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーの呼び出し元が必要な**db_owner**の役割です。 によって要求されたアクションを呼び出し元する必要がありますいない権限を拒否する変更またはコントロール (、 **db_owner**が) 対象のフルテキスト カタログにします。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-create-a-full-text-catalog"></a>A. フルテキスト カタログを作成する  
 次の使用例は、空のフルテキスト カタログを作成**Cat_Desc**で、 **AdventureWorks2012**データベースです。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'create';  
GO  
```  
  
### <a name="b-to-rebuild-a-full-text-catalog"></a>B. フルテキスト カタログを再構築するには  
 次の使用例は、既存のフルテキスト カタログを再構築します**Cat_Desc**で、 **AdventureWorks2012**データベースです。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'rebuild';  
GO  
```  
  
### <a name="c-start-the-population-of-a-full-text-catalog"></a>C. フルテキスト カタログの作成を開始する  
 この例の全カタログの作成を開始する、 **Cat_Desc**カタログです。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'start_full';  
GO  
```  
  
### <a name="d-stop-the-population-of-a-full-text-catalog"></a>D. フルテキスト カタログの作成を中止する  
 次の使用例のカタログ作成を停止する、 **Cat_Desc**カタログです。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'stop';  
GO  
```  
  
### <a name="e-to-remove-a-full-text-catalog"></a>E. フルテキスト カタログを削除する  
 この例で削除、 **Cat_Desc**カタログです。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'drop';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_database &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql.md)   
 [sp_help_fulltext_catalogs &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_catalogs_cursor &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)  
  
  

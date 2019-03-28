---
title: sp_fulltext_catalog (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_catalog_TSQL
- sp_fulltext_catalog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_catalog
ms.assetid: e49b98e4-d1f1-42b2-b16f-eb2fc7aa1cf5
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f97a1f480b360270d803c502dd40a6e1653b3935
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526444"
---
# <a name="spfulltextcatalog-transact-sql"></a>sp_fulltext_catalog (Transact SQL)
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
`[ @ftcat = ] 'fulltext_catalog_name'` フルテキスト カタログの名前です。 カタログ名は、データベースごとに一意である必要があります。 *fulltext_catalog_name*は**sysname**します。  
  
`[ @action = ] 'action'` 実行する操作です。 *アクション*は**varchar (20)**、これらの値のいずれかを指定できます。  
  
> [!NOTE]  
>  フルテキスト カタログの作成、削除、および必要に応じて変更します。 複数のカタログで同時にスキーマを変更することは避けてください。 使用してこれらのアクションを実行できる、 **sp_fulltext_table**ストアド プロシージャは、これは推奨される方法です。  
  
|値|説明|  
|-----------|-----------------|  
|**作成**|ファイル システムに空の新しいフルテキスト カタログを作成しに関連付けられている行を追加します**sysfulltextcatalogs**で、 *fulltext_catalog_name*と*root_directory*、存在する場合は、次の値です。 *fulltext_catalog_name*データベース内で一意である必要があります。|  
|**Drop**|削除操作を行う*fulltext_catalog_name*ファイル システムから削除してに関連する行を削除する**sysfulltextcatalogs**します。 このカタログには、1 つまたは複数のテーブルのインデックスが含まれている場合、このアクションは失敗します。 **sp_fulltext_table** '*table_name*'、'drop' は、カタログからテーブルを削除するために実行する必要があります。<br /><br /> カタログが存在しない場合、エラーが表示されます。|  
|**start_incremental**|増分作成を開始*fulltext_catalog_name*します。 カタログが存在しない場合、エラーが表示されます。 フルテキスト インデックス作成が既にアクティブである場合、警告が表示されますが、カタログの作成は行われません。 存在が、変更された行だけをフルテキスト インデックス作成、取得するよう増分作成で、**タイムスタンプ**テーブル内の列、フルテキスト インデックスを作成します。|  
|**start_full**|完全作成を開始*fulltext_catalog_name*します。 フルテキスト インデックスが既に作成されている場合でも、このフルテキスト カタログに関連付けられているすべてのテーブルのすべての行が取得されます。|  
|**[停止]**|インデックスの作成を停止する*fulltext_catalog_name*します。 カタログが存在しない場合、エラーが表示されます。 インデックスの作成を既に中止している場合、警告は表示されません。|  
|**Rebuild**|再構築*fulltext_catalog_name*します。 カタログを再構築すると、既存のカタログは削除され、代わりに新しいカタログが作成します。 フルテキスト インデックス作成の参照があるすべてのテーブルは、新しいカタログに関連付けられます。 再構築には、データベース システム テーブル内のフルテキスト メタデータがリセットされます。<br /><br /> 変更の追跡が OFF の場合、再構築しても、新しく作成されたフルテキスト カタログの再作成は発生しません。 この場合、再作成する次のように実行します。 **sp_fulltext_catalog**で、 **start_full**または**start_incremental**アクション。|  
  
`[ @path = ] 'root_directory'` ルート ディレクトリ (、完全な物理パスではなく) は、**作成**アクション。 *ただし、物理的な*は**nvarchar (100)** あり、既定値は null の場合、セットアップ時に指定された既定の場所の使用を示すです。 これは Mssql ディレクトリ内の Ftdata サブディレクトリです。たとえば、C:\Program files \microsoft SQL Server\MSSQL13 です。MSSQLSERVER\MSSQL\FTData します。 指定したルート ディレクトリが存在する必要が同じコンピューター上のドライブ、ドライブ文字だけで構成され、相対パスにすることはできません。 ネットワーク ドライブ、リムーバブル ドライブ、フロッピー ディスク、および UNC パスはサポートされていません。 インスタンスに関連付けられているローカルのハード ドライブ上のフルテキスト カタログを作成する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
 **@path** 有効な場合にのみ*アクション*は**作成**です。 以外のアクションの**作成**(**停止**、**を再構築**など)、 **@path** NULL であるかを省略するとします。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスがクラスター内の仮想サーバーの場合、指定するカタログ ディレクトリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースが依存する共有ディスク ドライブ上にある必要があります。 場合@pathが指定されていない、既定のカタログ ディレクトリの場所が仮想サーバーのインストール時に指定されたディレクトリ内のディスク ドライブの共有。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **Start_full**でフルテキスト データの完全なスナップショットを作成するアクションが使用される*fulltext_catalog_name*します。 **Start_incremental**アクションは、データベースで変更された行のみのインデックスを再作成するために使用します。 テーブル型の列がある場合にのみ、増分作成を適用できる**タイムスタンプ**します。 フルテキスト カタログ内のテーブルには、型の列が含まれていない場合**タイムスタンプ**テーブルには完全作成が行われます。  
  
 フルテキスト カタログおよびインデックス データは、フルテキスト カタログ ディレクトリに作成したファイルに格納されます。 フルテキスト カタログ ディレクトリで指定されたディレクトリのサブディレクトリとして作成**@path**またはサーバーの既定のフルテキスト カタログ ディレクトリに場合**@path**はありません指定します。 フルテキスト カタログ ディレクトリの名前は、サーバー上で一意でことが保証する方法で構築されています。 そのため、サーバー上のすべてのフルテキスト カタログ ディレクトリは、同じパスを共有できます。  
  
## <a name="permissions"></a>アクセス許可  
 呼び出し元がのメンバーであるために必要な**db_owner**ロール。 によって要求された操作、呼び出し元が拒否されていない ALTER または CONTROL 権限 (が**db_owner**が)、ターゲット、フルテキスト カタログ。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-create-a-full-text-catalog"></a>A. フルテキスト カタログを作成する  
 この例は、空のフルテキスト カタログを作成します。 **Cat_Desc**の、 **AdventureWorks2012**データベース。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'create';  
GO  
```  
  
### <a name="b-to-rebuild-a-full-text-catalog"></a>B. フルテキスト カタログを再構築するには  
 この例では、既存のフルテキスト カタログを再構築。 **Cat_Desc**の、 **AdventureWorks2012**データベース。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'rebuild';  
GO  
```  
  
### <a name="c-start-the-population-of-a-full-text-catalog"></a>C. フルテキスト カタログの作成を開始します。  
 この例の完全作成を開始する、 **Cat_Desc**カタログ。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'start_full';  
GO  
```  
  
### <a name="d-stop-the-population-of-a-full-text-catalog"></a>D. フルテキスト カタログの作成を中止します。  
 この例の作成を中止します、 **Cat_Desc**カタログ。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'stop';  
GO  
```  
  
### <a name="e-to-remove-a-full-text-catalog"></a>E. フルテキスト カタログを削除するには  
 この例は、 **Cat_Desc**カタログ。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_fulltext_catalog 'Cat_Desc', 'drop';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [FULLTEXTCATALOGPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)   
 [sp_fulltext_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql.md)   
 [sp_help_fulltext_catalogs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_catalogs_cursor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [フルテキスト検索](../../relational-databases/search/full-text-search.md)  
  
  

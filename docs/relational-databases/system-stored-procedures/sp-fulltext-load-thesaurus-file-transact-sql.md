---
title: sp_fulltext_load_thesaurus_file (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_load_thesaurus_file
- sp_fulltext_load_thesaurus_file_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_load_thesaurus_file
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], editing
ms.assetid: 73a309c3-6d22-42dc-a6fe-8a63747aa2e4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d076bfde2e4dc4a71af558a08f197d20144ce9db
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47840973"
---
# <a name="spfulltextloadthesaurusfile-transact-sql"></a>sp_fulltext_load_thesaurus_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された LCID の言語に対応する類義語辞典ファイルのデータをサーバー インスタンスで解析して読み込みます。 このストアド プロシージャは、類義語辞典ファイルを更新した後に役立ちます。 実行**sp_fulltext_load_thesaurus_file**により、指定された LCID の類義語辞典を使用して、フルテキスト クエリの再コンパイルします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_fulltext_load_thesaurus_file lcid [ , @loadOnlyIfNotLoaded  = action ]   
```  
  
## <a name="arguments"></a>引数  
 *lcid*  
 類義語辞典 XML 定義を読み込む言語のロケール識別子 (LCID) に対応する整数です。 サーバー インスタンスで使用可能な言語の Lcid を取得する、 [sys.fulltext_languages &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)カタログ ビューです。  
  
 **@loadOnlyIfNotLoaded** = *アクション*  
 類義語辞典ファイルが既に読み込まれている場合でも、内部の類義語辞典テーブルに類義語辞典ファイルを読み込むかどうかを指定します。 *アクション*の 1 つです。  
  
|値|定義|  
|-----------|----------------|  
|**0**|類義語辞典ファイルが既に読み込まれているかどうかにかかわらず、類義語辞典ファイルを読み込みます。 これは、既定の動作の**sp_fulltext_load_thesaurus_file**します。|  
|1|類義語辞典ファイルがまだ読み込まれていない場合にのみ、類義語辞典ファイルを読み込みます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 類義語辞典ファイルは、類義語辞典を使用するフルテキスト クエリによって自動的に読み込まれます。 実行することお勧めをフルテキスト クエリのこの初回使用時のパフォーマンスに影響を避けるためには、 **sp_fulltext_load_thesaurus_file**します。  
  
 使用[sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)'**update_languages**'、フルテキスト検索に登録された言語の一覧を更新します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたはシステム管理者が実行できる、 **sp_fulltext_load_thesaurus_file**ストアド プロシージャ。  
  
 類義語辞典ファイルを更新、変更、または削除できるのはシステム管理者だけです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-load-a-thesaurus-file-even-if-it-is-already-loaded"></a>A. 類義語辞典ファイルが既に読み込まれている場合でも類義語辞典ファイルを読み込む  
 次の例では、解析して、英語の類義語辞典ファイルを読み込みます。  
  
```  
EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
GO  
```  
  
### <a name="b-load-a-thesaurus-file-only-if-it-is-not-yet-loaded"></a>B. 類義語辞典ファイルがまだ読み込まれていない場合にのみ、類義語辞典ファイルを読み込む。  
 次の例では、アラビア語の類義語辞典ファイルがまだ読み込まれていない場合に、アラビア語の類義語辞典ファイルを解析して読み込みます。  
  
```  
EXEC sys.sp_fulltext_load_thesaurus_file 1025, @loadOnlyIfNotLoaded = 1;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [構成して、フルテキスト検索の類義語辞典ファイルを管理](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [フルテキスト検索に使用する類義語辞典ファイルの構成と管理](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)  
  
  

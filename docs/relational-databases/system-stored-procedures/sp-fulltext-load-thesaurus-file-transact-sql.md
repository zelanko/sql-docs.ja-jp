---
title: "sp_fulltext_load_thesaurus_file (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: de4468120488b4f7d8942ecf540c36370a36de7f
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="spfulltextloadthesaurusfile-transact-sql"></a>sp_fulltext_load_thesaurus_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定された LCID の言語に対応する類義語辞典ファイルのデータをサーバー インスタンスで解析して読み込みます。 このストアド プロシージャは、類義語辞典ファイルを更新した後に役立ちます。 実行する**sp_fulltext_load_thesaurus_file**により指定された LCID の類義語辞典を使用して、フルテキスト クエリの再コンパイルします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_fulltext_load_thesaurus_file lcid [ , @loadOnlyIfNotLoaded  = action ]   
```  
  
## <a name="arguments"></a>引数  
 *lcid*  
 類義語辞典 XML 定義を読み込む言語のロケール識別子 (LCID) に対応する整数です。 サーバー インスタンスで使用可能な言語の Lcid を取得するを使用して、 [sys.fulltext_languages &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)カタログ ビューです。  
  
 **@loadOnlyIfNotLoaded** = *アクション*  
 類義語辞典ファイルが既に読み込まれている場合でも、内部の類義語辞典テーブルに類義語辞典ファイルを読み込むかどうかを指定します。 *アクション*の 1 つです。  
  
|[値]|定義|  
|-----------|----------------|  
|**0**|類義語辞典ファイルが既に読み込まれているかどうかにかかわらず、類義語辞典ファイルを読み込みます。 既定の動作は、この**sp_fulltext_load_thesaurus_file**です。|  
|1|類義語辞典ファイルがまだ読み込まれていない場合にのみ、類義語辞典ファイルを読み込みます。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 類義語辞典ファイルは、類義語辞典を使用するフルテキスト クエリによって自動的に読み込まれます。 フルテキスト クエリの初回実行時のパフォーマンスへの影響を回避することをお勧めを実行して**sp_fulltext_load_thesaurus_file**です。  
  
 使用して[sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)'**update_languages**'、フルテキスト検索に登録された言語の一覧を更新します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたはシステム管理者が実行できる、 **sp_fulltext_load_thesaurus_file**ストアド プロシージャです。  
  
 類義語辞典ファイルを更新、変更、または削除できるのはシステム管理者だけです。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-load-a-thesaurus-file-even-if-it-is-already-loaded"></a>A. 類義語辞典ファイルが既に読み込まれている場合でも類義語辞典ファイルを読み込む  
 次の例では、解析し、英語の類義語辞典ファイルを読み込みます。  
  
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
 [FULLTEXTSERVICEPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [構成して、フルテキスト検索の類義語辞典ファイルの管理](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [フルテキスト検索に使用する類義語辞典ファイルの構成と管理](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)  
  
  

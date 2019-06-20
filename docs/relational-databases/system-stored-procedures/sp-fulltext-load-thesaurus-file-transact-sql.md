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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c0857066ba5f8f57a5a6d088a4f37d69315225ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822764"
---
# <a name="spfulltextloadthesaurusfile-transact-sql"></a>sp_fulltext_load_thesaurus_file (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー インスタンスを解析し、指定された LCID の言語に対応する類義語辞典ファイルからデータを読み込むとします。 このストアド プロシージャは、類義語辞典ファイルを更新した後に便利です。 実行**sp_fulltext_load_thesaurus_file**により、指定された LCID の類義語辞典を使用して、フルテキスト クエリの再コンパイルします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sys.sp_fulltext_load_thesaurus_file lcid [ , @loadOnlyIfNotLoaded  = action ]   
```  
  
## <a name="arguments"></a>引数  
 *lcid*  
 類義語辞典 XML 定義の対応する言語のロケール識別子 (LCID) を対応する整数。 サーバー インスタンスで使用可能な言語の Lcid を取得する、 [sys.fulltext_languages &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)カタログ ビューです。  
  
 **@loadOnlyIfNotLoaded** = *アクション*  
 既に読み込まれている場合でも、内部の類義語辞典テーブルに類義語辞典ファイルが読み込まれるかどうかを指定します。 *アクション*の 1 つです。  
  
|値|定義|  
|-----------|----------------|  
|**0**|既にの読み込むかどうかに関係なく、類義語辞典ファイルを読み込みます。 これは、既定の動作の**sp_fulltext_load_thesaurus_file**します。|  
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
  
```sql
EXEC sys.sp_fulltext_load_thesaurus_file 1033;
```  
  
### <a name="b-load-a-thesaurus-file-only-if-it-is-not-yet-loaded"></a>B. 類義語辞典ファイルがまだ読み込まれていない場合にのみ、類義語辞典ファイルを読み込む。  
 次の例では、解析して、既に読み込まれていない限り、アラビア語の類義語辞典ファイルを読み込みます。  
  
```sql
EXEC sys.sp_fulltext_load_thesaurus_file 1025, @loadOnlyIfNotLoaded = 1;
```  

## <a name="see-also"></a>参照

[FULLTEXTSERVICEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)  
[システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
[フルテキスト検索に使用する類義語辞典ファイルの構成と管理](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)

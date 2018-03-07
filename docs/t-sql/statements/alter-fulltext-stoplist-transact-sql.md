---
title: "ALTER FULLTEXT STOPLIST (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER FULLTEXT STOPLIST
- ALTER_FULLTEXT_STOPLIST_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- ALTER FULLTEXT STOPLIST statement
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: f6ad87d5-6a34-435a-8456-8244947c5c83
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 20947c0331f9713a937e0a7de8efb1f2fc9f753c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="alter-fulltext-stoplist-transact-sql"></a>ALTER FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースの既定のフルテキスト ストップリストに対してストップワードを挿入または削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER FULLTEXT STOPLIST stoplist_name  
{   
        ADD [N] 'stopword' LANGUAGE language_term    
  | DROP   
    {  
        'stopword' LANGUAGE language_term   
      | ALL LANGUAGE language_term   
      | ALL  
     }  
;  
```  
  
## <a name="arguments"></a>引数  
 *stoplist_name*  
 変更するストップリストの名前を指定します。 *stoplist_name*最大 128 文字まで指定できます。  
  
 **'** *ストップ ワード* **'**  
 指定した言語で言語的な意味を持つ単語の場合や言語的な意味のないトークンの場合がある文字列を指定します。 *ストップ ワード*は最大トークン長 (64 文字) に制限されます。 ストップワードは Unicode 文字列として指定できます。  
  
 言語*language_term*  
 関連付ける言語を指定します、*ストップ ワード*追加または削除します。  
  
 *language_term*文字列、整数、または次のように、言語のロケール識別子 (LCID) に対応する 16 進数の値として指定できます。  
  
|Format|Description|  
|------------|-----------------|  
|文字列|*language_term*に対応する、**エイリアス**列の値、 [sys.syslanguages (TRANSACT-SQL)](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)互換性ビューです。 文字列は、ように、単一引用符で囲む必要があります**'***language_term***'**です。|  
|Integer|*language_term*言語の LCID です。|  
|16 進数|*language_term*は 0 x 後に LCID の 16 進数の値。 16 進数の値は、先頭の 0 を含め、8 桁以内で指定してください。 値を 2 バイト文字セット (DBCS) の形式で指定すると、SQL Server で Unicode に変換されます。|  
  
 追加**'***ストップ ワード***'**言語*language_term*  
 言語で指定された言語のストップ リストにストップ ワードを追加*language_term*です。  
  
 指定したキーワードの組み合わせと言語の LCID 値がストップリスト内で一意でない場合、エラーが返されます。  LCID 値が登録言語に対応していない場合は、エラーが生成されます。  
  
 DROP { **'***ストップ ワード***'**言語*language_term* |すべての言語*language_term* |すべて}  
 ストップ リストからストップ ワードを削除します。  
  
 **'** *ストップ ワード* **'**言語*language_term*  
 指定された言語の指定されたストップ ワード削除*language_term*です。  
  
 すべての言語*language_term*  
 すべてで指定された言語のストップ ワードの削除*language_term*です。  
  
 ALL  
 ストップリストのストップワードをすべて削除します。  
  
## <a name="remarks"></a>解説  
 CREATE FULLTEXT STOPLIST は互換性レベル 100 以上に対してのみサポートされます。 互換性レベル 80 および 90 の場合は、常にシステム ストップリストがデータベースに割り当てられます。  
  
## <a name="permissions"></a>Permissions  
 ストップリストをデータベースの既定のストップリストとして指定するには、ALTER DATABASE 権限が必要です。 それ以外の場合、ストップ リストを変更するには、ストップ リストの所有者またはメンバーシップが必要、 **db_owner**または**db_ddladmin**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、というストップ リストを変更`CombinedFunctionWordList`、用に追加、単語 'en' をまずスペイン語用、フランス語です。  
  
```  
ALTER FULLTEXT STOPLIST CombinedFunctionWordList ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST CombinedFunctionWordList ADD 'en' LANGUAGE 'French';  
```  
  
## <a name="see-also"></a>参照  
 [FULLTEXT STOPLIST &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [DROP FULLTEXT STOPLIST &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)   
 [構成およびストップ ワードとストップ リストをフルテキスト検索の管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [sys.fulltext_stoplists &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)  
  
  

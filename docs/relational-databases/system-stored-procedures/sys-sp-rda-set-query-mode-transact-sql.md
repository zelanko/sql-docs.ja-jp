---
title: sys.sp_rda_set_query_mode (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_query_mode
- sys.sp_rda_set_query_mode_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_query_mode stored procedure
ms.assetid: 65a0b390-cf87-4db7-972a-1fdf13456c88
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4741ef6ac09d81da5054200363f12753130c2e5f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410441"
---
# <a name="syssprdasetquerymode-transact-sql"></a>sys.sp_rda_set_query_mode (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  現在の Stretch 対応データベースとそのテーブルに対するクエリがローカルとリモートの両方のデータ (既定)、またはローカルのデータのみを返すかどうかを指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_rda_set_query_mode [ @mode = ] @mode   
    [ , [ @force = ]  @force ]  
```  
  
## <a name="arguments"></a>引数  
 [ @mode = ] *@mode*  
 次の値の 1 つです。  
  
-   **無効になっている**Stretch 対応テーブルに対するすべてのクエリは失敗します。  
  
-   **LOCAL_ONLY** Stretch 対応テーブルに対するクエリがローカル データだけを返します。  
  
-   **LOCAL_AND_REMOTE** Stretch 対応テーブルに対するクエリは、ローカルとリモートの両方のデータを返します。 これは既定の動作です。  
  
 [ @force = ]  *@force*  
 検証を伴わないクエリ モードを変更する場合は 1 に設定できるオプションのビット値です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または >0 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 Db_owner アクセス許可が必要です。  
  
## <a name="remarks"></a>コメント  
 次の拡張ストアド プロシージャでは、Stretch 対応データベースのクエリ モードも設定します。  
  
-   **sp_rda_deauthorize_db**  
  
     実行した後**sp_rda_deauthorize_db** 、Stretch 対応データベースとテーブルに対するすべてのクエリは失敗します。 つまり、クエリ モードは無効に設定します。 このモードを終了するには、次のいずれかの操作を行います。  
  
    -   実行[sys.sp_rda_reauthorize_db &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)リモート Azure データベースに再接続します。 この操作に自動的にリセット クエリ モード LOCAL_AND_REMOTE、Stretch Database の既定の動作はします。 つまり、クエリは、ローカルとリモートの両方のデータから結果を返します。  
  
    -   実行[sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md)をクエリがローカルのデータのみに対して引き続き実行できるように、LOCAL_ONLY 引数。  
  
-   **sp_rda_reauthorize_db**  
  
     実行すると[sys.sp_rda_reauthorize_db &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)リモート Azure データベースに再接続すると、この操作が自動的にリセットされたクエリ モード LOCAL_AND_REMOTE で、既定の動作のを Stretch Database。 つまり、クエリは、ローカルとリモートの両方のデータから結果を返します。  
  
## <a name="see-also"></a>参照  
 [sys.sp_rda_deauthorize_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  

---
title: sys.sp_rda_set_query_mode (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_query_mode
- sys.sp_rda_set_query_mode_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_query_mode stored procedure
ms.assetid: 65a0b390-cf87-4db7-972a-1fdf13456c88
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 75040d59b21772d4089fce38074ff22895937e48
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="syssprdasetquerymode-transact-sql"></a>sys.sp_rda_set_query_mode (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  現在の Stretch 対応データベースとそのテーブルに対するクエリが、ローカルとリモートの両方のデータ (既定)、またはローカル データだけを返すかどうかを指定します。  
  
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
  
-   **LOCAL_ONLY** Stretch 対応テーブルに対するクエリは、ローカル データだけを返します。  
  
-   **LOCAL_AND_REMOTE** Stretch 対応テーブルに対するクエリは、ローカルおよびリモートの両方のデータを返します。 これは既定の動作です。  
  
 [ @force = ]  *@force*  
 検証を伴わないクエリ モードを変更する場合は、1 に設定できるオプションのビット値です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または >0 (失敗)  
  
## <a name="permissions"></a>権限  
 Db_owner アクセス許可が必要です。  
  
## <a name="remarks"></a>解説  
 次の拡張ストアド プロシージャでは、Stretch 対応データベースのクエリ モードも設定します。  
  
-   **sp_rda_deauthorize_db**  
  
     実行した後**sp_rda_deauthorize_db** 、Stretch 対応データベースとテーブルに対するすべてのクエリは失敗します。 つまり、クエリ モードは無効に設定します。 このモードを終了するには、するには、次のいずれかの操作を行います。  
  
    -   実行[sys.sp_rda_reauthorize_db &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)リモート Azure データベースに再接続します。 この操作に自動的にリセット クエリ モード LOCAL_AND_REMOTE、Stretch Database の既定の動作はします。 つまり、クエリは、ローカルおよびリモートの両方のデータから結果を返します。  
  
    -   実行[sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) LOCAL_ONLY の引数にローカル データだけに対して実行する継続クエリできるようにします。  
  
-   **sp_rda_reauthorize_db**  
  
     実行すると[sys.sp_rda_reauthorize_db &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)再接続するには、リモート Azure データベースにこの操作が自動的にリセット クエリ モード LOCAL_AND_REMOTE に Stretch Database の既定の動作です。 つまり、クエリは、ローカルおよびリモートの両方のデータから結果を返します。  
  
## <a name="see-also"></a>参照  
 [sys.sp_rda_deauthorize_db &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-rda-deauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  

---
title: sys.sp_rda_deauthorize_db (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_deauthorize_db
- sys.sp_rda_deauthorize_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_deauthorize_db stored procedure
ms.assetid: 2e362e15-2cd5-4856-9f0b-54df56b0866b
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 70aea0297b20a9862a8e55dc2f73b19852f6a59f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="syssprdadeauthorizedb-transact-sql"></a>sys.sp_rda_deauthorize_db (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  ローカルの Stretch 対応データベースとリモート Azure データベース間で認証された接続を削除します。 実行**sp_rda_deauthorize_db**ときに、リモート データベースは到達できないか、不整合な状態にし、データベース内のすべての Stretch 対応テーブルに対するクエリの動作を変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_rda_deauthorize_db   
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または >0 (失敗)  
  
## <a name="permissions"></a>権限  
 Db_owner アクセス許可が必要です。  
  
## <a name="remarks"></a>解説  
 実行した後**sp_rda_deauthorize_db** 、Stretch 対応データベースとテーブルに対するすべてのクエリは失敗します。 つまり、クエリ モードは無効に設定します。 このモードを終了するには、するには、次のいずれかの操作を行います。  
  
-   実行[sys.sp_rda_reauthorize_db &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)リモート Azure データベースに再接続します。 この操作に自動的にリセット クエリ モード LOCAL_AND_REMOTE、Stretch Database の既定の動作はします。 つまり、クエリは、ローカルおよびリモートの両方のデータから結果を返します。  
  
-   実行[sys.sp_rda_set_query_mode &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md) 、LOCAL_ONLY の引数にローカル データだけに対して実行する継続クエリできるようにします。  
  
## <a name="see-also"></a>参照  
 [sys.sp_rda_set_query_mode &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md)   
 [sys.sp_rda_reauthorize_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md)   
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  

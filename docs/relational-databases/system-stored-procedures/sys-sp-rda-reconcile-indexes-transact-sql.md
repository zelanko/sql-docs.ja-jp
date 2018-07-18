---
title: sys.sp_rda_reconcile_indexes (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_rda_reconcile_indexes
- sp_rda_reconcile_indexes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_indexes stored procedure
ms.assetid: 96b31ab9-bf84-46d6-9990-81f5c51f885a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ff2352fde5124f1f0db140914799f2a6d75f88d8
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37431921"
---
# <a name="syssprdareconcileindexes-transact-sql"></a>sys.sp_rda_reconcile_indexes (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  リモート テーブルのインデックスを調整するために、スキーマに関するタスク キューに入れます。 このタスクが正常に完了した後、リモートのテーブルは、ローカルの拡張が有効なテーブルに存在するのと同じインデックスにあります。  
  
 呼び出すときにインデックスを調整する別のタスクがキューに存在する場合**sp_rda_reconcile_indexes**、重複するタスクがこのストアド プロシージャをキューに登録します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_rda_reconcile_indexes [@objname = ] 'objname'  
  
```  
  
## <a name="arguments"></a>引数  
 [@objname =] *'objname'*  
 インデックスを調整する、拡張が有効なテーブルの修飾名または非修飾の名前です。 修飾されたオブジェクトを指定する場合にのみ、引用符が必要です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または >0 (失敗)  
  
## <a name="see-also"></a>参照  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  

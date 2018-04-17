---
title: sp_cursorclose (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_close_TSQL
- sp_cursor_close
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorclose
ms.assetid: d9b7b44d-cdff-456e-97df-7031a3b9beb6
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1053cf5b483f2bce87c103bd1ad44fee3bae0455
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spcursorclose-transact-sql"></a>sp_cursorclose (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  閉じると、カーソルの割り当てを解除だけでなく関連付けられているすべてのリソースを解放つまり、KEYSET または STATIC をサポートするために使用する一時テーブルを削除**カーソル**です。 sp_cursorclose は、ID を指定して呼び出される、表形式のデータ ストリーム (TDS) パケットで 9 を = です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cursorclose cursor  
```  
  
## <a name="arguments"></a>引数  
 *カーソル (cursor)*  
 カーソル*処理*によって生成される値[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]され、sp_cursoropen プロシージャから返されます。 *カーソル*必須パラメーターですが、 **int**値を入力します。  
  
> [!NOTE]  
>  入力値を -1 にすると、現在の接続のすべてのカーソルに適用されます。  
  
## <a name="remarks"></a>解説  
 *カーソル*カーソルが閉じられた後、プロシージャが実行された場合、または無効なハンドルが指定されている場合、エラー メッセージが返されます。  
  
 RPC のステータスでは、プロシージャ全体が成功したか失敗したかが示されます。  
  
 DONE の行数は常に 0 になります。  
  
## <a name="see-also"></a>参照  
 [sp_cursoropen &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

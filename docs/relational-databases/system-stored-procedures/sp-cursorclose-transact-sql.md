---
title: sp_cursorclose (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b1556ebbfd0f5e01cfccae734036122360e68944
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022008"
---
# <a name="spcursorclose-transact-sql"></a>sp_cursorclose (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  閉じると、カーソルの割り当てを解除だけでなく関連付けられているリソースをすべて解放つまり、KEYSET または STATIC のサポートに使用される一時テーブルを削除**カーソル**します。 sp_cursorclose は、ID を指定して呼び出される、表形式のデータ ストリーム (TDS) パケットで 9 を = です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cursorclose cursor  
```  
  
## <a name="arguments"></a>引数  
 *カーソル (cursor)*  
 カーソル*処理*によって生成される値[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]され、sp_cursoropen プロシージャから返されます。 *カーソル*が必要なパラメーターです、 **int**値を入力します。  
  
> [!NOTE]  
>  入力値を -1 にすると、現在の接続のすべてのカーソルに適用されます。  
  
## <a name="remarks"></a>コメント  
 *カーソル*カーソルが閉じられた後、プロシージャが実行された場合、または無効なハンドルが指定されている場合、エラー メッセージが返されます。  
  
 RPC のステータスでは、プロシージャ全体が成功したか失敗したかが示されます。  
  
 DONE の行数は常に 0 になります。  
  
## <a name="see-also"></a>参照  
 [sp_cursoropen &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

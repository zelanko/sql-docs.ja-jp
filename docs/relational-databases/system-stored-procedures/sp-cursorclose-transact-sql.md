---
title: sp_cursorclose (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_close_TSQL
- sp_cursor_close
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorclose
ms.assetid: d9b7b44d-cdff-456e-97df-7031a3b9beb6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f21e6db8e9c1cb8ec33f9bddd9610d8179b3e5ac
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820616"
---
# <a name="sp_cursorclose-transact-sql"></a>sp_cursorclose (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  カーソルを閉じて割り当てを解除するだけでなく、関連付けられているすべてのリソースを解放します。つまり、キーセットまたは静的**カーソル**をサポートするために使用される一時テーブルが削除されます。 sp_cursorclose は、ID = 9 を指定した場合に表形式のデータストリーム (TDS) パケットで呼び出されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cursorclose cursor  
```  
  
## <a name="arguments"></a>引数  
 *cursor*  
 によって*handle*生成され、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_cursoropen プロシージャによって返されるカーソルハンドル値です。 *cursor*は、 **int**入力値を必要とする必須パラメーターです。  
  
> [!NOTE]  
>  入力値-1 は、現在の接続のすべてのカーソルに適用されます。  
  
## <a name="remarks"></a>解説  
 カーソルが閉じられた後にプロシージャが実行された場合、または無効なハンドルが指定されている場合は、*カーソル*によってエラーメッセージが返されます。  
  
 RPC の状態は、全体の成功または失敗を示します。  
  
 DONE rowcount は常に0です。  
  
## <a name="see-also"></a>参照  
 [sp_cursoropen &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

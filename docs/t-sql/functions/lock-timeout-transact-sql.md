---
title: "@@LOCK_TIMEOUT (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@LOCK_TIMEOUT'
- '@@LOCK_TIMEOUT_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- timeout options [SQL Server], locks
- '@@LOCK_TIMEOUT function'
- current lock time-out setting
- locking [SQL Server], time-outs
ms.assetid: 6bf8bf97-60b8-40c1-b89d-8f5a00bcae2e
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 15ee9c5789ea6f1c7bbad6fc8caeabab14f3df4f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="locktimeout-transact-sql"></a>@@LOCK_TIMEOUT (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のセッションの現在のロック タイムアウト設定をミリ秒単位で返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
@@LOCK_TIMEOUT  
```  
  
## <a name="return-types"></a>戻り値の型  
 **整数 (integer)**  
  
## <a name="remarks"></a>解説  
 SET LOCK_TIMEOUT を使用して、使用されないようにブロックされているリソースが使用できるようになるまでのステートメントの最大待ち時間を設定できます。 待ち時間が LOCK_TIMEOUT の設定を超える場合、ブロックされているステートメントは自動的に取り消され、エラー メッセージがアプリケーションに返されます。  
  
 @@LOCK_TIMEOUT SET LOCK_TIMEOUT が現在のセッションで実行されていない場合、値は-1 を返します。  
  
## <a name="examples"></a>使用例  
 この例では、LOCK_TIMEOUT 値が設定されていない場合の結果セットを表示します。  
  
```  
SELECT @@LOCK_TIMEOUT AS [Lock Timeout];  
GO  
```  
  
 Here is the result set:  
  
```  
Lock Timeout  
------------  
-1  
```  
  
 この例は、LOCK_TIMEOUT を 1,800 ミリ秒に設定し、を呼び出して@LOCK_TIMEOUTです。  
  
```  
SET LOCK_TIMEOUT 1800;  
SELECT @@LOCK_TIMEOUT AS [Lock Timeout];  
GO  
```  
  
 Here is the result set:  
  
```  
Lock Timeout  
------------  
1800          
```  
  
## <a name="see-also"></a>参照  
 [構成関数 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [[SET LOCK_TIMEOUT] & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-lock-timeout-transact-sql.md)  
  
  

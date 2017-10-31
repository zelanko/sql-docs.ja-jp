---
title: "@@FETCH_STATUS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@FETCH_STATUS'
- '@@FETCH_STATUS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- FETCH statement
- status information [SQL Server], FETCH
- '@@FETCH_STATUS function'
ms.assetid: 93659193-e4ff-4dfb-9043-0c4114921b91
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 61e209f7cf2a3a654b33979129e9500d3734fe64
ms.contentlocale: ja-jp
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40fetchstatus-transact-sql"></a>& #x 40; & #x 40 です。FETCH_STATUS (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  接続によって現在オープンされているカーソルに対して最後に実行した FETCH ステートメントの状態を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
@@FETCH_STATUS  
```  
  
## <a name="return-type"></a>戻り値の型  
 **整数 (integer)**  
  
## <a name="return-value"></a>戻り値  
  
|戻り値|Description|  
|------------------|-----------------|  
|0|FETCH ステートメントは正常に実行されました。|  
|-1|FETCH ステートメントが失敗したか、または行が結果セットに収まりません。|  
|-2|取り出した行がありません。|
|-9|カーソルがフェッチ操作を実行しません。|  
  
## <a name="remarks"></a>解説  
 @@FETCH_STATUS接続に、すべてのカーソルに対してグローバルなを使用して@FETCH_STATUS慎重にします。 FETCH ステートメントが実行された後に @ テスト@FETCH_STATUS他の FETCH ステートメントが別のカーソルに対して実行される前に行う必要があります。 値を @@FETCH_STATUSフェッチが接続で実行する前に、定義されていません。  
  
 たとえば、ユーザーがあるカーソルからの FETCH ステートメントを実行します。次に、別のカーソルからの結果を開いて処理するためのストアド プロシージャを呼び出します。 コントロールが返される場合、呼び出されたストアド プロシージャから@FETCH_STATUSストアド プロシージャを呼び出す前に実行された FETCH ステートメントではない、ストアド プロシージャで最後にフェッチが反映されます。  
  
 特定のカーソルの最後のフェッチの状態を取得するクエリ、 **fetch_status**の列、 **sys.dm_exec_cursors**動的管理関数です。  
  
## <a name="examples"></a>使用例  
 次の例では、`@@FETCH_STATUS` を使用して `WHILE` ループ内のカーソルの動作を制御します。  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT BusinessEntityID, JobTitle  
FROM AdventureWorks2012.HumanResources.Employee;  
OPEN Employee_Cursor;  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
   BEGIN  
      FETCH NEXT FROM Employee_Cursor;  
   END;  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [カーソル関数 &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-functions-transact-sql.md)   
 [フェッチ & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/fetch-transact-sql.md)  
  
  


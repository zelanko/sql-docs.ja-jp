---
title: "閉じる (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLOSE_TSQL
- CLOSE
dev_langs: TSQL
helpviewer_keywords:
- closing cursors
- cursors [SQL Server], closing
- CLOSE statement
ms.assetid: 21546874-97e3-4b93-970f-87c27f6b78c7
caps.latest.revision: "32"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d056ab67537c6b0646f58242bc8d3d7ab445f73f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="close-transact-sql"></a>CLOSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在の結果セットを解放し、カーソルが置かれている行に設定されているカーソル ロックを解除して、開いているカーソルを閉じます。 CLOSE では、再度開けるようにデータ構造がアクセス可能なままになりますが、フェッチや位置指定更新は、カーソルを再度開くまで実行できません。 CLOSE は開いているカーソル上で実行する必要があります。宣言されただけのカーソルや、既に閉じているカーソルでは実行できません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CLOSE { { [ GLOBAL ] cursor_name } | cursor_variable_name }  
```  
  
## <a name="arguments"></a>引数  
 GLOBAL  
 指定する*cursor_name*はグローバル カーソルを参照します。  
  
 *cursor_name*  
 開いているカーソルの名前です。 グローバルとローカル カーソルの両方に存在しない場合*cursor_name* 、名前として*cursor_name*グローバル カーソルと GLOBAL が指定されている、それ以外の場合は*cursor_name*ローカル カーソルを参照します。  
  
 *cursor_variable_name*  
 開いているカーソルに関連付けられたカーソル変数の名前です。  
  
## <a name="examples"></a>使用例  
 次の例では、カーソルを使用した処理での `CLOSE` ステートメントの正しい位置を示しています。  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT EmployeeID, Title FROM AdventureWorks2012.HumanResources.Employee;  
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
 [カーソル](../../relational-databases/cursors.md)   
 [カーソル &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DEALLOCATE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [フェッチ &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/fetch-transact-sql.md)   
 [開く &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/open-transact-sql.md)  
  
  

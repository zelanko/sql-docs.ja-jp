---
title: "開く (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- OPEN_TSQL
- OPEN
dev_langs: TSQL
helpviewer_keywords:
- opening cursors
- cursors [SQL Server], opening
- populating cursors [SQL Server]
- OPEN statement
- Transact-SQL cursors, opening
ms.assetid: fd1c5e3b-6045-4a42-b646-3fca76e874c1
caps.latest.revision: "36"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 92ba2ddafe591c570300918bfb968ae44debea62
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="open-transact-sql"></a>OPEN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  開きます、[!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー カーソルを実行して、カーソルを作成し、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントで DECLARE CURSOR または SET 指定*cursor_variable*ステートメントです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
OPEN { { [ GLOBAL ] cursor_name } | cursor_variable_name }  
```  
  
## <a name="arguments"></a>引数  
 GLOBAL  
 指定する*cursor_name*はグローバル カーソルを参照します。  
  
 *cursor_name*  
 宣言済みのカーソルの名前を指定します。 グローバルとローカル カーソルの両方に存在しない場合*cursor_name* 、名前として*cursor_name* GLOBAL が指定された、それ以外の場合、グローバル カーソル参照*cursor_name*ローカル カーソルを参照します。  
  
 *cursor_variable_name*  
 カーソルを参照するカーソル変数の名前を指定します。  
  
## <a name="remarks"></a>解説  
 INSENSITIVE または STATIC オプションと共にカーソルが宣言されている場合、OPEN を実行すると結果セットを格納する一時テーブルが作成されます。 結果セットの任意の行のサイズが最大行サイズを超える OPEN は失敗[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 KEYSET オプションと共にカーソルが宣言されている場合、OPEN を実行するとキーセットを格納する一時テーブルが作成されます。 一時テーブルは tempdb に格納されます。  
  
 カーソルを開いた後を使用して、@@CURSOR_ROWS条件を満たすの数を受け取る関数の行では、最後に開かれたカーソル。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、キーセット ドリブン カーソルまたは静的 [!INCLUDE[tsql](../../includes/tsql-md.md)] カーソルの非同期な作成はサポートされません。 [!INCLUDE[tsql](../../includes/tsql-md.md)] カーソル操作はバッチで行われます。したがって、 [!INCLUDE[tsql](../../includes/tsql-md.md)] カーソルを非同期に生成する必要はありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 各カーソル操作におけるクライアントのラウンド トリップのため、待機時間が少ない OPEN が問題になるような非同期キーセット ドリブン カーソルまたは静的 API (アプリケーション プログラミング インターフェイス) サーバー カーソルは、 で引き続きサポートされます。  
  
## <a name="examples"></a>使用例  
 次の例では、カーソルをオープンし、すべての行をフェッチします。  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT LastName, FirstName  
FROM AdventureWorks2012.HumanResources.vEmployee  
WHERE LastName like 'B%';  
  
OPEN Employee_Cursor;  
  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
BEGIN  
    FETCH NEXT FROM Employee_Cursor  
END;  
  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
```  
  
## <a name="see-also"></a>参照  
 [閉じる &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/close-transact-sql.md)   
 [@@CURSOR_ROWS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-rows-transact-sql.md)   
 [DEALLOCATE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [フェッチ &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/fetch-transact-sql.md)  
  
  

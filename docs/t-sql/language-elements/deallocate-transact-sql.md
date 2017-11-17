---
title: "(TRANSACT-SQL) の割り当てを解除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DEALLOCATE
- DEALLOCATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], cursors
- DEALLOCATE statement
- deallocations [SQL Server]
- deleting cursor references
- removing cursor references
ms.assetid: c75cf73d-0268-4c57-973d-b8a84ff801fa
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: cedd8bd32c076a5732586653d11276bcfb880bd9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deallocate-transact-sql"></a>DEALLOCATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  カーソル参照を削除します。 によって、カーソルを構成するデータ構造がリリースされたとき、カーソルの最後の参照を解放し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DEALLOCATE { { [ GLOBAL ] cursor_name } | @cursor_variable_name }  
```  
  
## <a name="arguments"></a>引数  
 *cursor_name*  
 宣言済みのカーソル名を指定します。 かどうか、グローバルとローカル カーソルの両方存在で*cursor_name* 、名前として*cursor_name* GLOBAL が指定されていない場合、GLOBAL が指定されている場合は、グローバル カーソルとローカル カーソルを参照します。  
  
 @*cursor_variable_name*  
 名前を指定、**カーソル**変数。 @*cursor_variable_name*型でなければなりません**カーソル**です。  
  
## <a name="remarks"></a>解説  
 カーソルを操作するステートメントでは、カーソル名またはカーソル変数を使用してカーソルを参照します。 DEALLOCATE を実行すると、カーソルと、カーソル名またはカーソル変数との間の関係が削除されます。 名前または変数がカーソルを参照する最後のものである場合は、カーソルの割り当てが解除され、カーソルが使用しているリソースが解放されます。 フェッチの孤立を防ぐために使用するスクロール ロックは、DEALLOCATE で解放されます。 カーソルを介して行われる位置指定更新を含め、更新を保護するために使用するトランザクション ロックは、トランザクションの終了時まで保持されます。  
  
 DECLARE CURSOR ステートメントでは、カーソルを割り当て、カーソル名と関連付けます。  
  
```  
DECLARE abc SCROLL CURSOR FOR  
SELECT * FROM Person.Person;  
```  
  
 カーソルにカーソル名が割り当てられると、このカーソルの割り当てが解除されるまで、その名前を同じ範囲 (GLOBAL または LOCAL) の別のカーソルに対して使用することはできません。  
  
 カーソル変数は、次のいずれかの方法でカーソルに関連付けられます。  
  
-   カーソルをカーソル変数に設定する SET ステートメントを使用して、名前を指定する。  
  
    ```  
    DECLARE @MyCrsrRef CURSOR;  
    SET @MyCrsrRef = abc;  
    ```  
  
-   カーソル名を定義せずにカーソルを作成し、変数に関連付ける。  
  
    ```  
    DECLARE @MyCursor CURSOR;  
    SET @MyCursor = CURSOR LOCAL SCROLL FOR  
    SELECT * FROM Person.Person;  
    ```  
  
 DEALLOCATE @*cursor_variable_name*ステートメントがカーソルに名前付きの変数の参照のみを削除します。 変数の割り当ては、バッチ、ストアド プロシージャ、またはトリガーの終了時にその有効範囲が失われるまで、解除されることはありません。 DEALLOCATE @ 後*cursor_variable_name*ステートメントでは、変数に関連付けられる、SET ステートメントを使用して別のカーソル。  
  
```  
USE AdventureWorks2012;  
GO  
  
DECLARE @MyCursor CURSOR;  
SET @MyCursor = CURSOR LOCAL SCROLL FOR  
    SELECT * FROM Sales.SalesPerson;  
  
DEALLOCATE @MyCursor;  
  
SET @MyCursor = CURSOR LOCAL SCROLL FOR  
    SELECT * FROM Sales.SalesTerritory;  
GO  
```  
  
 カーソル変数は、明示的に割り当てを解除する必要はありません。 変数は、有効範囲を失うと暗黙的に割り当てが解除されます。  
  
## <a name="permissions"></a>Permissions  
 DEALLOCATE 権限は、既定では、有効なユーザーであればどのユーザーにも与えられます。  
  
## <a name="examples"></a>使用例  
 次の例では、最後の名前まで、またはカーソルを参照している変数の割り当てが解除されるまで、カーソルが保持されます。  
  
```  
USE AdventureWorks2012;  
GO  
-- Create and open a global named cursor that  
-- is visible outside the batch.  
DECLARE abc CURSOR GLOBAL SCROLL FOR  
    SELECT * FROM Sales.SalesPerson;  
OPEN abc;  
GO  
-- Reference the named cursor with a cursor variable.  
DECLARE @MyCrsrRef1 CURSOR;  
SET @MyCrsrRef1 = abc;  
-- Now deallocate the cursor reference.  
DEALLOCATE @MyCrsrRef1;  
-- Cursor abc still exists.  
FETCH NEXT FROM abc;  
GO  
-- Reference the named cursor again.  
DECLARE @MyCrsrRef2 CURSOR;  
SET @MyCrsrRef2 = abc;  
-- Now deallocate cursor name abc.  
DEALLOCATE abc;  
-- Cursor still exists, referenced by @MyCrsrRef2.  
FETCH NEXT FROM @MyCrsrRef2;  
-- Cursor finally is deallocated when last referencing  
-- variable goes out of scope at the end of the batch.  
GO  
-- Create an unnamed cursor.  
DECLARE @MyCursor CURSOR;  
SET @MyCursor = CURSOR LOCAL SCROLL FOR  
SELECT * FROM Sales.SalesTerritory;  
-- The following statement deallocates the cursor  
-- because no other variables reference it.  
DEALLOCATE @MyCursor;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [閉じる & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/close-transact-sql.md)   
 [カーソル](../../relational-databases/cursors.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [フェッチ & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/fetch-transact-sql.md)   
 [開く & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/open-transact-sql.md)  
  
  


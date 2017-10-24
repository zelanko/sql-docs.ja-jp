---
title: "フェッチ (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FETCH
- FETCH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FETCH statement
- cursors [SQL Server], fetching
- Transact-SQL cursors, fetching and scrolling
- retrieving rows
- fetching [SQL Server]
- SCROLL option
- row fetching [SQL Server]
ms.assetid: 5d68dac2-f91b-4342-bb4e-209ee132665f
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1333af6ceba4a4410fefadd1a99d8611fae88a6a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="fetch-transact-sql"></a>FETCH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[tsql](../../includes/tsql-md.md)] サーバー カーソルから特定の行を取得します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
FETCH   
          [ [ NEXT | PRIOR | FIRST | LAST   
                    | ABSOLUTE { n | @nvar }   
                    | RELATIVE { n | @nvar }   
               ]   
               FROM   
          ]   
{ { [ GLOBAL ] cursor_name } | @cursor_variable_name }   
[ INTO @variable_name [ ,...n ] ]   
```  
  
## <a name="arguments"></a>引数  
 NEXT  
 現在の行の直後にある行を結果行として返し、この返した行に現在の行を加えます。 カーソルに対する最初のフェッチが FETCH NEXT の場合、結果セットの中の先頭の行が返ります。 NEXT は、カーソル フェッチの既定のオプションです。  
  
 PRIOR  
 現在の行の直前にある行を結果行として返し、現在の行を減らして、この返した行にします。 カーソルに対する最初のフェッチが FETCH PRIOR の場合、行は返されません。カーソルは先頭行の前に位置したままです。  
  
 FIRST  
 カーソル内の先頭行を返し、これを現在の行にします。  
  
 LAST  
 カーソル内の最終行を返し、これを現在の行にします。  
  
 絶対 {  *n* | @*nvar*}  
 場合 *n* または @*nvar*が正の値、行を返します *n* カーソルの先頭からの行し、新しい現在の行を返し、返した行です。 場合 *n* または @*nvar*負の場合、行を返します *n* カーソルの終端する前に行の行を新しい現在の行を返し、返した行です。 場合 *n* または @*nvar*は 0、行は返されません。 *n*整数定数でなければなりませんおよび @*nvar*する必要があります**smallint**、 **tinyint**、または**int**です。  
  
 相対 {  *n* | @*nvar*}  
 場合 *n* または @*nvar*が正の値、行を返します *n* 現在の行を超えるし、新しい現在の行を返し、返した行です。 場合 *n* または @*nvar*負の場合、行を返します *n* 行の現在の行の前に、新しい現在の行を返し、返した行です。 場合 *n* または @*nvar*が 0 の場合、現在の行を返します。 FETCH RELATIVE を指定した場合に *n* または @*nvar*負の値またはカーソルに対して実行する最初のフェッチで 0 に設定すると、行は返されません。 *n*整数定数でなければなりませんおよび @*nvar*する必要があります**smallint**、 **tinyint**、または**int**です。  
  
 GLOBAL  
 指定する*cursor_name*はグローバル カーソルを参照します。  
  
 *cursor_name*  
 フェッチが行われる、開いているカーソルの名前です。 かどうか、グローバルとローカル カーソルの両方存在で*cursor_name* 、名前として*cursor_name* GLOBAL が指定されている場合は、グローバル カーソルと GLOBAL が指定されていない場合は、ローカル カーソルをします。  
  
 @*cursor_variable_name*  
 フェッチが行われる、開いているカーソルを参照するカーソル変数の名前です。  
  
 INTO @*variable_name*[,...*n*]  
 フェッチの列で得られたデータを、ローカル変数に設定します。 リスト内の各変数は、左から右に向かって、カーソル結果セット内の対応する列に関連付けられます。 各変数のデータ型は、対応する結果セット列のデータ型に一致するか、または暗黙的な型変換がサポートされていなければなりません。 変数の個数は、カーソル選択リスト内の列の個数と一致している必要があります。  
  
## <a name="remarks"></a>解説  
 ISO 形式の DECLARE CURSOR ステートメントに SCROLL オプションが指定されていない場合、サポートされる FETCH オプションは NEXT だけです。 ISO 形式の DECLARE CURSOR ステートメントに SCROLL が指定されている場合は、すべての FETCH オプションがサポートされます。  
  
 ときに、 [!INCLUDE[tsql](../../includes/tsql-md.md)] DECLARE カーソル拡張機能を使用する、これらの規則が適用されます。  
  
-   FORWARD_ONLY と FAST_FORWARD のいずれかが指定されている場合、サポートされる FETCH オプションは NEXT だけです。  
  
-   DYNAMIC、FORWARD_ONLY、FAST_FORWARD のいずれも指定されておらず、かつ KEYSET、STATIC、SCROLL のいずれか 1 つが指定されている場合は、すべての FETCH オプションがサポートされます。  
  
-   DYNAMIC SCROLL カーソルは、ABSOLUTE 以外のすべての FETCH オプションをサポートします。  
  
 @@FETCH_STATUS関数が最後にフェッチ ステートメントの状態を報告します。 sp_describe_cursor で返されるカーソル内の fetch_status 列に、同じ情報が記録されます。 FETCH ステートメントで返されたデータに対して操作を行う前に、このステータス情報を使用してデータの妥当性を判断する必要があります。 詳細については、次を参照してください。 [@@FETCH_STATUS & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/fetch-status-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 FETCH 権限は、特に指定のない限り有効なすべてのユーザーに与えられます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-fetch-in-a-simple-cursor"></a>A. 単純カーソル内での FETCH を使用する  
 次の例は、単純カーソル内の行を宣言、`Person.Person`で始まる姓を持つテーブル`B`を使用して`FETCH NEXT`行をステップ実行します。 `FETCH` ステートメントは、`DECLARE CURSOR` の中で指定された列の値を、単一行の結果セットとして返します。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE contact_cursor CURSOR FOR  
SELECT LastName FROM Person.Person  
WHERE LastName LIKE 'B%'  
ORDER BY LastName;  
  
OPEN contact_cursor;  
  
-- Perform the first fetch.  
FETCH NEXT FROM contact_cursor;  
  
-- Check @@FETCH_STATUS to see if there are any more rows to fetch.  
WHILE @@FETCH_STATUS = 0  
BEGIN  
   -- This is executed as long as the previous fetch succeeds.  
   FETCH NEXT FROM contact_cursor;  
END  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
### <a name="b-using-fetch-to-store-values-in-variables"></a>B. FETCH を使用して変数に値を格納する  
 次の例は例 A で、出力のような`FETCH`ステートメントが直接クライアントに返されるのではなく、ローカル変数に格納します。 `PRINT` ステートメントは変数を 1 つの文字列に結合し、これをクライアントに返します。  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare the variables to store the values returned by FETCH.  
DECLARE @LastName varchar(50), @FirstName varchar(50);  
  
DECLARE contact_cursor CURSOR FOR  
SELECT LastName, FirstName FROM Person.Person  
WHERE LastName LIKE 'B%'  
ORDER BY LastName, FirstName;  
  
OPEN contact_cursor;  
  
-- Perform the first fetch and store the values in variables.  
-- Note: The variables are in the same order as the columns  
-- in the SELECT statement.   
  
FETCH NEXT FROM contact_cursor  
INTO @LastName, @FirstName;  
  
-- Check @@FETCH_STATUS to see if there are any more rows to fetch.  
WHILE @@FETCH_STATUS = 0  
BEGIN  
  
   -- Concatenate and display the current values in the variables.  
   PRINT 'Contact Name: ' + @FirstName + ' ' +  @LastName  
  
   -- This is executed as long as the previous fetch succeeds.  
   FETCH NEXT FROM contact_cursor  
   INTO @LastName, @FirstName;  
END  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
### <a name="c-declaring-a-scroll-cursor-and-using-the-other-fetch-options"></a>C. SCROLL カーソルを宣言し、他の FETCH オプションを使用する  
 次の例では、`SCROLL` カーソルを作成し、`LAST`、`PRIOR`、`RELATIVE`、および `ABSOLUTE` オプションを介してすべてのスクロール機能を使用します。  
  
```  
USE AdventureWorks2012;  
GO  
-- Execute the SELECT statement alone to show the   
-- full result set that is used by the cursor.  
SELECT LastName, FirstName FROM Person.Person  
ORDER BY LastName, FirstName;  
  
-- Declare the cursor.  
DECLARE contact_cursor SCROLL CURSOR FOR  
SELECT LastName, FirstName FROM Person.Person  
ORDER BY LastName, FirstName;  
  
OPEN contact_cursor;  
  
-- Fetch the last row in the cursor.  
FETCH LAST FROM contact_cursor;  
  
-- Fetch the row immediately prior to the current row in the cursor.  
FETCH PRIOR FROM contact_cursor;  
  
-- Fetch the second row in the cursor.  
FETCH ABSOLUTE 2 FROM contact_cursor;  
  
-- Fetch the row that is three rows after the current row.  
FETCH RELATIVE 3 FROM contact_cursor;  
  
-- Fetch the row that is two rows prior to the current row.  
FETCH RELATIVE -2 FROM contact_cursor;  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [閉じる & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/close-transact-sql.md)   
 [DEALLOCATE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [開く & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/open-transact-sql.md)  
  
  


---
title: sp_describe_cursor (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
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
- sp_describe_cursor
- sp_describe_cursor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_cursor
ms.assetid: 0c836c99-1147-441e-998c-f0a30cd05275
caps.latest.revision: 22
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a9d4810ed2894f1bcb4df116b9b62e64a475b48d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spdescribecursor-transact-sql"></a>sp_describe_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー カーソルの属性をレポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_describe_cursor [ @cursor_return = ] output_cursor_variable OUTPUT   
     { [ , [ @cursor_source = ] N'local'  
    , [ @cursor_identity = ] N'local_cursor_name' ]   
   | [ , [ @cursor_source = ] N'global'  
    , [ @cursor_identity = ] N'global_cursor_name' ]   
   | [ , [ @cursor_source = ] N'variable'  
     , [ @cursor_identity = ] N'input_cursor_variable' ]   
     }   
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ @cursor_return=] *output_cursor_variable*出力  
 カーソル出力を受け取るように宣言したカーソル変数の名前です。 *output_cursor_variable*は**カーソル**, ない必要があり、既定をどのカーソルに関連付けられた時にできない、sp_describe_cursor が呼び出されます。 スクロール可能で動的な読み取り専用カーソルが返されます。  
  
 [ @cursor_source=] {N'local' |N'global' |N'variable'}  
 レポート対象のカーソルをローカル カーソル、グローバル カーソル、カーソル変数のどの名前で指定するのかを指定します。 パラメーターが**nvarchar (30)** です。  
  
 [ @cursor_identity=] N'*local_cursor_name*']  
 LOCAL キーワードを指定した DECLARE CURSOR ステートメント、または既定値が LOCAL になっている DECLARE CURSOR ステートメントによって作成されたカーソルの名前を指定します。 *local_cursor_name*は**nvarchar (128)** です。  
  
 [ @cursor_identity=] N'*global_cursor_name*']  
 GLOBAL キーワードを指定した DECLARE CURSOR ステートメント、または既定値が GLOBAL になっている DECLARE CURSOR ステートメントによって作成されたカーソルの名前を指定します。 *global_cursor_name*は**nvarchar (128)** です。  
  
 *global_cursor_name*が指定する ODBC アプリケーションによって開かれた API サーバー カーソルの名前を指定できますも SQLSetCursorName を呼び出すことによってです。  
  
 [ @cursor_identity=] N'*input_cursor_variable*']  
 開いているカーソルに関連付けられたカーソル変数の名前です。 *input_cursor_variable*は**nvarchar (128)** です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="cursors-returned"></a>返されるカーソル  
 sp_describe_cursor は、その結果セットをカプセル化、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **カーソル**出力パラメーターです。 これにより、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ、ストアド プロシージャ、およびトリガーを一度に 1 行の出力を使用します。 つまり、プロシージャは、データベース API 関数から直接呼び出すことができません。 **カーソル**出力パラメーターは、プログラム変数にバインドする必要がありますが、データベース Api は、バインディングをサポートしていない**カーソル**パラメーターまたは変数です。  
  
 次の表に、sp_describe_cursor が返すカーソルの形式を示します。 カーソルの形式は、sp_cursor_list を使用した場合に返される形式と同じです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|reference_name|**sysname**|カーソルを参照するために使用される名前です。 DECLARE CURSOR ステートメントに指定された名前を介してカーソルを参照すると、参照名はカーソル名と同じになります。 変数を使用してカーソルを参照した場合、参照名は変数の名前になります。|  
|cursor_name|**sysname**|DECLARE CURSOR ステートメントから、カーソルの名前です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、カーソルがカーソル変数を設定して作成されると、cursor_name にカーソル変数の名前が返されます。 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この出力列がシステムによって生成された名前を返します。|  
|cursor_scope|**tinyint**|1 = LOCAL<br /><br /> 2 = GLOBAL|  
|ステータス|**int**|CURSOR_STATUS システム関数によって報告された、同じ値:<br /><br /> 1 = カーソル名または変数によって参照されたカーソルは開いています。 カーソルが状態非依存、静的、キーセットのいずれかの場合には、結果セットに少なくとも 1 行が含まれます。 カーソルが動的の場合には、結果セットに 0 行以上が含まれます。<br /><br /> 0 = カーソル名または変数によって参照されたカーソルは開いていますが、行は含まれていません。 動的カーソルがこの値を返すことはありません。<br /><br /> -1 = カーソル名または変数によって参照されたカーソルは閉じています。<br /><br /> -2 = カーソル変数にのみ適用されます。 変数に割り当てられたカーソルはありません。 おそらく、OUTPUT パラメーターによってカーソルを変数に割り当てましたが、戻る前にストアド プロシージャがカーソルを閉じました。<br /><br /> -3 = 指定された名前のカーソルまたはカーソル変数が存在しないか、またはカーソル変数にカーソルが割り当てられていません。|  
|model|**tinyint**|1 = 状態非依存 (または静的)<br /><br /> 2 = キーセット<br /><br /> 3 = 動的<br /><br /> 4 = 高速順方向|  
|同時実行 (concurrency)|**tinyint**|1 = 読み取り専用<br /><br /> 2 = スクロール ロック<br /><br /> 3 = オプティミスティック|  
|scrollable|**tinyint**|0 = 順方向専用<br /><br /> 1 = スクロール可能|  
|open_status|**tinyint**|0 = 閉じた状態<br /><br /> 1 = 開いた状態|  
|cursor_rows|**decimal(10,0)**|条件を満たすの結果セットを行数します。 詳細については、「[@@CURSOR_ROWS &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-rows-transact-sql.md)」を参照してください。|  
|fetch_status|**smallint**|このカーソル上での最後のフェッチのステータスです。 詳細については、「[@@FETCH_STATUS &#40;Transact-SQL&#41;](../../t-sql/functions/fetch-status-transact-sql.md)」を参照してください。<br /><br /> 0 = フェッチが成功しました。<br /><br /> -1 = フェッチが失敗したか、またはカーソルの境界を越えています。<br /><br /> -2 = 要求された行がありません。<br /><br /> -9 = カーソル上でフェッチは行われていません。|  
|column_count|**smallint**|カーソル結果セット内の列の数。|  
|row_count|**decimal(10,0)**|カーソルの最後の操作によって影響を受ける行の数。 詳細については、「[@@ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/rowcount-transact-sql.md)」を参照してください。|  
|last_operation|**tinyint**|カーソル上で実行された最後の操作です。<br /><br /> 0 = カーソル上で操作は実行されていません。<br /><br /> 1 = OPEN <br /><br /> 2 = FETCH <br /><br /> 3 = 挿入<br /><br /> 4 = UPDATE <br /><br /> 5 = DELETE<br /><br /> 6 = CLOSE <br /><br /> 7 = DEALLOCATE|  
|cursor_handle|**int**|サーバーの有効範囲内でのカーソルの一意な値です。|  
  
## <a name="remarks"></a>解説  
 sp_describe_cursor は、カーソルがスクロール可能かどうか、更新可能かどうかなど、サーバー カーソルのグローバルな属性を説明します。 カーソルによって返される結果セットの属性の詳細については、sp_describe_cursor_columns を使用します。 カーソルが参照するベース テーブルのレポートが必要な場合は、sp_describe_cursor_tables を使用します。 接続時に可視になる [!INCLUDE[tsql](../../includes/tsql-md.md)] Server カーソルのレポートが必要な場合は、sp_cursor_list を使用します。  
  
 DECLARE CURSOR ステートメントがいない、カーソルの種類を要求することが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]DECLARE CURSOR に含まれている SELECT ステートメントを使用することはできません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カーソルを SELECT ステートメントの使用をサポートできる型に暗黙的に変換します。 DECLARE CURSOR ステートメントで TYPE_WARNING を指定した場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]情報メッセージの変換が完了したことをアプリケーションに送ります。 sp_describe_cursor は、インプリメントされたカーソルの種類を判断し、呼び出すことができます。  
  
## <a name="permissions"></a>権限  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、グローバル カーソルを開き、`sp_describe_cursor` を使用してカーソルの属性をレポートします。  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a global cursor.  
DECLARE abc CURSOR STATIC FOR  
SELECT LastName  
FROM Person.Person;  
  
OPEN abc;  
  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_describe_cursor.  
DECLARE @Report CURSOR;  
  
-- Execute sp_describe_cursor into the cursor variable.  
EXEC master.dbo.sp_describe_cursor @cursor_return = @Report OUTPUT,  
        @cursor_source = N'global', @cursor_identity = N'abc';  
  
-- Fetch all the rows from the sp_describe_cursor output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
    FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_describe_cursor.  
CLOSE @Report;  
DEALLOCATE @Report;  
GO  
  
-- Close and deallocate the original cursor.  
CLOSE abc;  
DEALLOCATE abc;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [カーソル](../../relational-databases/cursors.md)   
 [CURSOR_STATUS &#40;TRANSACT-SQL&#41;](../../t-sql/functions/cursor-status-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [sp_cursor_list &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-list-transact-sql.md)   
 [sp_describe_cursor_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-columns-transact-sql.md)   
 [sp_describe_cursor_tables &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-tables-transact-sql.md)  
  
  

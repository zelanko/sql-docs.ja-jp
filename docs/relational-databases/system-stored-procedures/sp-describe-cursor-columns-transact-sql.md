---
title: "sp_describe_cursor_columns (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_describe_cursor_columns
- sp_describe_cursor_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_cursor_columns
ms.assetid: 6eaa54af-7ba4-4fce-bf6c-6ac67cc1ac94
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2fe882cf908e4ae227a486b68c54d34376164455
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdescribecursorcolumns-transact-sql"></a>sp_describe_cursor_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー カーソルの結果セットにある列の属性をレポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_describe_cursor_columns   
   [ @cursor_return = ] output_cursor_variable OUTPUT   
    { [ , [ @cursor_source = ] N'local' ,   
          [ @cursor_identity = ] N'local_cursor_name' ]   
    | [ , [ @cursor_source = ] N'global' ,   
          [ @cursor_identity = ] N'global_cursor_name' ]   
    | [ , [ @cursor_source = ] N'variable' ,   
          [ @cursor_identity = ] N'input_cursor_variable' ]   
   }  
```  
  
## <a name="arguments"></a>引数  
 [ @cursor_return=] *output_cursor_variable*出力  
 カーソル出力を受け取るように宣言したカーソル変数の名前です。 *output_cursor_variable*は**カーソル**, ない必要があり、既定をどのカーソルに関連付けられた時にできない、sp_describe_cursor_columns が呼び出されます。 スクロール可能で動的な読み取り専用カーソルが返されます。  
  
 [ @cursor_source=] {N'local' |N'global' |N'variable'}  
 レポート対象のカーソルをローカル カーソル、グローバル カーソル、カーソル変数のどの名前で指定するのかを指定します。 パラメーターが**nvarchar (30)**です。  
  
 [ @cursor_identity=] N'*local_cursor_name*'  
 LOCAL キーワードを指定した DECLARE CURSOR ステートメント、または既定値が LOCAL になっている DECLARE CURSOR ステートメントによって作成されたカーソルの名前を指定します。 *local_cursor_name*は**nvarchar (128)**です。  
  
 [ @cursor_identity=] N'*global_cursor_name*'  
 GLOBAL キーワードを指定した DECLARE CURSOR ステートメント、または既定値が GLOBAL になっている DECLARE CURSOR ステートメントによって作成されたカーソルの名前を指定します。 *global_cursor_name*は**nvarchar (128)**です。  
  
 *global_cursor_name*を ODBC アプリケーションによって開かれたは SQLSetCursorName を呼び出すことによって、API サーバー カーソルの名前をすることもできます。  
  
 [ @cursor_identity=] N'*input_cursor_variable*'  
 開いているカーソルに関連付けられたカーソル変数の名前です。 *input_cursor_variable*は**nvarchar (128)**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="cursors-returned"></a>返されるカーソル  
 sp_describe_cursor_columns としてレポートをカプセル化、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **カーソル**出力パラメーターです。 これにより、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ、ストアド プロシージャ、およびトリガーを一度に 1 行の出力を使用します。 つまり、プロシージャは、データベース API 関数から直接呼び出すことができません。 **カーソル**出力パラメーターは、プログラム変数にバインドする必要がありますが、データベース Api は、バインディングをサポートしていない**カーソル**パラメーターまたは変数です。  
  
 次の表に、sp_describe_cursor_columns が返すカーソルの形式を示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|column_name|**sysname** (null 許容の)|結果セット列に割り当てられた名前です。 AS 句なしで列を指定した場合、列は NULL になります。|  
|ordinal_position|**int**|結果セットで左端の列を基準とする列の相対位置です。 最初の列の位置は 0 です。|  
|column_characteristics_flags|**int**|OLE DB の DBCOLUMNFLAGS に格納された情報を示すビットマスクです。 次のいずれか、または組み合わせで示します。<br /><br /> 1 = ブックマーク<br /><br /> 2 = 固定長<br /><br /> 4 = NULL 値を許容<br /><br /> 8 = 行のバージョン管理<br /><br /> 16 = 更新可能な列 (FOR UPDATE 句がないカーソルの射影された列に対して設定されます。このような列がある場合、更新可能な列は各カーソルで 1 つだけです)<br /><br /> ビット値の組み合わせを使用する場合、組み合わされたビット値の特性が適用されます。 たとえば、ビット値が 6 の場合、列は固定長 (2)、NULL 値を許容 (4) です。|  
|column_size|**int**|この列で可能な値の最大サイズです。|  
|data_type_sql|**smallint**|数を示す、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列のデータ型。|  
|column_precision|**tinyint**|1 列の最大有効桁数、 *bPrecision* OLE DB 内の値。|  
|column_scale|**tinyint**|小数点の右側にある数字の数、**数値**または**decimal**としてごとのデータ型、 *bScale* OLE DB 内の値。|  
|order_position|**int**|列が結果セットの順序付けに関係する場合、左端の列を基準とする順序キーでの列の相対位置です。|  
|order_direction|**varchar (1)**(null 許容の)|A = 列は順序キーにあり、順序付けは昇順です。<br /><br /> D = 列は順序キーにあり、順序付けは降順です。<br /><br /> NULL = 列は順序付けに関係しません。|  
|hidden_column|**smallint**|0 = この列は選択リストに表示されます。<br /><br /> 1 = 予約済みです。|  
|columnid|**int**|基になる列の列 ID です。 結果セット列が式で構成されている場合、columnid は -1 です。|  
|objectid|**int**|オブジェクトのオブジェクト ID、または列の値を提供するベース テーブルのオブジェクト ID です。 結果セット列が式で構成されている場合、objectid は -1 です。|  
|dbid|**int**|列の値を提供するベース テーブルを含むデータベースの ID です。 結果セット列が式で構成されている場合、dbid は -1 です。|  
|dbname|**sysname**<br /><br /> (NULL 値を許容)|列の値を提供するベース テーブルを含むデータベースの名前です。 結果セット列が式で構成されている場合、dbname は NULL です。|  
  
## <a name="remarks"></a>解説  
 sp_describe_cursor_columns は、各カーソルの名前やデータ型など、サーバー カーソルの結果セットにある列の属性を示します。 サーバー カーソルにグローバルな属性の説明が必要な場合は、sp_describe_cursor を使用します。 カーソルが参照するベース テーブルのレポートが必要な場合は、sp_describe_cursor_tables を使用します。 接続時に可視になる [!INCLUDE[tsql](../../includes/tsql-md.md)] Server カーソルのレポートが必要な場合は、sp_cursor_list を使用します。  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、グローバル カーソルをオープンし、カーソルで使用されている列を `sp_describe_cursor_columns` を使用してレポートします。  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a global cursor.  
DECLARE abc CURSOR KEYSET FOR  
SELECT LastName  
FROM Person.Person;  
GO  
OPEN abc;  
  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_describe_cursor_columns.  
DECLARE @Report CURSOR;  
  
-- Execute sp_describe_cursor_columns into the cursor variable.  
EXEC master.dbo.sp_describe_cursor_columns  
    @cursor_return = @Report OUTPUT  
    ,@cursor_source = N'global'   
    ,@cursor_identity = N'abc';  
  
-- Fetch all the rows from the sp_describe_cursor_columns output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
   FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_describe_cursor_columns.  
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
 [CURSOR_STATUS &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/cursor-status-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [sp_describe_cursor &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-describe-cursor-transact-sql.md)   
 [sp_cursor_list と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cursor-list-transact-sql.md)   
 [sp_describe_cursor_tables &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-describe-cursor-tables-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

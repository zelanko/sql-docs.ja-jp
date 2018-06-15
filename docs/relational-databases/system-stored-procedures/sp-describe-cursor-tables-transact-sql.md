---
title: sp_describe_cursor_tables (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_describe_cursor_tables_TSQL
- sp_describe_cursor_tables
dev_langs:
- TSQL
helpviewer_keywords:
- sp_describe_cursor_tables
ms.assetid: 02c0f81a-54ed-4ca4-aa4f-bb7463a9ab9a
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 767cf7be622e557f78e207cfc8fecb9c4b0707e9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33261871"
---
# <a name="spdescribecursortables-transact-sql"></a>sp_describe_cursor_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバー カーソルが参照するオブジェクトまたはベース テーブルをレポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_describe_cursor_tables   
     [ @cursor_return = ] output_cursor_variable OUTPUT   
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
 カーソル出力を受け取るように宣言したカーソル変数の名前です。 *output_cursor_variable*は**カーソル**, ない必要があり、既定をどのカーソルに関連付けられた時にできない、sp_describe_cursor_tables が呼び出されます。 スクロール可能で動的な読み取り専用カーソルが返されます。  
  
 [ @cursor_source=] {N'local' |N'global' |N'variable'}  
 レポート対象のカーソルをローカル カーソル、グローバル カーソル、カーソル変数のどの名前で指定するのかを指定します。 パラメーターが**nvarchar (30)** です。  
  
 [ @cursor_identity=] N'*local_cursor_name*'  
 カーソルの名前または作成された DECLARE CURSOR ステートメントによって、ローカルのキーワードを既定値であるローカルです。 *local_cursor_name*は**nvarchar (128)** です。  
  
 [ @cursor_identity=] N'*global_cursor_name*'  
 カーソルの名前または作成された DECLARE CURSOR ステートメントによって、グローバルのキーワードをグローバルを既定値です。 *global_cursor_name* SQLSetCursorName を呼び出すことによってカーソルが指定する ODBC アプリケーションによってオープンされた API サーバー カーソルの名前をすることもできます *。global_cursor_name*は**nvarchar (128)** です。  
  
 [ @cursor_identity=] N'*input_cursor_variable*'  
 開いているカーソルに関連付けられたカーソル変数の名前です。 *input_cursor_variable*は**nvarchar (128)** です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="cursors-returned"></a>返されるカーソル  
 sp_describe_cursor_tables としてレポートをカプセル化、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **カーソル**出力パラメーターです。 これにより、[!INCLUDE[tsql](../../includes/tsql-md.md)]バッチ、ストアド プロシージャ、およびトリガーを一度に 1 行の出力を使用します。 また、API 関数からプロシージャを直接呼び出すことができなくなります。 **カーソル**出力パラメーターは、プログラム変数にバインドする必要がありますが、Api はバインドをサポートしていない**カーソル**パラメーターまたは変数です。  
  
 次の表に、sp_describe_cursor_tables が返すカーソルの形式を示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|table_owner|**sysname**|テーブル所有者のユーザー ID。|  
|Table_name|**sysname**|オブジェクトまたはベース テーブルの名前。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、サーバー カーソルは常にベース テーブルではなく、ユーザーが指定したオブジェクトを返します。|  
|optimizer_hints|**smallint**|次のうちの 1 つ以上で構成されるビットマップです。<br /><br /> 1 = 行レベルのロック (ROWLOCK)<br /><br /> 4 = ページレベルのロック (PAGELOCK)<br /><br /> 8 = テーブル ロック (TABLOCK)<br /><br /> 16 = 排他テーブル ロック (TABLOCKX)<br /><br /> 32 = 更新ロック (UPDLOCK)<br /><br /> 64 = ロックなし (NOLOCK)<br /><br /> 128 = 高速順方向参照 (FASTFIRST)<br /><br /> 4096 = DECLARE CURSOR で使用する場合、反復可能セマンティックの読み取り (HOLDLOCK)<br /><br /> 複数のオプションを指定する場合、システムは最も限定的なオプションを使用します。 ただし、sp_describe_cursor_tables は、クエリに指定されているフラグを表示します。|  
|lock_type|**smallint**|カーソルの基になっている各ベース テーブルに対して、明示的にまたは暗黙的に要求したスクロール ロックの種類です。 値は、次のいずれかです。<br /><br /> 0 = なし<br /><br /> 1 = 共有<br /><br /> 3 = 更新|  
|server_name|**sysname で、null 値を許容**|テーブルが存在するリンク サーバーの名前。 OPENQUERY または OPENROWSET が使用されている場合は NULL です。|  
|Objectid|**int**|テーブルのオブジェクト ID。 OPENQUERY または OPENROWSET が使用されている場合は 0 です。|  
|dbid|**int**|テーブルが存在するデータベースの ID。 OPENQUERY または OPENROWSET が使用されている場合は 0 です。|  
|dbname|**sysname**、 **null 許容型**|テーブルが存在するデータベースの名前。 OPENQUERY または OPENROWSET が使用されている場合は NULL です。|  
  
## <a name="remarks"></a>解説  
 sp_describe_cursor_tables は、サーバー カーソルが参照するベース テーブルを説明します。 カーソルから返された結果セットの属性の説明が必要な場合は、sp_describe_cursor_columns を使用します。 スクロール可能かどうか、更新可能かどうかなど、カーソルの総体的な特性の説明が必要な場合は、sp_describe_cursor を使用します。 接続時に可視である [!INCLUDE[tsql](../../includes/tsql-md.md)] Server カーソルに関するレポートが必要な場合は、sp_cursor_list を使用します。  
  
## <a name="permissions"></a>権限  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、グローバル カーソルを開きを使用して`sp_describe_cursor_tables`カーソルが参照されているテーブル上にレポートします。  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare and open a global cursor.  
DECLARE abc CURSOR KEYSET FOR  
SELECT LastName  
FROM Person.Person  
WHERE LastName LIKE 'S%';  
  
OPEN abc;  
GO  
-- Declare a cursor variable to hold the cursor output variable  
-- from sp_describe_cursor_tables.  
DECLARE @Report CURSOR;  
  
-- Execute sp_describe_cursor_tables into the cursor variable.  
EXEC master.dbo.sp_describe_cursor_tables  
      @cursor_return = @Report OUTPUT,  
      @cursor_source = N'global', @cursor_identity = N'abc';  
  
-- Fetch all the rows from the sp_describe_cursor_tables output cursor.  
FETCH NEXT from @Report;  
WHILE (@@FETCH_STATUS <> -1)  
BEGIN  
   FETCH NEXT from @Report;  
END  
  
-- Close and deallocate the cursor from sp_describe_cursor_tables.  
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
 [sp_describe_cursor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-transact-sql.md)   
 [sp_describe_cursor_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-cursor-columns-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

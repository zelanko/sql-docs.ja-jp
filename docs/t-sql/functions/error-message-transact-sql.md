---
title: ERROR_MESSAGE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- ERROR_MESSAGE_TSQL
- ERROR_MESSAGE
dev_langs:
- TSQL
helpviewer_keywords:
- ERROR_MESSAGE function
- errors [SQL Server], text of
- messages [SQL Server], text of
- TRY...CATCH [SQL Server]
- CATCH block
ms.assetid: f32877a6-5f17-418c-a32c-5a1a344b3c45
caps.latest.revision: 53
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4f8ca76a181cd518b2790fda4e85ba12d9150a4c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43073660"
---
# <a name="errormessage-transact-sql"></a>ERROR_MESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

この関数は、TRY…CATCH 構造の CATCH ブロックが実行される原因となったエラーのメッセージ テキストを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ERROR_MESSAGE ( )   
```  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (4000)**  
  
## <a name="return-value"></a>戻り値  
`ERROR_MESSAGE` は、CATCH ブロック内で呼び出されると、`CATCH` ブロックが実行される原因となったエラー メッセージの全テキストを返します。 このテキストには、長さ、オブジェクト名、時刻など、置換可能なパラメーターに指定された値が含まれます。  
  
`ERROR_MESSAGE` は、CATCH ブロックの範囲外で呼び出されると、NULL を返します。  
  
## <a name="remarks"></a>Remarks  
`ERROR_MESSAGE` は、CATCH ブロックのスコープ内の任意の場所で呼び出すことができます。  
  
`ERROR_MESSAGE` は、実行回数に関係なく、あるいは `CATCH` ブロックのスコープ内の実行場所に関係なく、関連エラー メッセージを返します。 エラーが発生したステートメントの直後のステートメントのエラー番号のみを返す、@@ERROR などの関数とは対照的となります。  
  
`CATCH` ブロックが入れ子になっている場合、`ERROR_MESSAGE` は、`CATCH` ブロックを参照した `CATCH` ブロックのスコープに固有のエラー メッセージを返します。 たとえば、外側の TRY...CATCH 構造の `CATCH` ブロックの中に `TRY...CATCH` 構造が含まれることがあります。 その内側の `CATCH` ブロック内では、`ERROR_MESSAGE` は内側の `CATCH` ブロックを呼び出したエラーからのメッセージを返します。 `ERROR_MESSAGE` が外側の `CATCH` ブロック内で実行される場合、外側の `CATCH` ブロックを呼び出したエラーからのメッセージを返します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-errormessage-in-a-catch-block"></a>A. CATCH ブロックで ERROR_MESSAGE を使用する  
この例は、0 除算エラーを生成する `SELECT` ステートメントを示しています。 `CATCH` ブロックはエラー メッセージを返します。  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorMessage
----------------------------------
Divide by zero error encountered.

(1 row(s) affected)

```  
  
### <a name="b-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>B. CATCH ブロックで、別のエラー処理ツールと一緒に ERROR_MESSAGE を使用する  
この例は、0 除算エラーを生成する `SELECT` ステートメントを示しています。 `CATCH` ブロックは、エラー メッセージと共にそのエラーに関する情報を返します。  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  

-----------

(0 row(s) affected)

ErrorNumber ErrorSeverity ErrorState  ErrorProcedure  ErrorLine  ErrorMessage
----------- ------------- ----------- --------------- ---------- ----------------------------------
8134        16            1           NULL            4          Divide by zero error encountered.

(1 row(s) affected)

```
  


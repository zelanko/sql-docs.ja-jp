---
title: "ERROR_MESSAGE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f15d9d23726f7558f0bf73aff3f8c3c5253cb24d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="errormessage-transact-sql"></a>ERROR_MESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  TRY...CATCH 構造の CATCH ブロックが実行される原因となったエラーのメッセージ テキストを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
ERROR_MESSAGE ( )   
```  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (4000)**  
  
## <a name="return-value"></a>戻り値  
 CATCH ブロック内で呼び出された場合は、CATCH ブロックが実行される原因となったエラー メッセージの全テキストを返します。 このテキストには、長さ、オブジェクト名、回数など、置き換え可能なパラメーターに提供される値が含まれます。  
  
 CATCH ブロックの範囲外で呼び出された場合は NULL を返します。  
  
## <a name="remarks"></a>解説  
 ERROR_MESSAGE は、CATCH ブロックのスコープ内であればどこでも呼び出すことができます。  
  
 ERROR_MESSAGE では、実行される回数や、CATCH ブロックのスコープ内のどこで実行されるかに関係なく、エラー メッセージが返されます。 これは、@ などの関数とは対照的@ERRORエラーが発生した直後後のステートメントでのみ、エラー番号が返されます、または CATCH の最初のステートメントをブロックします。  
  
 入れ子にされた CATCH ブロックでは、ERROR_MESSAGE によって、参照される CATCH ブロックのスコープ固有のエラー メッセージが返されます。 たとえば、外側の TRY...CATCH 構造の CATCH ブロックには、TRY...CATCH 構造が入れ子にされている場合があります。 入れ子にされた CATCH ブロックでは、ERROR_MESSAGE によって、入れ子にされた CATCH ブロックを起動したエラーのメッセージが返されます。 ERROR_MESSAGE が外側の CATCH ブロックで実行された場合は、その CATCH ブロックを起動したエラーのメッセージが返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-errormessage-in-a-catch-block"></a>A. CATCH ブロックで ERROR_MESSAGE を使用する  
 次のコード例は、 `SELECT` 0 除算エラーを生成するステートメント。 ここではエラーのメッセージが返されます。  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>B. CATCH ブロックで、別のエラー処理ツールと一緒に ERROR_MESSAGE を使用する  
 次のコード例は、 `SELECT` 0 除算エラーを生成するステートメント。 ここではエラー メッセージと共に、エラーに関連する情報が返されます。  
  
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
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errormessage-in-a-catch-block"></a>C. CATCH ブロックで ERROR_MESSAGE を使用する  
 次のコード例は、 `SELECT` 0 除算エラーを生成するステートメント。 ここではエラーのメッセージが返されます。  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
### <a name="d-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>D. CATCH ブロックで、別のエラー処理ツールと一緒に ERROR_MESSAGE を使用する  
 次のコード例は、 `SELECT` 0 除算エラーを生成するステートメント。 ここではエラー メッセージと共に、エラーに関連する情報が返されます。  
  
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
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  



---
title: "ERROR_NUMBER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ERROR_NUMBER_TSQL
- ERROR_NUMBER
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], line number
- messages [SQL Server], numbers
- TRY...CATCH [SQL Server]
- ERROR_NUMBER function
- CATCH block
ms.assetid: 1de85fff-1ca2-4b31-841b-926e571cb150
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 88a6b73698c38e88905ea5efe3883a5d0d73d85e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="errornumber-transact-sql"></a>ERROR_NUMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  TRY...CATCH 構造の CATCH ブロックの実行を引き起こしたエラーのエラー番号を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ERROR_NUMBER ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="return-value"></a>戻り値  
 CATCH ブロックで呼び出されると、CATCH ブロックの実行を引き起こしたエラー メッセージのエラー番号を返します。  
  
 CATCH ブロックの範囲外で呼び出された場合は NULL を返します。  
  
## <a name="remarks"></a>解説  
 この関数は、CATCH ブロックのスコープ内の任意の場所で呼び出すことができます。  
  
 ERROR_NUMBER は、その実行回数、または実行される CATCH ブロックのスコープ内の場所に関係なく、エラー番号を返します。 これは、対照的に@ERRORのみ、エラーが発生した直後後のステートメントではエラー番号が返されます、または CATCH の最初のステートメントをブロックします。  
  
 入れ子になった CATCH ブロックでは、ERROR_NUMBER は、参照されている CATCH ブロックのスコープに固有のエラー番号を返します。 たとえば、外側の TRY...CATCH 構造の CATCH ブロックには、TRY...CATCH 構造が入れ子にされている場合があります。 入れ子になった CATCH ブロック内では、ERROR_NUMBER は、入れ子になった CATCH ブロックを呼び出したエラーの番号を返します。 ERROR_NUMBER が外部の CATCH ブロックで実行されると、その CATCH ブロックを呼び出したエラーの番号が返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-errornumber-in-a-catch-block"></a>A. CATCH ブロックで ERROR_NUMBER を使用する  
 次のコード例は、 `SELECT` 0 除算エラーを生成するステートメント。 エラーの番号が返されます。  
  
```  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_NUMBER() AS ErrorNumber;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errornumber-in-a-catch-block-with-other-error-handling-tools"></a>B. CATCH ブロックで ERROR_NUMBER を他のエラー処理ツールと一緒に使用する  
 次のコード例は、 `SELECT` 0 除算エラーを生成するステートメント。 エラー番号と共に、エラーに関連する情報が返されます。  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_LINE() AS ErrorLine,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errornumber-in-a-catch-block-with-other-error-handling-tools"></a>C. CATCH ブロックで ERROR_NUMBER を他のエラー処理ツールと一緒に使用する  
 次のコード例は、 `SELECT` 0 除算エラーを生成するステートメント。 エラー番号と共に、エラーに関連する情報が返されます。  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber,  
        ERROR_SEVERITY() AS ErrorSeverity,  
        ERROR_STATE() AS ErrorState,  
        ERROR_PROCEDURE() AS ErrorProcedure,  
        ERROR_MESSAGE() AS ErrorMessage;  
END CATCH;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE &#40; です。TRANSACT-SQL と&#41; です。](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  


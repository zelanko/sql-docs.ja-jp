---
title: ERROR_SEVERITY (Transact-SQL) | Microsoft Docs
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
- ERROR_SEVERITY_TSQL
- ERROR_SEVERITY
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], severity
- messages [SQL Server], severity
- TRY...CATCH [SQL Server]
- CATCH block
- ERROR_SEVERITY function
ms.assetid: 50228f2f-6949-4d2e-8e43-fad11bf973ab
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d5c8b4aa0a53a39ed6773fdf90ff42dc6128b2f3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="errorseverity-transact-sql"></a>ERROR_SEVERITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  TRY...CATCH 構造の CATCH ブロックの実行を引き起こしたエラーの重大度を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ERROR_SEVERITY ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="return-value"></a>戻り値  
 CATCH ブロックの中で呼び出されると、CATCH ブロックの実行を引き起こしたエラー メッセージの重大度を返します。  
  
 CATCH ブロックの範囲外で呼び出された場合は NULL を返します。  
  
## <a name="remarks"></a>Remarks  
 ERROR_SEVERITY は、CATCH ブロックのスコープ内の任意の場所で呼び出すことができます。  
  
 ERROR_SEVERITY は、その実行回数、または実行される CATCH ブロックのスコープ内の場所に関係なく、エラーの重大度を返します。 これは、@@ERROR などの関数とは対照的です。これらの関数がエラー番号を返すのは、エラーが発生したステートメントの直後のステートメントか、CATCH ブロックの最初のステートメントだけです。  
  
 入れ子になった CATCH ブロックでは、ERROR_SEVERITY は、参照されている CATCH ブロックのスコープに固有のエラーの重大度を返します。 たとえば、外側の TRY...CATCH 構造の CATCH ブロックには、TRY...CATCH 構造が入れ子にされている場合があります。 この場合、入れ子になった CATCH ブロック内では、ERROR_SEVERITY は、入れ子になった CATCH ブロックを呼び出したエラーの重大度を返します。 ERROR_SEVERITY が外部の CATCH ブロックで実行された場合は、その CATCH ブロックを呼び出したエラーの重大度が返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-errorseverity-in-a-catch-block"></a>A. CATCH ブロックで ERROR_SEVERITY を使用する  
 次の例は、0 除算エラーを生成する `SELECT` ステートメントを示しています。 エラーの重大度が返されます。  
  
```  
  
BEGIN TRY  
    -- Generate a divide-by-zero error.  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_SEVERITY() AS ErrorSeverity;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorseverity-in-a-catch-block-with-other-error-handling-tools"></a>B. CATCH ブロックで ERROR_SEVERITY を他のエラー処理ツールと一緒に使用する  
 次の例は、0 除算エラーを生成する `SELECT` ステートメントを示しています。 重大度と共にエラーに関する情報が返されます。  
  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errorseverity-in-a-catch-block-with-other-error-handling-tools"></a>C. CATCH ブロックで ERROR_SEVERITY を他のエラー処理ツールと一緒に使用する  
 次の例は、0 除算エラーを生成する `SELECT` ステートメントを示しています。 重大度と共にエラーに関する情報が返されます。  
  
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
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_STATE &#40;Transact-SQL&#41;](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  


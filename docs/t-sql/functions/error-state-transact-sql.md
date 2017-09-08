---
title: "ERROR_STATE (TRANSACT-SQL) |Microsoft ドキュメント"
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
- ERROR_STATE_TSQL
- ERROR_STATE
dev_langs:
- TSQL
helpviewer_keywords:
- messages [SQL Server], state
- ERROR_STATE function
- errors [SQL Server], state
- TRY...CATCH [SQL Server]
- CATCH block
- states [SQL Server], error numbers
ms.assetid: 6059af00-83fe-409f-ab7c-daad111bc671
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 98b5a1ecfbfd9efd84f8a5cc55454aaaec6f8423
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="errorstate-transact-sql"></a>ERROR_STATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  TRY...CATCH 構造の CATCH ブロックが実行された原因となるエラーの状態番号を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
ERROR_STATE ( )  
```  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="return-value"></a>戻り値  
 CATCH ブロックの中で呼び出された場合は、CATCH ブロックが実行された原因となるエラー メッセージの状態番号を返します。  
  
 CATCH ブロックの範囲外で呼び出された場合は NULL を返します。  
  
## <a name="remarks"></a>解説  
 コードでの複数のポイントで一部のエラー メッセージが生成されることが、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]です。 たとえば、異なる複数の条件で "1105" エラーが生成されることがあります。 エラーを生成するそれぞれの条件によって、一意の状態コードが割り当てられます。  
  
 など、既知の問題のデータベースを表示するときに、[!INCLUDE[msCoName](../../includes/msconame-md.md)]ナレッジ ベース、記録された問題が発生したエラーと同じである可能性があるかどうかを決定する、状態番号を使用することができます。 たとえば、技術情報の資料で取り上げられている 1105 エラー メッセージの状態番号が 2 で、実際の 1105 エラー メッセージの状態番号が 3 だった場合、そのエラーは、その資料で報告されているものとは別の原因で発生したと考えられます。  
  
 A[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サポート エンジニアはできるもエラー状態コードを使用して問題を診断する方法の他のアイデアを提供する可能性がありますが、そのエラーが生成されたソース コードの場所を検索します。  
  
 ERROR_STATE は、CATCH ブロックのスコープ内の任意の場所で呼び出すことができます。  
  
 ERROR_STATE は、実行された回数や実行される CATCH ブロックのスコープ内の場所に関係なく、エラー状態を返します。 これは、@ などの関数とは対照的@ERROR、または CATCH ブロックの最初のステートメントでは、エラーが発生した直後後のステートメントでのみエラー番号が返されます。  
  
 入れ子になった CATCH ブロックでは、ERROR_STATE は、参照されている CATCH ブロックのスコープに固有のエラー状態を返します。 たとえば、外側の TRY...CATCH 構造の CATCH ブロックには、TRY...CATCH 構造が入れ子にされている場合があります。 この場合、入れ子になった CATCH ブロック内では、ERROR_STATE は、入れ子になった CATCH ブロックを呼び出したエラーの状態を返します。 ERROR_STATE が外部の CATCH ブロックで実行された場合は、その CATCH ブロックを呼び出したエラーの状態が返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-errorstate-in-a-catch-block"></a>A. CATCH ブロックで ERROR_STATE を使用する  
 次の例は、 `SELECT` 0 除算エラーを生成するステートメント。 エラーの状態が返されます。  
  
```  
BEGIN TRY  
    -- Generate a divide by zero error  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_STATE() AS ErrorState;  
END CATCH;  
GO  
```  
  
### <a name="b-using-errorstate-in-a-catch-block-with-other-error-handling-tools"></a>B. CATCH ブロックで ERROR_STATE を他のエラー処理ツールと一緒に使用する  
 次の例は、 `SELECT` 0 除算エラーを生成するステートメント。 エラーの状態と共にエラーに関する情報が返されます。  
  
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
  
### <a name="c-using-errorstate-in-a-catch-block"></a>C. CATCH ブロックで ERROR_STATE を使用する  
 次の例は、 `SELECT` 0 除算エラーを生成するステートメント。 エラーの状態が返されます。  
  
```  
BEGIN TRY  
    -- Generate a divide by zero error  
    SELECT 1/0;  
END TRY  
BEGIN CATCH  
    SELECT ERROR_STATE() AS ErrorState;  
END CATCH;  
GO  
```  
  
### <a name="d-using-errorstate-in-a-catch-block-with-other-error-handling-tools"></a>D. CATCH ブロックで ERROR_STATE を他のエラー処理ツールと一緒に使用する  
 次の例は、 `SELECT` 0 除算エラーを生成するステートメント。 エラーの状態と共にエラーに関する情報が返されます。  
  
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
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)  
  
  



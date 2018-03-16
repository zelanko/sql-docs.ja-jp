---
title: ERROR_MESSAGE (Transact-SQL) | Microsoft Docs
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 598b89a47941c038b39387468de8bd3036acae2b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="errormessage-transact-sql"></a>ERROR_MESSAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  TRY...CATCH 構造の CATCH ブロックが実行される原因となったエラーのメッセージ テキストを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ERROR_MESSAGE ( )   
```  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (4000)**  
  
## <a name="return-value"></a>戻り値  
 CATCH ブロック内で呼び出された場合は、CATCH ブロックが実行される原因となったエラー メッセージの全テキストを返します。 このテキストには、長さ、オブジェクト名、回数など、置き換え可能なパラメーターに提供される値が含まれます。  
  
 CATCH ブロックの範囲外で呼び出された場合は NULL を返します。  
  
## <a name="remarks"></a>Remarks  
 ERROR_MESSAGE は、CATCH ブロックのスコープ内であればどこでも呼び出すことができます。  
  
 ERROR_MESSAGE では、実行される回数や、CATCH ブロックのスコープ内のどこで実行されるかに関係なく、エラー メッセージが返されます。 これは、@@ERROR のような関数とは対照的です。@@ERROR 関数では、エラーが発生したステートメントの直後のステートメント、または CATCH ブロックの最初のステートメントでエラー番号が返されます。  
  
 入れ子にされた CATCH ブロックでは、ERROR_MESSAGE によって、参照される CATCH ブロックのスコープ固有のエラー メッセージが返されます。 たとえば、外側の TRY...CATCH 構造の CATCH ブロックには、TRY...CATCH 構造が入れ子にされている場合があります。 入れ子にされた CATCH ブロックでは、ERROR_MESSAGE によって、入れ子にされた CATCH ブロックを起動したエラーのメッセージが返されます。 ERROR_MESSAGE が外側の CATCH ブロックで実行された場合は、その CATCH ブロックを起動したエラーのメッセージが返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-errormessage-in-a-catch-block"></a>A. CATCH ブロックで ERROR_MESSAGE を使用する  
 次の例では、0 除算エラーを生成する `SELECT` ステートメントを示します。 ここではエラーのメッセージが返されます。  
  
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
 次の例では、0 除算エラーを生成する `SELECT` ステートメントを示します。 ここではエラー メッセージと共に、エラーに関連する情報が返されます。  
  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-errormessage-in-a-catch-block-with-other-error-handling-tools"></a>C. CATCH ブロックで、別のエラー処理ツールと一緒に ERROR_MESSAGE を使用する  
 次の例では、0 除算エラーを生成する `SELECT` ステートメントを示します。 ここではエラー メッセージと共に、エラーに関連する情報が返されます。  
  
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
  


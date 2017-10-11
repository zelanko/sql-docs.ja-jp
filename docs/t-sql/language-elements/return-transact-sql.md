---
title: "戻り値 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- RETURN_TSQL
- RETURN
dev_langs:
- TSQL
helpviewer_keywords:
- unconditionally exiting program
- stored procedures [SQL Server], exiting
- batches [SQL Server], exiting
- statement blocks [SQL Server]
- queries [SQL Server], exiting
- exiting queries [SQL Server]
- exiting procedures [SQL Server]
- RETURN statement
ms.assetid: 1d9c8247-fd89-4544-be9c-01c95b745db0
caps.latest.revision: 39
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c4c3db821e25a671872035e1a584bf5e4205657d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="return-transact-sql"></a>RETURN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  クエリまたはプロシージャを無条件で終了します。 RETURN は即時に実行され、完了します。また、プロシージャ、バッチ、またはステートメント ブロックを終了する任意の位置で使用できます。 RETURN の後に続くステートメントは実行されません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
RETURN [ integer_expression ]   
```  
  
## <a name="arguments"></a>引数  
 *integer_expression*  
 返される整数値です。 ストアド プロシージャは、呼び出しプロシージャまたはアプリケーションに整数値を返すことができます。  
  
## <a name="return-types"></a>戻り値の型  
 必要に応じて返します**int**です。  
  
> [!NOTE]  
>  特に記述がない限り、すべてのシステム ストアド プロシージャでは値 0 が返されます。 これは成功を示し、0 以外の値は失敗を示します。  
  
## <a name="remarks"></a>解説  
 ストアド プロシージャと一緒に使用する場合、RETURN は NULL 値を返すことができません。 プロシージャは、null 値を取得しようとした場合 (たとえば、戻り値を使用して@statusとき@statusnull)、警告メッセージが生成され、値 0 が返されます。  
  
 現在のプロシージャを実行したバッチまたはプロシージャの中の後続の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントに、返されたステータス値を指定できます。この場合、`EXECUTE @return_status = <procedure_name>` の形式で入力する必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-from-a-procedure"></a>A. プロシージャを終了する  
 次の例は、パラメーターとしてユーザー名を指定しないかどうかと`findjobs`が実行される`RETURN`が原因で、ユーザーの画面にメッセージが送信された後に終了するプロシージャ。 ユーザー名が指定された場合は、そのユーザーが現在のデータベースに作成したすべてのオブジェクトの名前を、適切なシステム テーブルから取得します。  
  
```  
CREATE PROCEDURE findjobs @nm sysname = NULL  
AS   
IF @nm IS NULL  
    BEGIN  
        PRINT 'You must give a user name'  
        RETURN  
    END  
ELSE  
    BEGIN  
        SELECT o.name, o.id, o.uid  
        FROM sysobjects o INNER JOIN master..syslogins l  
            ON o.uid = l.sid  
        WHERE l.name = @nm  
    END;  
```  
  
### <a name="b-returning-status-codes"></a>B. ステータス コードを返す  
 次の例では、指定した連絡先の ID の状態をチェックします。 状態が Washington 場合 (`WA`)、ステータスの`1`が返されます。 `2` が `WA` 以外の値であったり、`StateProvince` が行に一致しないなど、それ以外のすべての場合は、`ContactID` を返します。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE PROCEDURE checkstate @param varchar(11)  
AS  
IF (SELECT StateProvince FROM Person.vAdditionalContactInfo WHERE ContactID = @param) = 'WA'  
    RETURN 1  
ELSE  
    RETURN 2;  
GO  
```  
  
 次の例では、`checkstate` を実行して得られる戻りステータスを示します。 最初は Washington の連絡先、2 つ目は Washington 以外の連絡先、3 つ目は有効でない連絡先を示しています。 `@return_status` ローカル変数は、これを宣言してからでないと使用できません。  
  
```  
DECLARE @return_status int;  
EXEC @return_status = checkstate '2';  
SELECT 'Return Status' = @return_status;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Return Status 
  
 ------------- 
  
 1
 ```  
  
 別の連絡先番号を指定して、クエリを再び実行します。  
  
```  
DECLARE @return_status int;  
EXEC @return_status = checkstate '6';  
SELECT 'Return Status' = @return_status;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Return Status  
 -------------  
  
 2
 ```  
  
 別の連絡先の電話番号を指定する、もう一度クエリを実行します。  
  
```  
DECLARE @return_status int  
EXEC @return_status = checkstate '12345678901';  
SELECT 'Return Status' = @return_status;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Return Status  
 -------------  
  
 2
 ```  
  
## <a name="see-also"></a>参照  
 [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)   
 [THROW &#40;Transact-SQL&#41;](../../t-sql/language-elements/throw-transact-sql.md)  
  
  

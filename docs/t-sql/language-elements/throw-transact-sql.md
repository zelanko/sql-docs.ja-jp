---
title: "THROW (TRANSACT-SQL) |Microsoft ドキュメント"
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
- THROW_TSQL
- THROW
dev_langs:
- TSQL
helpviewer_keywords:
- THROW statement
ms.assetid: 43661b89-8f13-4480-ad53-70306cbb14c5
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7e61cb9edc75dda4368e31e9eac6e4e452d4387f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="throw-transact-sql"></a>THROW (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all_md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  例外が発生し、実行を試してみてくださいの CATCH ブロックに転送しています.CATCH 構造で[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
THROW [ { error_number | @local_variable },  
        { message | @local_variable },  
        { state | @local_variable } ]   
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *error_number*  
 例外を表す定数または変数です。 *error_number*は**int** 50000 以上にする必要があります 2,147, 483,647 以下です。  
  
 *メッセージ*  
 例外を説明する文字列または変数です。 *メッセージ*は**nvarchar (2048)**です。  
  
 *状態*  
 メッセージに関連付けられる状態を示す、0 ～ 255 の範囲の定数または変数です。 *状態*は**tinyint**です。  
  
## <a name="remarks"></a>解説  
 THROW ステートメントはセミコロン (;) が続かなければなりません前に、のステートメント ステートメントのターミネータです。  
  
 TRY...CATCH 構造を使用できない場合は、セッションが終了します。 例外が発生する行番号およびプロシージャが設定されます。 重大度は 16 に設定されます。  
  
 パラメーターを使用せずに THROW ステートメントを指定する場合は、ステートメントが CATCH ブロック内に存在する必要があります。 これによりキャッチされた例外が発生します。 THROW ステートメントで発生したエラーは、ステートメント バッチが終了させます。  
  
 % は THROW ステートメントのメッセージ テキストに予約された文字で、エスケープする必要があります。 文字 % を二重にすると、% をメッセージ テキストの一部として返します (例: 「増加が元の値の 15 %% を超えました。」)。  
  
## <a name="differences-between-raiserror-and-throw"></a>RAISERROR と THROW の違い  
 次の表では、RAISERROR ステートメントと THROW ステートメントの違いを示します。  
  
|RAISERROR ステートメント|THROW ステートメント|  
|-------------------------|---------------------|  
|場合、 *msg_id*渡される sys.messages 内で raiserror に ID を定義する必要があります。|*Error_number*パラメーターが sys.messages 内で定義する必要はありません。|  
|*Msg_str*パラメーターを含めることができます**printf**スタイルの書式設定します。|*メッセージ*パラメーターが受け付けない**printf**スタイルで書式設定します。|  
|*重大度*パラメーターは、例外の重大度を指定します。|ない*重大度*パラメーター。 例外の重大度は常に 16 に設定されます。|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-throw-to-raise-an-exception"></a>A. THROW を使用して例外を発生させる  
 次の例を使用する方法を示しています、`THROW`ステートメントから例外が発生します。  
  
```tsql  
THROW 51000, 'The record does not exist.', 1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Msg 51000, Level 16, State 1, Line 1`  
  
 `The record does not exist.`  
  
### <a name="b-using-throw-to-raise-an-exception-again"></a>B. THROW を使用して例外を再度発生させる  
 次の例では、`THROW`最後スローされた例外を再度を発生させるステートメントです。  
  
```tsql  
USE tempdb;  
GO  
CREATE TABLE dbo.TestRethrow  
(    ID INT PRIMARY KEY  
);  
BEGIN TRY  
    INSERT dbo.TestRethrow(ID) VALUES(1);  
--  Force error 2627, Violation of PRIMARY KEY constraint to be raised.  
    INSERT dbo.TestRethrow(ID) VALUES(1);  
END TRY  
BEGIN CATCH  
  
    PRINT 'In catch block.';  
    THROW;  
END CATCH;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `PRINT 'In catch block.';`  
  
 `Msg 2627, Level 14, State 1, Line 1`  
  
 `Violation of PRIMARY KEY constraint 'PK__TestReth__3214EC272E3BD7D3'. Cannot insert duplicate key in object 'dbo.TestRethrow'.`  
  
 `The statement has been terminated.`  
  
### <a name="c-using-formatmessage-with-throw"></a>C. FORMATMESSAGE を THROW と共に使用する  
 次の例を使用する方法を示しています、`FORMATMESSAGE`で機能`THROW`カスタマイズされたエラー メッセージをスローします。 この例では、まず、`sp_addmessage` を使用して、ユーザー定義のエラー メッセージを作成します。 THROW ステートメントは置換パラメーターで許可されないため、*メッセージ*エラー メッセージ 60000 で想定されている 3 つのパラメーター値を渡す方法では、RAISERROR FORMATMESSAGE 関数のパラメーターを使用します。  
  
```tsql  
EXEC sys.sp_addmessage  
     @msgnum   = 60000  
,@severity = 16  
,@msgtext  = N'This is a test message with one numeric parameter (%d), one string parameter (%s), and another string parameter (%s).'  
    ,@lang = 'us_english';   
GO  
  
DECLARE @msg NVARCHAR(2048) = FORMATMESSAGE(60000, 500, N'First string', N'second string');   
  
THROW 60000, @msg, 1;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Msg 60000, Level 16, State 1, Line 2`  
  
 `This is a test message with one numeric parameter (500), one string parameter (First string), and another string parameter (second string).`  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-throw-to-raise-an-exception"></a>D. THROW を使用して例外を発生させる  
 次の例を使用する方法を示しています、`THROW`ステートメントから例外が発生します。  
  
```tsql  
THROW 51000, 'The record does not exist.', 1;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Msg 51000, Level 16, State 1, Line 1`  
  
 `The record does not exist.`  
  
## <a name="see-also"></a>参照  
 [FORMATMESSAGE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/formatmessage-transact-sql.md)   
 [データベース エンジン エラーの重大度](../../relational-databases/errors-events/database-engine-error-severities.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/error-state-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)   
 [GOTO & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/goto-transact-sql.md)   
 [作業を開始してください.END & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [XACT_STATE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/xact-state-transact-sql.md)   
 [SET XACT_ABORT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-xact-abort-transact-sql.md)  
  
  



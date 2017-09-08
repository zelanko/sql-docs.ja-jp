---
title: "RAISERROR (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/21/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RAISERROR
- RAISERROR_TSQL
- RAISEERROR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmessages system table
- errors [SQL Server], RAISERROR statement
- user-defined error messages [SQL Server]
- system flags
- generating errors [SQL Server]
- TRY block [SQL Server]
- recording errors
- ad hoc messages
- RAISERROR statement
- CATCH block
- messages [SQL Server], RAISERROR statement
ms.assetid: 483588bd-021b-4eae-b4ee-216268003e79
caps.latest.revision: 73
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 15ed174d3f16a70f63973c586a15759afad72565
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="raiserror-transact-sql"></a>RAISERROR Transact SQL
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  エラー メッセージを生成し、セッションのエラー処理を開始します。 RAISERROR では、sys.messages カタログ ビューに格納されているユーザー定義のメッセージを参照することまたは、メッセージを動的に作成できます。 メッセージは、サーバー エラー メッセージとして、呼び出し元のアプリケーションまたは関連する TRY...CATCH 構造の CATCH ブロックに返されます。 新しいアプリケーションを使用する必要があります[スロー](../../t-sql/language-elements/throw-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
RAISERROR ( { msg_id | msg_str | @local_variable }  
    { ,severity ,state }  
    [ ,argument [ ,...n ] ] )  
    [ WITH option [ ,...n ] ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
RAISERROR ( { msg_str | @local_variable }  
    { ,severity ,state }  
    [ ,argument [ ,...n ] ] )  
    [ WITH option [ ,...n ] ]  
```  
  
## <a name="arguments"></a>引数  
 *msg_id*  
 ユーザー定義エラー メッセージ番号は、sp_addmessage を使用して、sys.messages カタログ ビューに格納されます。 ユーザー定義エラー メッセージのエラー番号は、必ず 50000 より大きくなります。 ときに*msg_id*が指定されていない、RAISERROR はエラー番号 50000 のエラー メッセージを発生させます。  
  
 *msg_str*  
 書式設定を含むユーザー定義メッセージをに似ていますが、 **printf** C 標準ライブラリ内の関数。 エラー メッセージの長さは最大 2,047 文字です。 メッセージの文字数が 2,048 文字を超えると、2,044 文字までだけ表示され、メッセージが途中で切れていることを示す省略記号が追加されます。 内部的な記憶動作が原因で、書式引数は出力として表示されるより多くの文字を使用することに注意してください。 置換パラメーターなど、 *%d* 2 の値が割り当てられる実際に生成されるメッセージ文字列内の 1 つの文字が、内部的にも記憶域の 3 つの追加の文字を占有します。 この記憶領域の要件により、メッセージ出力で使用できる文字数は少なくなります。  
  
 ときに*msg_str*を指定すると、RAISERROR はエラー番号 50000 のエラー メッセージを発生させます。  
  
 *msg_str*省略可能な組み込みの変換が指定された文字の文字列を指定します。 各変換指定子は、引数リスト内の値を書式化およびフィールド内の変換指定の場所に配置する方法を定義します。 *msg_str*です。 変換指定の形式は、  
  
 % [*フラグ*] [*幅*] [です。 *有効桁数*] [{h | l}]*型*  
  
 使用できるパラメーター *msg_str*は。  
  
 *フラグ*  
  
 置換された値の間隔と配置を決めるコードです。  
  
|コード|プレフィックスまたは配置|Description|  
|----------|-----------------------------|-----------------|  
|- (マイナス)|左寄せ|指定されたフィールド幅内で引数の値を左寄せします。|  
|+ (プラス)|符号プレフィックス|引数の値が符号付きの場合に、プラス記号 (+) またはマイナス記号 (-) を先頭に付けます。|  
|0 (ゼロ)|0 埋め|幅の最小値になるまで、出力の先頭に 0 を付けます。 0 とマイナス記号 (-) が付いている場合は、0 は無視されます。|  
|# (番号)|16 進型の x または X に対する 0x プレフィックス|番号記号 (#) フラグは、o、x、または X 形式で使われる場合、0 以外の値の先頭に、それぞれ 0、0x、0X を付けます。 d、i、または u に番号記号 (#) フラグが付いている場合、フラグは無視されます。|  
|' ' (空白)|スペース埋め|出力値が符号付きで正の値の場合に、先頭に空白を付けます。 プラス記号 (+) フラグが指定される場合は、この空白は無視されます。|  
  
 *幅*  
  
 引数値が配置されるフィールドの幅の最小値を定義する整数です。 引数の値の長さが同じかまたはよりも長いかどうか*幅*、埋め込みなしで、値を出力します。 値がよりも短い場合*幅*、値が指定された長さに埋め込まれた*幅*です。  
  
 アスタリスク (*) は、width が引数リスト内の関連する引数によって指定されることを意味します。この引数は整数値である必要があります。  
  
 *有効桁数 (precision)*  
  
 文字列の値の引数値から取得される最大文字数です。 たとえば、文字列が 5 文字で、precision が 3 の場合、文字列の値の最初の 3 文字のみが使用されます。  
  
 整数値の場合は、*精度*印刷桁の数字の最小数です。  
  
 アスタリスク (*) は、precision が引数のリスト内の関連する引数により指定されることを意味します。この引数は整数値である必要があります。  
  
 {h | l}*型*  
  
 文字の種類の d で使用される i、o、s、x、X、または u を作成および**shortint** (h) または**longint** (l) の値。  
  
|型の仕様|表します|  
|------------------------|----------------|  
|d または i|符号付き整数|  
|o|符号なし 8 進数|  
|s|文字列|  
|u|符号なし整数|  
|x または X|符号なし 16 進数|  
  
> [!NOTE]  
>  に対して定義されているに基づいてこれらの種類の仕様、 **printf** C 標準ライブラリ内の関数。 RAISERROR メッセージ文字列マップで使用されるタイプ仕様[!INCLUDE[tsql](../../includes/tsql-md.md)]で使用される仕様の中に、データ型**printf** C 言語のデータ型にマップします。 使用される仕様の入力**printf** RAISERROR でサポートされていないときに[!INCLUDE[tsql](../../includes/tsql-md.md)]C データ型が関連付けられているようなデータ型はありません。 たとえば、 *%p*ために、ポインターの仕様は RAISERROR でサポートされていません[!INCLUDE[tsql](../../includes/tsql-md.md)]ポインターのデータ型はありません。  
  
> [!NOTE]  
>  値を変換する、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **bigint**データ型、 **%i64d**です。  
  
 **@***local_variable*  
 任意の有効な文字データ型と同じ方法で書式設定文字列を含む変数*msg_str*です。 **@***local_variable*する必要があります**char**または**varchar**、これらのデータ型に暗黙的に変換することができるか。  
  
 *重要度*  
 このメッセージに関連付けられたユーザー定義重大度レベルです。 使用する場合*msg_id* RAISERROR で指定された重大度を sp_addmessage を使用して作成されたユーザー定義のメッセージを発生させるには、sp_addmessage で指定された重大度をオーバーライドします。  
  
 0 から 18 までの重大度レベルはどのユーザーでも指定できます。 19 から 25 までの重大度レベルは、固定サーバー ロールまたはユーザー ALTER TRACE 権限を持つ、sysadmin のメンバーでのみ指定できます。 重大度レベル 19 から 25 までは、WITH LOG オプションを必要とします。 0 より小さい重大度レベルは 0 と解釈されます。 25 より大きい重大度レベルは 25 と解釈されます。  
  
> [!CAUTION]  
>  重大度レベル 20 から 25 までは、致命的と見なされます。 この致命的な重大度レベルが発生した場合は、メッセージを受け取った後でクライアントの接続が終了し、エラーがエラー ログおよびアプリケーション ログに記録されます。  
  
 次の例に示すように、エラーに関連付けられた重大度の値を返すには -1 を指定できます。  
  
```  
RAISERROR (15600,-1,-1, 'mysp_CreateCustomer');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Msg 15600, Level 15, State 1, Line 1`   
 `An invalid parameter or option was specified for procedure 'mysp_CreateCustomer'.`  
  
 *状態*  
 0 ～ 255 の整数です。 負の値を 1 に既定値です。 255 より大きい値には使用できません。 
  
 同じユーザー定義エラーが複数の場所で発生する場合、それぞれの場所に対して一意の状態番号を使用すると、コードのどのセクションでエラーが発生しているのかを探すのに役立ちます。  
  
 *引数*  
 定義された変数の代入に使用されるパラメーターは、 *msg_str*またはに対応するメッセージ*msg_id*です。 書式引数は指定しなくても、複数指定してもかまいませんが、合計で 20 を超えることはできません。 各置換パラメーターには、ローカル変数、またはこれらのデータ型のいずれかを指定できます: **tinyint**、 **smallint**、 **int**、 **char**、 **varchar**、 **nchar**、 **nvarchar**、**バイナリ**、または**varbinary**です。 その他のデータ型はサポートされません。  
  
 *オプション*  
 エラーのカスタム オプションです。次の表のいずれかの値をとります。  
  
|値|Description|  
|-----------|-----------------|  
|LOG|エラー ログとアプリケーション ログのインスタンスに、エラーがログ記録、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]です。 エラー ログに記録されるエラーは、現在のところ最高 440 バイトに制限されています。 Sysadmin 固定サーバー ロールまたは ALTER TRACE 権限を持つユーザーのメンバーだけでは、WITH LOG を指定できます。<br /><br /> [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|  
|NOWAIT|クライアントにすぐにメッセージを送信します。<br /><br /> [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|  
|SETERROR|セット、@@ERRORおよび ERROR_NUMBER 値に*msg_id*または重大度レベルに関係なく、50000 します。<br /><br /> [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssSDS](../../includes/sssds-md.md)]|  
  
## <a name="remarks"></a>解説  
 RAISERROR によって生成されたエラーは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のコードによって生成されたエラーと同様に機能します。 RAISERROR で指定された値が報告されますで ERROR_LINE、ERROR_MESSAGE、ERROR_NUMBER、ERROR_PROCEDURE、ERROR_SEVERITY、ERROR_STATE、および @@ERRORシステム関数です。 TRY ブロックで 11 以上の重大度で RAISERROR を実行すると、RAISERROR は関連する CATCH ブロックに制御を渡します。 RAISERROR が次の条件で実行されると、呼び出し元にエラーが返されます。  
  
-   TRY ブロックのスコープの外で実行された場合  
  
-   TRY ブロックで 10 以下の重大度で実行された場合  
  
-   データベース接続を終了させる 20 以上の重大度で実行された場合  
  
 CATCH ブロックは、ERROR_NUMBER や ERROR_MESSAGE などのシステム関数を使用して CATCH ブロックを呼び出したエラーを、RAISERROR を使用して再度スローし、元のエラー情報を取得できます。 @@ERROR 1 から 10 までの重大度がメッセージの既定で 0 に設定します。  
  
 ときに*msg_id* sys.messages カタログ ビュー、RAISERROR のプロセスから利用可能なユーザー定義のメッセージが指定されたユーザー定義メッセージのテキストに適用されると、同じ規則を使用して、テキスト列からメッセージを指定します。使用して*msg_str*です。 ユーザー定義メッセージのテキストには変換指定を含めることができ、RAISERROR は引数値を変換指定にマップします。 ユーザー定義エラー メッセージを削除するには、ユーザー定義エラー メッセージと sp_dropmessage を追加するには、sp_addmessage を使用します。  
  
 RAISERROR は、呼び出し元のアプリケーションにメッセージを返すために、PRINT の代わりに使用することができます。 RAISERROR の機能に類似した代替文字をサポートしている、 **printf** 、C 標準ライブラリ内の関数間、 [!INCLUDE[tsql](../../includes/tsql-md.md)] PRINT ステートメントは返しません。 RAISERROR が TRY ブロックで 11 から 19 の重大度で実行され、関連する CATCH ブロックに制御を渡す間、PRINT ステートメントは TRY ブロックの影響を受けません。 CATCH ブロックを呼び出さずに TRY ブロックからのメッセージを返すには、重大度を 10 以下に指定して RAISERROR を使用します。  
  
 通常、最初の引数が最初の変換指定を置き換え、2 番目の引数が 2 番目の変換指定を置き換えるというように、連続する引数が連続する変換指定を置き換えます。 たとえば、次の`RAISERROR`ステートメントでは、最初の引数`N'number'`の最初の変換指定を置き換える`%s`; および 2 番目の引数の`5`の 2 番目の変換指定を置き換えます`%d.`  
  
```  
RAISERROR (N'This is message %s %d.', -- Message text.  
           10, -- Severity,  
           1, -- State,  
           N'number', -- First argument.  
           5); -- Second argument.  
-- The message text returned is: This is message number 5.  
GO  
```  
  
 変換指定の width または precision にアスタリスク (*) が指定されている場合、width または precision に使用される値は整数の引数値として指定されます。 この場合、1 つの変換指定で、width、precision、および置換値に対して 1 つずつ、最大 3 つまでの引数を使用できます。  
  
 たとえば、どちらも、次の`RAISERROR`ステートメントが同じ文字列を返します。 一方のステートメントでは引数リストで width と precision の値を指定し、もう一方のステートメントでは変換指定でこれらを指定しています。  
  
```  
RAISERROR (N'<\<%*.*s>>', -- Message text.  
           10, -- Severity,  
           1, -- State,  
           7, -- First argument used for width.  
           3, -- Second argument used for precision.  
           N'abcde'); -- Third argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
RAISERROR (N'<\<%7.3s>>', -- Message text.  
           10, -- Severity,  
           1, -- State,  
           N'abcde'); -- First argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
```  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-error-information-from-a-catch-block"></a>A. CATCH ブロックからエラー情報を返す  
 次のコード例は、使用する方法を示しています。`RAISERROR`内、`TRY`実行を、関連付けられている移動が発生するブロック`CATCH`ブロックします。 使用する方法も示します`RAISERROR`を呼び出したエラーに関する情報を返す、`CATCH`ブロックします。  
  
> [!NOTE]  
>  RAISERROR では、1 から 127 までの状態番号のエラーだけが生成されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]では状態番号 0 のエラーが発生する場合があるため、ERROR_STATE によって返されるエラーの状態番号は、RAISERROR の state パラメーターの値として渡す前に確認することをお勧めします。  
  
```  
BEGIN TRY  
    -- RAISERROR with severity 11-19 will cause execution to   
    -- jump to the CATCH block.  
    RAISERROR ('Error raised in TRY block.', -- Message text.  
               16, -- Severity.  
               1 -- State.  
               );  
END TRY  
BEGIN CATCH  
    DECLARE @ErrorMessage NVARCHAR(4000);  
    DECLARE @ErrorSeverity INT;  
    DECLARE @ErrorState INT;  
  
    SELECT   
        @ErrorMessage = ERROR_MESSAGE(),  
        @ErrorSeverity = ERROR_SEVERITY(),  
        @ErrorState = ERROR_STATE();  
  
    -- Use RAISERROR inside the CATCH block to return error  
    -- information about the original error that caused  
    -- execution to jump to the CATCH block.  
    RAISERROR (@ErrorMessage, -- Message text.  
               @ErrorSeverity, -- Severity.  
               @ErrorState -- State.  
               );  
END CATCH;  
```  
  
### <a name="b-creating-an-ad-hoc-message-in-sysmessages"></a>B. sys.messages 内でアドホック メッセージを作成する  
 次の例では、sys.messages カタログ ビューに格納されているメッセージを生成する方法を示します。 使用して、メッセージが sys.messages カタログ ビューに追加された、`sp_addmessage`メッセージ番号としてのシステム ストアド プロシージャ`50005`です。  
  
```  
sp_addmessage @msgnum = 50005,  
              @severity = 10,  
              @msgtext = N'<\<%7.3s>>';  
GO  
RAISERROR (50005, -- Message id.  
           10, -- Severity,  
           1, -- State,  
           N'abcde'); -- First argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
sp_dropmessage @msgnum = 50005;  
GO  
```  
  
### <a name="c-using-a-local-variable-to-supply-the-message-text"></a>C. ローカル変数を使用してメッセージ テキストを指定する  
 次のコード例は、ローカル変数を使用してメッセージ テキストを指定する方法を示しています、`RAISERROR`ステートメントです。  
  
```  
DECLARE @StringVariable NVARCHAR(50);  
SET @StringVariable = N'<\<%7.3s>>';  
  
RAISERROR (@StringVariable, -- Message text.  
           10, -- Severity,  
           1, -- State,  
           N'abcde'); -- First argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-returning-error-information-from-a-catch-block"></a>D. CATCH ブロックからエラー情報を返す  
 次のコード例は、使用する方法を示しています。`RAISERROR`内、`TRY`実行を、関連付けられている移動が発生するブロック`CATCH`ブロックします。 使用する方法も示します`RAISERROR`を呼び出したエラーに関する情報を返す、`CATCH`ブロックします。  
  
> [!NOTE]  
>  RAISERROR は、1 ~ 18 の状態とエラーを生成します。 PDW エンジン可能性がありますを上げると、エラー状態 0 のため、RAISERROR の state パラメーターの値として渡す前に、ERROR_STATE によって返されるエラー状態を確認することをお勧めします。  
  
```  
BEGIN TRY  
    -- RAISERROR with severity 11-18 will cause execution to   
    -- jump to the CATCH block.  
    RAISERROR ('Error raised in TRY block.', -- Message text.  
               16, -- Severity.  
               1 -- State.  
               );  
END TRY  
BEGIN CATCH  
    DECLARE @ErrorMessage NVARCHAR(4000);  
    DECLARE @ErrorSeverity INT;  
    DECLARE @ErrorState INT;  
  
    SET @ErrorMessage = ERROR_MESSAGE();  
    SET @ErrorSeverity = ERROR_SEVERITY();  
    SET @ErrorState = ERROR_STATE();  
  
    -- Use RAISERROR inside the CATCH block to return error  
    -- information about the original error that caused  
    -- execution to jump to the CATCH block.  
    RAISERROR (@ErrorMessage, -- Message text.  
               @ErrorSeverity, -- Severity.  
               @ErrorState -- State.  
               );  
END CATCH;  
```  
  
### <a name="e-using-a-local-variable-to-supply-the-message-text"></a>E. ローカル変数を使用してメッセージ テキストを指定する  
 次のコード例は、ローカル変数を使用してメッセージ テキストを指定する方法を示しています、`RAISERROR`ステートメントです。  
  
```  
DECLARE @StringVariable NVARCHAR(50);  
SET @StringVariable = N'<\<%7.3s>>';  
  
RAISERROR (@StringVariable, -- Message text.  
           10, -- Severity,  
           1, -- State,  
           N'abcde'); -- First argument supplies the string.  
-- The message text returned is: <<    abc>>.  
GO  
```  
  
## <a name="see-also"></a>参照  
 [宣言@local_variable(TRANSACT-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md) [組み込み関数 & #40 です。TRANSACT-SQL と #41 です。](~/t-sql/functions/functions.md)   
 [PRINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/print-transact-sql.md)   
 [sp_addmessage & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_dropmessage & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [sys.messages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages.md)   
 [xp_logevent & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/xp-logevent-transact-sql.md)   
 [@@ERROR &#40;Transact-SQL&#41;](../../t-sql/functions/error-transact-sql.md)   
 [ERROR_LINE &#40;Transact-SQL&#41;](../../t-sql/functions/error-line-transact-sql.md)   
 [ERROR_MESSAGE &#40;Transact-SQL&#41;](../../t-sql/functions/error-message-transact-sql.md)   
 [ERROR_NUMBER &#40;Transact-SQL&#41;](../../t-sql/functions/error-number-transact-sql.md)   
 [ERROR_PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/functions/error-procedure-transact-sql.md)   
 [ERROR_SEVERITY &#40;Transact-SQL&#41;](../../t-sql/functions/error-severity-transact-sql.md)   
 [ERROR_STATE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/error-state-transact-sql.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/try-catch-transact-sql.md)  
  
  



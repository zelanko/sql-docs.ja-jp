---
title: "WAITFOR (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WAITFOR
- WAITFOR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- TIME option
- delaying executions [SQL Server]
- batches [SQL Server], execution times
- stored procedures [SQL Server], executing
- DELAY
- time [SQL Server], execution delays
- blocking executions
- transactions [SQL Server], execution times
- WAITFOR statement
- timing executions
ms.assetid: 8e896e73-af27-4cae-a725-7a156733f3bd
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 003a48d9f4e7e36061674b60909f84957670f5d5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="waitfor-transact-sql"></a>WAITFOR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定された時間または期間に達するか、指定されたステートメントによって少なくとも 1 つの行が変更または返されるまで、バッチ、ストアド プロシージャ、またはトランザクションの実行をブロックします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
WAITFOR   
{  
    DELAY 'time_to_pass'   
  | TIME 'time_to_execute'   
  | [ ( receive_statement ) | ( get_conversation_group_statement ) ]   
    [ , TIMEOUT timeout ]  
}  
```  
  
## <a name="arguments"></a>引数  
 DELAY  
 バッチ、ストアド プロシージャ、またはトランザクションを実行する前に経過する必要のある、最大 24 時間までの指定された時間です。  
  
 '*time_to_pass*'  
 待機する時間の長さです。 *time_to_pass*の使用可能な形式のいずれかで指定できる**datetime**データ、またはそれをローカル変数として指定することができます。 日付を指定することはできません。そのため、日付の部分の**datetime**値は許可されていません。  
  
 TIME  
 バッチ、ストアド プロシージャ、またはトランザクションを実行するように指定された時間です。  
  
 '*time_to_execute*'  
 WAITFOR ステートメントが終了する時間です。 *time_to_execute*の使用可能な形式のいずれかで指定できる**datetime**データ、またはそれをローカル変数として指定することができます。 日付を指定することはできません。そのため、日付の部分の**datetime**値は許可されていません。  
  
 *receive_statement*  
 有効な RECEIVE ステートメントです。  
  
> [!IMPORTANT]  
>  指定された WAITFOR、 *receive_statement*にのみ適用[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ。 詳細については、次を参照してください。[受信 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/receive-transact-sql.md).  
  
 *get_conversation_group_statement*  
 有効な GET CONVERSATION GROUP ステートメントです。  
  
> [!IMPORTANT]  
>  指定された WAITFOR、 *get_conversation_group_statement*にのみ適用[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ。 詳細については、次を参照してください。 [GET CONVERSATION GROUP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/get-conversation-group-transact-sql.md).  
  
 タイムアウト*タイムアウト*  
 キューでメッセージの到着を待機する時間を、ミリ秒単位で指定します。  
  
> [!IMPORTANT]  
>  TIMEOUT が指定された WAITFOR は、[!INCLUDE[ssSB](../../includes/sssb-md.md)] メッセージに対してのみ適用できます。 詳細については、次を参照してください。[受信 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/receive-transact-sql.md)と[GET CONVERSATION GROUP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/get-conversation-group-transact-sql.md).  
  
## <a name="remarks"></a>解説  
 WAITFOR ステートメントを実行している間は、トランザクションが実行され、その他のリクエストは同じトランザクションの下で実行することはできません。  
  
 指定された時間から実際の遅延時間が異なる場合があります*time_to_pass*、 *time_to_execute*、または*タイムアウト*サーバーの利用状況のレベルに依存します。 時間のカウンターは、WAITFOR ステートメントに関連付けられたスレッドがスケジュールされた時点から開始します。 サーバーがビジーの場合、スレッドはすぐにスケジュールされない場合があります。したがって遅延時間は指定した時間よりも長くなることがあります。  
  
 WAITFOR はクエリのセマンティクスを変更しません。 クエリが行を返すことができない場合、WAITFOR は待機状態のままか、TIMEOUT が指定されている場合は TIMEOUT に達するまで待機します。  
  
 WAITFOR ステートメントでは、カーソルをオープンすることはできません。  
  
 WAITFOR ステートメントでは、ビューを定義することはできません。  
  
 クエリが query wait オプションの値を超えると、WAITFOR ステートメントの引数を実行せずに完了できます。 構成オプションの詳細については、次を参照してください。 [query wait サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-query-wait-server-configuration-option.md)です。 アクティブであり待機中の処理を表示する[sp_who](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)です。  
  
 各 WAITFOR ステートメントには、それに関連付けられたスレッドがあります。 同じサーバーに多くの WAITFOR ステートメントが指定されている場合、これらのステートメントの実行を待機することを中止できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、WAITFOR ステートメントに関連付けられたスレッドの数を監視し、スレッドが不足し始めるとランダムにこれらのスレッドのいくつかを選択し、終了させます。  
  
 WAITFOR ステートメントがアクセスしようとしている行セットが変更されないようにロックも設定されているトランザクション内で、WAITFOR のあるクエリを実行することにより、デッドロックを作成することができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、これらのシナリオを識別し、このようなデッドロックの機会が存在する場合は、空の結果セットを返します。  
  
> [!CAUTION]  
>  WAITFOR を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスの完了が遅くなり、その結果、アプリケーションでタイムアウト メッセージが表示される可能性があります。 必要に応じて、アプリケーション レベルで接続のタイムアウト設定を調整してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-waitfor-time"></a>A. WAITFOR TIME を使用する  
 次の例では、午後 10 時 20 分に msdb データベースでストアド プロシージャ `sp_update_job` を実行します。 (`22:20`).  
  
```  
EXECUTE sp_add_job @job_name = 'TestJob';  
BEGIN  
    WAITFOR TIME '22:20';  
    EXECUTE sp_update_job @job_name = 'TestJob',  
        @new_name = 'UpdatedJob';  
END;  
GO  
```  
  
### <a name="b-using-waitfor-delay"></a>B. WAITFOR DELAY を使用する  
 次の例では、ストアド プロシージャを 2 時間遅延して実行します。  
  
```  
BEGIN  
    WAITFOR DELAY '02:00';  
    EXECUTE sp_helpdb;  
END;  
GO  
```  
  
### <a name="c-using-waitfor-delay-with-a-local-variable"></a>C. ローカル変数と共に WAITFOR DELAY を使用する  
 次の例で、ローカル変数を使用する方法を示しています、`WAITFOR DELAY`オプション。 ここでは、変更可能な時間が経過するまで待機し、経過した時間の時、分、秒の長さに関する情報をユーザーに返すストアド プロシージャを作成します。  
  
```  
IF OBJECT_ID('dbo.TimeDelay_hh_mm_ss','P') IS NOT NULL  
    DROP PROCEDURE dbo.TimeDelay_hh_mm_ss;  
GO  
CREATE PROCEDURE dbo.TimeDelay_hh_mm_ss   
    (  
    @DelayLength char(8)= '00:00:00'  
    )  
AS  
DECLARE @ReturnInfo varchar(255)  
IF ISDATE('2000-01-01 ' + @DelayLength + '.000') = 0  
    BEGIN  
        SELECT @ReturnInfo = 'Invalid time ' + @DelayLength   
        + ',hh:mm:ss, submitted.';  
        -- This PRINT statement is for testing, not use in production.  
        PRINT @ReturnInfo   
        RETURN(1)  
    END  
BEGIN  
    WAITFOR DELAY @DelayLength  
    SELECT @ReturnInfo = 'A total time of ' + @DelayLength + ',   
        hh:mm:ss, has elapsed! Your time is up.'  
    -- This PRINT statement is for testing, not use in production.  
    PRINT @ReturnInfo;  
END;  
GO  
/* This statement executes the dbo.TimeDelay_hh_mm_ss procedure. */  
EXEC TimeDelay_hh_mm_ss '00:00:10';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `A total time of 00:00:10, in hh:mm:ss, has elapsed. Your time is up.`  
  
## <a name="see-also"></a>参照  
 [フロー制御言語 & #40 です。TRANSACT-SQL と #41 です。](~/t-sql/language-elements/control-of-flow.md)   
 [datetime & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/datetime-transact-sql.md)   
 [sp_who &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
  
  


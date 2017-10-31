---
title: "受信 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RECEIVE_TSQL
- RECEIVE
dev_langs:
- TSQL
helpviewer_keywords:
- queues [Service Broker], message retrieval
- messages [Service Broker], retrieving
- RECEIVE statement
- receiving messages
- retrieving messages
ms.assetid: 878c6c14-37ab-4b87-9854-7f8f42bac7dd
caps.latest.revision: 50
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4cf66234550d32eafae1029d80c0330499d75553
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="receive-transact-sql"></a>RECEIVE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キューから 1 つ以上のメッセージを受信します。 キューの保有期間の設定に応じて、キューからメッセージを削除するか、キューのメッセージの状態を更新します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
[ WAITFOR ( ]  
    RECEIVE [ TOP ( n ) ]   
        <column_specifier> [ ,...n ]  
        FROM <queue>  
        [ INTO table_variable ]  
        [ WHERE {  conversation_handle = conversation_handle  
                 | conversation_group_id = conversation_group_id } ]  
[ ) ] [ , TIMEOUT timeout ]  
[ ; ]  
  
<column_specifier> ::=  
{    *   
  |  { column_name | [ ] expression } [ [ AS ] column_alias ]  
  |  column_alias = expression   
}     [ ,...n ]   
  
<queue> ::=  
{  
    [ database_name . [ schema_name ] . | schema_name . ]  
        queue_name  
}  
  
```  
  
## <a name="arguments"></a>引数  
 WAITFOR  
 現在メッセージが存在しない場合、RECEIVE ステートメントは、キューにメッセージが到着するのを待機します。  
  
 上部 (  *n*  )  
 返されるメッセージの最大数を指定します。 この句を指定しない場合、ステートメントの条件に合致したすべてのメッセージが返されます。  
  
 \*  
 結果セットにキューのすべての列を含めます。  
  
 *column_name*  
 結果セットに含める列の名前です。  
  
 *式 (expression)*  
 列名、定数、関数、またはその組み合わせです。組み合わせる場合は演算子を使用します。  
  
 *column_alias*  
 結果セット内の列名に対する別名です。  
  
 FROM  
 取得するメッセージが含まれているキューを指定します。  
  
 *database_name*  
 メッセージを受信するキューが含まれているデータベースの名前です。 ない場合*データベース名*が提供される、既定値は、現在のデータベースです。  
  
 *schema_name*  
 メッセージを受信するキューを所有するスキーマの名前です。 ない場合*スキーマ名*が提供される、既定値は、現在のユーザーの既定のスキーマです。  
  
 *queue_name*  
 メッセージを受信するキューの名前です。  
  
 *Table_variable*  
 RECEIVE によってメッセージを格納するテーブル変数を指定します。 テーブル変数の列数は、メッセージ内の列数と同じである必要があります。 テーブル変数の各列のデータ型は、メッセージ内の対応する列のデータ型に暗黙的に変換できる必要があります。 INTO を指定しない場合、メッセージは結果セットとして返されます。  
  
 WHERE  
 受信するメッセージのメッセージ交換、またはメッセージ交換グループを指定します。 指定しない場合、次に使用可能なメッセージ交換グループからのメッセージが返されます。  
  
 conversation_handle = *conversation_handle*  
 受信するメッセージのメッセージ交換を指定します。 *メッセージ交換ハンドル*必要がありますを指定する、 **uniqueidentifer**、または型に変換できる**uniqueidentifier**です。  
  
 conversation_group_id = *conversation_group_id*  
 受信するメッセージのメッセージ交換グループを指定します。 *られているメッセージ交換グループ ID*提供する必要がありますする、 **uniqueidentifier**に変換できる型または**uniqueidentifier**です。  
  
 タイムアウト*タイムアウト*  
 ステートメントでメッセージを待機する時間をミリ秒で指定します。 この句は、WAITFOR 句と共にのみ使用できます。 この句が指定されていないか、タイムアウトが -**1**、待機時間は無制限です。 タイムアウトの時間を過ぎると、RECEIVE では空の結果セットが返されます。  
  
## <a name="remarks"></a>解説  
  
> [!IMPORTANT]  
>  RECEIVE ステートメントがバッチまたはストアド プロシージャで最初のステートメントではない場合は、前のステートメントの後にセミコロン (;) を指定する必要があります。  
  
 RECEIVE ステートメントでは、キューからメッセージが読み取られ、結果セットが返されます。 結果セットには 0 以上の行が含まれ、各行には 1 つのメッセージが含まれます。 INTO 句を使用しない場合および*column_specifier*値が割り当てられないローカル変数に、ステートメントが呼び出し元のプログラムに結果セットを返します。  
  
 RECEIVE ステートメントによって返されるメッセージには、さまざまなメッセージ型があります。 アプリケーションを使用して、 **message_type_name**をコードに各メッセージをルーティングする列が関連付けられているメッセージの種類を処理します。 メッセージ型には、次の 2 種類があります。  
  
-   CREATE MESSAGE TYPE ステートメントを使用して作成されたアプリケーション定義のメッセージ型。 によって、メッセージ交換で許可されているアプリケーション定義のメッセージ型のセットが定義されている、[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ交換に対して指定されているコントラクト。  
  
-   [!INCLUDE[ssSB](../../includes/sssb-md.md)]システムでは、その戻り値の状態やエラー情報をメッセージです。  
  
 キューにメッセージ保有期間が指定されていない場合、RECEIVE ステートメントでは受信したメッセージがキューから削除されます。 キューの保有期間の設定が ON、RECEIVE ステートメントの更新プログラムの場合、**ステータス**列**0**し、キューにメッセージのままにします。 RECEIVE ステートメントを含むトランザクションがロールバックされる場合は、そのトランザクションでキューに行われたすべての変更もロールバックされ、キューにメッセージが戻されます。  
  
 RECEIVE ステートメントで返されるメッセージは、すべて同じメッセージ交換グループに属しています。 RECEIVE ステートメントでは、ステートメントを含むトランザクションが完了するまで、返されるメッセージのメッセージ交換グループがロックされます。 RECEIVE ステートメントを持つメッセージが返されます、**ステータス**の**1 です。** RECEIVE ステートメントで返された結果セットは暗黙的に並べ替えられます。  
  
-   複数のメッセージ交換のメッセージが WHERE 句の条件を満たす場合、RECEIVE ステートメントでは、1 つのメッセージ交換のメッセージがすべて返されてから、他のメッセージ交換のメッセージが返されます。 メッセージ交換は、優先度レベルの降順に処理されます。  
  
-   指定されたメッセージ交換を昇順に、RECEIVE ステートメントでメッセージが返されます**message_sequence_number**順序。  
  
 RECEIVE ステートメントの WHERE 句は、いずれかを使用する 1 つの検索条件を含めることができますのみ**conversation_handle**または**conversation_group_id**です。 検索条件にキューの他の列を 1 つ以上含めることはできません。 **Conversation_handle**または**conversation_group_id**式を指定することはできません。 返されるメッセージのセットは、WHERE 句で指定した条件によって決まります。  
  
-   場合**conversation_handle**を指定すると、受信キューで使用できる指定されたメッセージ交換からのすべてのメッセージが返されます。  
  
-   場合**conversation_group_id**を指定すると、RECEIVE では、キュー、指定したメッセージ交換グループのメンバーである任意のメッセージ交換からで使用できるすべてのメッセージが返されます。  
  
-   WHERE 句がない場合は、RECEIVE によって、次の条件を満たすメッセージ交換グループに決定されます。  
  
    -   1 つ以上のメッセージがキュー内にある。  
  
    -   別の RECEIVE ステートメントによってロックされていない。  
  
    -   上記の条件を満たすすべてのメッセージ交換グループのうち、最も高い優先度レベルを持つ。  
  
     決定後、RECEIVE によって、選択されたメッセージ交換グループのメンバーである任意のメッセージ交換から、キュー内の使用できるメッセージがすべて返されます。  
  
 WHERE 句で指定したメッセージ交換ハンドルまたはメッセージ交換グループの識別子が存在しないか、指定したキューに関連付けられていない場合、RECEIVE ステートメントではエラーが返されます。  
  
 RECEIVE ステートメントで指定されたキューに、キューの状態を OFF に設定がある場合、ステートメントは失敗し、[!INCLUDE[tsql](../../includes/tsql-md.md)]エラーです。  
  
 WAITFOR 句を指定した場合、ステートメントは指定のタイムアウト時間が経過するか結果セットが使用可能になるまで待機します。 ステートメントが待機しているときに、キューが削除されたり、キューの状態が OFF に設定されると、ステートメントでは直ちにエラーが返されます。 RECEIVE ステートメントでメッセージ交換グループまたはメッセージ交換ハンドルを指定したが、メッセージ交換で使用するサービスが削除されたり、他のキューに移動された場合、RECEIVE ステートメントでは [!INCLUDE[tsql](../../includes/tsql-md.md)] エラーがレポートされます。  
  
 RECEIVE は、ユーザー定義の関数では無効です。  
  
 RECEIVE ステートメントには、優先度のスタベーション防止はありません。 1 つの RECEIVE ステートメントによってメッセージ交換グループがロックされ、優先度の低いメッセージ交換から大量のメッセージが取得されると、そのグループ内の優先度の高いメッセージ交換からメッセージを受信できなくなります。 このような状態を回避するには、優先度の低いメッセージ交換からメッセージを取得する場合に、TOP 句を使用して、各 RECEIVE ステートメントによって取得されるメッセージ数を制限します。  
  
## <a name="queue-columns"></a>キューの列  
 次の表は、キュー内の列を示します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**ステータス**|**tinyint**|メッセージの状態。 メッセージの受信コマンドによって返される場合、状態は常に**0**します。 キューのメッセージには、次のいずれかの値が含まれます。<br /><br /> **0**= 準備完了**1**受信したメッセージを =**2**= 未完了**3**= 保持されているメッセージを送信|  
|**優先順位**|**tinyint**|メッセージに適用されているメッセージ交換の優先度レベル。|  
|**queuing_order**|**bigint**|キュー内のメッセージの順序番号。|  
|**conversation_group_id**|**uniqueidentifier**|このメッセージが属するメッセージ交換グループの識別子。|  
|**conversation_handle**|**uniqueidentifier**|メッセージが属するメッセージ交換のハンドル。|  
|**message_sequence_number**|**bigint**|メッセージ交換内でのメッセージのシーケンス番号。|  
|**service_name**|**nvarchar(512)**|メッセージ交換の対象サービスの名前。|  
|**service_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メッセージ交換のサービスのオブジェクト識別子です。|  
|**service_contract_name**|**nvarchar (256)**|メッセージ交換が従うコントラクトの名前。|  
|**service_contract_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メッセージ交換が従うコントラクトのオブジェクト識別子です。|  
|**message_type_name**|**nvarchar (256)**|メッセージの形式を示すメッセージ型の名前。 メッセージは、アプリケーション メッセージ型か Broker システム メッセージのいずれかになります。|  
|**message_type_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メッセージを記述するメッセージの種類のオブジェクト識別子です。|  
|**検証**|**nchar(2)**|メッセージに使用される検証。<br /><br /> **E**= 空**N**= None**X**= XML|  
|**message_body**|**varbinary (max)**|メッセージの内容。|  
  
## <a name="permissions"></a>Permissions  
 メッセージを受信するには、キューに対する RECEIVE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-receiving-all-columns-for-all-messages-in-a-conversation-group"></a>A. メッセージ交換グループにあるすべてのメッセージの、すべての列を受信する  
 次の例では、[次へ] の使用可能なメッセージ交換グループのすべての使用可能なメッセージを受信する、`ExpenseQueue`キュー。 このステートメントでは、メッセージが結果セットとして返されます。  
  
```  
RECEIVE * FROM ExpenseQueue ;  
```  
  
### <a name="b-receiving-specified-columns-for-all-messages-in-a-conversation-group"></a>B. メッセージ交換グループにあるすべてのメッセージを対象として、指定した列を受信する  
 次の例では、[次へ] の使用可能なメッセージ交換グループのすべての使用可能なメッセージを受信する、`ExpenseQueue`キュー。 このステートメントでは、列 `conversation_handle`、`message_type_name`、`message_body` を含むメッセージが結果セットとして返されます。  
  
```  
RECEIVE conversation_handle, message_type_name, message_body  
FROM ExpenseQueue ;  
```  
  
### <a name="c-receiving-the-first-available-message-in-the-queue"></a>C. キューで最初に使用可能なメッセージを受信する  
 次の例では、`ExpenseQueue` キューから、最初に使用可能なメッセージを結果セットとして受信します。  
  
```  
RECEIVE TOP (1) * FROM ExpenseQueue ;  
```  
  
### <a name="d-receiving-all-messages-for-a-specified-conversation"></a>D. 指定したメッセージ交換のすべてのメッセージを受信する  
 次の例から指定したメッセージ交換のすべての利用可能なメッセージを受信する、`ExpenseQueue`キューにその結果セットです。  
  
```  
DECLARE @conversation_handle UNIQUEIDENTIFIER ;  
  
SET @conversation_handle = <retrieve conversation from database> ;  
  
RECEIVE *  
FROM ExpenseQueue  
WHERE conversation_handle = @conversation_handle ;  
```  
  
### <a name="e-receiving-messages-for-a-specified-conversation-group"></a>E. 指定したメッセージ交換グループのメッセージを受信する  
 次の例では、`ExpenseQueue` キューから、指定したメッセージ交換グループに属している使用可能なすべてのメッセージを結果セットとして受信します。  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
SET @conversation_group_id =   
    <retrieve conversation group ID from database> ;  
  
RECEIVE *  
FROM ExpenseQueue  
WHERE conversation_group_id = @conversation_group_id ;  
```  
  
### <a name="f-receiving-into-a-table-variable"></a>F. 受信したメッセージをテーブル変数に挿入する  
 次の例では、`ExpenseQueue` キューから、指定したメッセージ交換グループに属している使用可能なすべてのメッセージを受信して、テーブル変数に挿入します。  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
DECLARE @procTable TABLE(  
     service_instance_id UNIQUEIDENTIFIER,  
     handle UNIQUEIDENTIFIER,  
     message_sequence_number BIGINT,  
     service_name NVARCHAR(512),  
     service_contract_name NVARCHAR(256),  
     message_type_name NVARCHAR(256),  
     validation NCHAR,  
     message_body VARBINARY(MAX)) ;  
  
SET @conversation_group_id = <retrieve conversation group ID from database> ;  
  
RECEIVE TOP (1)  
    conversation_group_id,  
    conversation_handle,  
    message_sequence_number,  
    service_name,  
    service_contract_name,  
    message_type_name,  
    validation,  
    message_body  
FROM ExpenseQueue  
INTO @procTable  
WHERE conversation_group_id = @conversation_group_id ;  
```  
  
### <a name="g-receiving-messages-and-waiting-indefinitely"></a>G. メッセージを受信して無制限に待機する  
 次の例では、次の使用可能なメッセージ交換グループのすべての使用可能なメッセージを受信する、`ExpenseQueue`キュー。 このステートメントは、少なくとも 1 つのメッセージが使用可能になるまで待機し、その後すべてのメッセージ列を含む結果セットを返します。  
  
```  
WAITFOR (  
    RECEIVE *  
    FROM ExpenseQueue) ;  
```  
  
### <a name="h-receiving-messages-and-waiting-for-a-specified-interval"></a>H. メッセージを受信して指定の期間待機する  
 次の例では、次の使用可能なメッセージ交換グループのすべての使用可能なメッセージを受信する、`ExpenseQueue`キュー。 このステートメントは、60 秒が経過するか、少なくとも 1 つのメッセージが使用可能になるまで待機します。 少なくとも 1 つのメッセージが使用可能である場合、このステートメントはすべてのメッセージ列を含む結果セットを返します。 それ以外の場合は、空の結果セットを返します。  
  
```  
WAITFOR (  
    RECEIVE *  
    FROM ExpenseQueue ),  
TIMEOUT 60000 ;  
```  
  
### <a name="i-receiving-messages-modifying-the-type-of-a-column"></a>I. メッセージを受信して列の型を変更する  
 次の例では、次の使用可能なメッセージ交換グループのすべての使用可能なメッセージを受信する、`ExpenseQueue`キュー。 メッセージ型でメッセージに XML ドキュメントが含まれることが指定されている場合、このステートメントでは、メッセージ本文が XML に変換されます。  
  
```  
WAITFOR (  
    RECEIVE message_type_name,  
        CASE  
            WHEN validation = 'X' THEN CAST(message_body as XML)  
            ELSE NULL  
         END AS message_body   
         FROM ExpenseQueue ),  
TIMEOUT 60000 ;  
```  
  
### <a name="j-receiving-a-message-extracting-data-from-the-message-body-retrieving-conversation-state"></a>J. メッセージを受信し、メッセージ本文からデータを抽出して、メッセージ交換の状態を取得する  
 次の例では、`ExpenseQueue` キューから、次に使用できるメッセージ交換グループに属している、次に使用可能なメッセージを取得します。 ときに、メッセージは型`//Adventure-Works.com/Expenses/SubmitExpense`ステートメントは、メッセージ本文から従業員 ID とアイテムの一覧を抽出します。 ステートメントからのメッセージ交換の状態も取得する、`ConversationState`テーブル。  
  
```  
WAITFOR(  
    RECEIVE   
    TOP(1)  
      message_type_name,  
      COALESCE(  
           (SELECT TOP(1) ConversationState  
            FROM CurrentConversations AS cc  
            WHERE cc.ConversationHandle = conversation_handle),  
           'NEW')  
      AS ConversationState,  
      COALESCE(  
          (SELECT TOP(1) ErrorCount  
           FROM CurrentConversations AS cc  
           WHERE cc.ConversationHandle = conversation_handle),   
           0)  
      AS ConversationErrors,  
      CASE WHEN message_type_name = N'//Adventure-Works.com/Expenses/SubmitExpense'  
          THEN CAST(message_body AS XML).value(  
                'declare namespace rpt = "http://Adventure-Works.com/schemas/expenseReport"  
                   (/rpt:ExpenseReport/rpt:EmployeeID)[1]', 'nvarchar(20)')  
         ELSE NULL  
      END AS EmployeeID,  
      CASE WHEN message_type_name = N'//Adventure-Works.com/Expenses/SubmitExpense'  
          THEN CAST(message_body AS XML).query(  
                'declare namespace rpt = "http://Adventure-Works.com/schemas/expenseReport"   
                     /rpt:ExpenseReport/rpt:ItemDetail')  
          ELSE NULL  
      END AS ItemList  
    FROM ExpenseQueue   
), TIMEOUT 60000 ;  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN DIALOG CONVERSATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [BEGIN CONVERSATION TIMER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/begin-conversation-timer-transact-sql.md)   
 [END CONVERSATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/end-conversation-transact-sql.md)   
 [コントラクト &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-contract-transact-sql.md)   
 [メッセージの種類 &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-message-type-transact-sql.md)   
 [SEND & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/send-transact-sql.md)   
 [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md)   
 [ALTER QUEUE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-queue-transact-sql.md)   
 [DROP QUEUE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-queue-transact-sql.md)  
  
  


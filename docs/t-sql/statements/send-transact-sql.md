---
title: "送信 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- SEND_ON_CONVERSATION_TSQL
- ON_CONVERSATION_TSQL
- SEND
- SEND_TSQL
- SEND ON CONVERSATION
- ON CONVERSATION
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker], message sending
- SEND statement
- messages [Service Broker], sending
- sending messages
ms.assetid: b6e66aeb-1714-4c2b-b7c2-d386d77b0d46
caps.latest.revision: 32
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b149c44df4fb417ed143147cd38b4ae838318ece
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="send-transact-sql"></a>SEND (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つ以上の既存のメッセージ交換を使用して、メッセージを送信します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SEND  
   ON CONVERSATION [(]conversation_handle [,.. @conversation_handle_n][)]  
   [ MESSAGE TYPE message_type_name ]  
   [ ( message_body_expression ) ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 メッセージ交換で*conversation_handle [..@conversation_handle_n]*  
 メッセージが属するメッセージ交換を指定します。 *Conversation_handle*は有効なメッセージ交換の識別子を含める必要があります。 同じメッセージ交換ハンドルを複数回使用することはできません。  
  
 メッセージの種類*message_type_name*  
 送信したメッセージのメッセージ型を指定します。 このメッセージ型は、これらのメッセージ交換で使用されるサービス コントラクトに含まれている必要があります。 これらのコントラクトによって、メッセージ型をメッセージ交換の発信側から送信できます。 たとえば、メッセージ交換の対象サービスは SENT BY TARGET または SENT BY ANY としてコントラクトに指定されたメッセージのみを送信できます。 この句が省略されると、メッセージは DEFAULT のメッセージ型になります。  
  
 *message_body_expression*  
 メッセージ本文を表す式を指定します。 *Message_body_expression*は省略可能です。 ただし場合、 *message_body_expression*が存在する変換できる型の式があります**varbinary (max)**です。 この式が NULL になることはありません。 この句が省略されると、メッセージ本文は空になります。  
  
## <a name="remarks"></a>解説  
  
> [!IMPORTANT]  
>  SEND ステートメントがバッチまたはストアド プロシージャで最初のステートメントではない場合は、前のステートメントの後にセミコロン (;) を指定する必要があります。  
  
 SEND ステートメントは 1 つまたは複数の一方の端にあるサービスからメッセージを送信[!INCLUDE[ssSB](../../includes/sssb-md.md)]これらのメッセージ交換の相手側のサービスにメッセージを交換します。 RECEIVE ステートメントは、対象サービスに関連付けられたキューから送信されたメッセージを取得するのには使用されます。  
  
 ON CONVERSATION 句に指定されるメッセージ交換ハンドルのソースは、次の 3 つのうちいずれかです。  
  
-   別のサービスから受信したメッセージに対する応答ではないメッセージを送信する場合、メッセージ交換を作成した BEGIN DIALOG ステートメントから返されるメッセージ交換ハンドルを使用します。  
  
-   別のサービスから以前に受信したメッセージに対して応答のメッセージを送信する場合、元のメッセージを返した RECEIVE ステートメントから返されるメッセージ交換ハンドルを使用します。  
  
 多くの場合、SEND ステートメントを含むコードは別のメッセージ交換ハンドルを指定して、BEGIN DIALOG または受信のいずれかのステートメントを含むコードです。 そのような場合、メッセージ交換ハンドルは、SEND ステートメントが含まれたコードに渡される状態情報のデータ アイテムのいずれかである必要があります。  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]の別のインスタンス内のサービスに送信されるメッセージは、リモート インスタンスのサービス キューに送信できるようになるまでの間、現在のデータベースの転送キューに格納されます。 同じインスタンス内のサービスに送信されたメッセージ、[!INCLUDE[ssDE](../../includes/ssde-md.md)]これらのサービスに関連付けられたキューに直接配置されます。 ローカル メッセージを転送先サービス キューに直接配置できない条件がある場合は、その条件が解決されるまで転送キューに格納されることがあります。 これが発生するのは、特定のエラーが発生した場合や、転送先サービス キューが非アクティブな場合などです。 使用することができます、 **sys.transmission_queue**システム ビューを転送キューにメッセージを参照してください。  
  
 SEND はアトミック ステートメントです。つまり、メッセージ交換がエラー状態の場合などに、複数のメッセージ交換でメッセージを送信する SEND ステートメントが失敗した場合、メッセージは転送キューまたは転送先サービス キューに格納されません。  
  
 Service Broker は、同じ SEND ステートメントを使用して複数のメッセージ交換で送信されるメッセージの格納と転送を最適化します。  
  
 インスタンスの転送キュー内のメッセージは、次の内容に基づいて順番に転送されます。  
  
-   関連するメッセージ交換エンドポイントの優先度レベル  
  
-   優先度レベル内では、メッセージ交換における送信順序  
  
 メッセージ交換の優先度で指定された優先順位は、HONOR_BROKER_PRIORITY データベース オプションが ON に設定されている場合にのみ、転送キュー内のメッセージに割り当てられます。 HONOR_BROKER_PRIORITY データベース オプションが OFF に設定されている場合、そのデータベースの転送キューに配置されたすべてのメッセージには、既定の優先度レベル 5 が割り当てられます。 同じインスタンス内のサービス キューに直接メッセージを格納する場所、送信に優先度レベルは適用されません、[!INCLUDE[ssDE](../../includes/ssde-md.md)]です。  
  
 SEND ステートメントは、メッセージを送信する各メッセージ交換を個別にロックし、メッセージ交換ごとの順序でメッセージが配信されるようにします。  
  
 SEND は、ユーザー定義の関数では無効です。  
  
## <a name="permissions"></a>Permissions  
 メッセージを送信するには、現在のユーザーは、メッセージを送信するすべてのサービスのキューに対する RECEIVE 権限を持っている必要があります。  
  
## <a name="examples"></a>使用例  
 次の例では、ダイアログを開始し、ダイアログ ボックスで、XML メッセージを送信します。 例では、メッセージを送信するには xml オブジェクトに変換します**varbinary (max)**です。  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER,  
        @ExpenseReport XML ;  
  
SET @ExpenseReport = < construct message as appropriate for the application > ;  
  
BEGIN DIALOG @dialog_handle  
FROM SERVICE [//Adventure-Works.com/Expenses/ExpenseClient]  
TO SERVICE '//Adventure-Works.com/Expenses'  
ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseProcessing] ;  
  
SEND ON CONVERSATION @dialog_handle  
    MESSAGE TYPE [//Adventure-Works.com/Expenses/SubmitExpense]  
    (@ExpenseReport) ;  
```  
  
 次の例では、3 つのダイアログを開始し、各ダイアログ上の XML メッセージを送信します。  
  
```  
DECLARE @dialog_handle1 UNIQUEIDENTIFIER,  
        @dialog_handle2 UNIQUEIDENTIFIER,  
        @dialog_handle3 UNIQUEIDENTIFIER,  
        @OrderMsg XML ;  
  
SET @OrderMsg = < construct message as appropriate for the application > ;  
  
BEGIN DIALOG @dialog_handle1  
FROM SERVICE [//InitiatorDB/InitiatorService]  
TO SERVICE '//TargetDB1/TargetService’  
ON CONTRACT [//AllDBs/OrderProcessing] ;  
  
BEGIN DIALOG @dialog_handle2  
FROM SERVICE [//InitiatorDB/InitiatorService]  
TO SERVICE '//TargetDB2/TargetService’  
ON CONTRACT [//AllDBs/OrderProcessing] ;  
  
BEGIN DIALOG @dialog_handle3  
FROM SERVICE [//InitiatorDB/InitiatorService]  
TO SERVICE '//TargetDB3/TargetService’  
ON CONTRACT [//AllDBs/OrderProcessing] ;  
  
SEND ON CONVERSATION (@dialog_handle1, @dialog_handle2, @dialog_handle3)  
    MESSAGE TYPE [//AllDBs/OrderMsg]  
    (@OrderMsg) ;  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN DIALOG CONVERSATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [END CONVERSATION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/end-conversation-transact-sql.md)   
 [受信 (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/receive-transact-sql.md)   
 [sys.transmission_queue & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)  
  
  


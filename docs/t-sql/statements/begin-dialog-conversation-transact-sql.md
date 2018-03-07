---
title: "BEGIN DIALOG CONVERSATION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DIALOG CONVERSATION
- DIALOG
- BEGIN_DIALOG_TSQL
- BEGIN_DIALOG_CONVERSATION_TSQL
- DIALOG_CONVERSATION_TSQL
- DIALOG_TSQL
- BEGIN DIALOG
- BEGIN DIALOG CONVERSATION
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker]
- beginning dialogs
- dialogs [Service Broker], beginning
- BEGIN DIALOG CONVERSATION statement
- cryptography [SQL Server], conversations
- opening conversations
- encryption [SQL Server], conversations
- starting conversations
ms.assetid: 8e814f9d-77c1-4906-b8e4-668a86fc94ba
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a2ece31010207b6044504f099c11443a2fec0fa2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="begin-dialog-conversation-transact-sql"></a>BEGIN DIALOG CONVERSATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  あるサービスから別のサービスに対してダイアログを開始します。 ダイアログとは、2 つのサービスの間で順序どおりにメッセージを 1 回だけ交換する (exactly-once-in-order) メッセージ交換のことです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
BEGIN DIALOG [ CONVERSATION ] @dialog_handle  
   FROM SERVICE initiator_service_name  
   TO SERVICE 'target_service_name'  
       [ , { 'service_broker_guid' | 'CURRENT DATABASE' }]   
   [ ON CONTRACT contract_name ]  
   [ WITH  
   [  { RELATED_CONVERSATION = related_conversation_handle   
      | RELATED_CONVERSATION_GROUP = related_conversation_group_id } ]   
   [ [ , ] LIFETIME = dialog_lifetime ]   
   [ [ , ] ENCRYPTION = { ON | OFF }  ] ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 **@** *dialog_handle*  
 システムで生成される、新しいダイアログ用のダイアログ ハンドルを格納する変数です。この値は、BEGIN DIALOG CONVERSATION ステートメントによって返されます。 型の変数がある必要があります**uniqueidentifier**です。  
  
 FROM SERVICE *initiator_service_name*  
 ダイアログを開始するサービスを指定します。 現在のデータベースにあるサービスの名前を指定する必要があります。 発信先サービスから返されるメッセージ、およびこのメッセージ交換用に Service Broker によって作成されるメッセージは、発信側サービス用に指定したキューで受信されます。  
  
 サービスに**'***target_service_name***'**  
 ダイアログの発信先となるサービスを指定します。 *Target_service_name*の種類は**nvarchar (256)**です。 [!INCLUDE[ssSB](../../includes/sssb-md.md)]一致するように、バイトごとの比較を使用して、 *target_service_name*文字列。 つまり、この場合、大文字小文字は区別され、現在の照合順序は考慮されません。  
  
 *service_broker_guid*  
 発信先サービスをホストするデータベースを指定します。 提供することによって、特定のデータベースと通信できる 1 つ以上のデータベースが対象となるサービスのインスタンスをホストする場合、 *service_broker_guid*です。  
  
 *Service_broker_guid*の種類は**nvarchar (128)**です。 検索する、 *service_broker_guid*データベースは、データベースで次のクエリを実行します。  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID() ;  
```  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 **'**CURRENT DATABASE**'**  
 メッセージ交換が使用することを指定、 *service_broker_guid*現在のデータベースです。  
  
 ON CONTRACT *contract_name*  
 メッセージ交換が従うコントラクトを指定します。 コントラクトは、現在のデータベース内に存在している必要があります。 発信先サービスで、指定したコントラクトに従った新しいメッセージ交換が受け入れられない場合、[!INCLUDE[ssSB](../../includes/sssb-md.md)] ではそのメッセージ交換に関するエラー メッセージが返されます。 この句を省略すると、メッセージ交換がという名前のコントラクトを従う**既定**です。  
  
 RELATED_CONVERSATION **=***related_conversation_handle*  
 新しいダイアログを追加する既存のメッセージ交換グループを指定します。 この句が存在する場合、新しいダイアログ ボックスが属するで指定したダイアログと同じメッセージ交換グループ*related_conversation_handle*です。 *Related_conversation_handle*型に暗黙的に変換できる型でなければなりません**uniqueidentifier**です。 場合、ステートメントが失敗、 *related_conversation_handle*は既存のダイアログを参照していません。  
  
 RELATED_CONVERSATION_GROUP **=***related_conversation_group_id*  
 新しいダイアログを追加する既存のメッセージ交換グループを指定します。 この句が存在する場合は、新しいダイアログは、によって指定されたメッセージ交換グループに追加されます*related_conversation_group_id*です。 *Related_conversation_group_id*型に暗黙的に変換できる型でなければなりません**uniqueidentifier**です。 場合*related_conversation_group_id*は参照、次のように既存のメッセージ交換グループ、service broker ではなくを作成、新しいメッセージ交換グループに、指定した*related_conversation_group_id*と新しいダイアログ ボックスをそのメッセージ交換グループに関連しています。  
  
 LIFETIME **=***dialog_lifetime*  
 ダイアログを開いたままにする最長時間を指定します。 ダイアログを正常に完了するには、有効期間の終了までに、双方のエンドポイントが明示的にダイアログを終了する必要があります。 *Dialog_lifetime*値を秒単位で表す必要があります。 型の有効期間は**int**です。LIFETIME 句を指定しないと、ダイアログの有効期間はの最大値、 **int**データ型。  
  
 ENCRYPTION  
 インスタンスの外部に送信するときに、このダイアログ ボックスで送受信されるメッセージを暗号化する必要があるかどうかを指定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 暗号化する必要がありますのあるダイアログは、*セキュリティで保護されたダイアログ*です。 場合暗号化 = ON および暗号化をサポートするために必要な証明書を構成、[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ交換でエラー メッセージが返されます。 場合暗号化 = OFF、リモート サービス バインドが構成されている場合、暗号化が使用される、 *target_service_name*です。 それ以外の場合のメッセージが暗号化されずに送信されます。 この句を指定しない場合、既定値の ON が使用されます。  
  
> [!NOTE]  
>  同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにあるサービス間で交換されるメッセージは暗号化されません。 ただし、メッセージ交換を行うサービスが異なるデータベースにある場合は、暗号化したメッセージ交換を行うために、データベースのマスター キーと暗号化の証明書が必要になります。 これらを用意しておくと、メッセージ交換中にデータベースの 1 つが別のインスタンスに移動した場合でも、メッセージ交換を続行できます。  
  
## <a name="remarks"></a>解説  
 すべてのメッセージはメッセージ交換の一部になります。 したがって、発信先サービスにメッセージを送信するには、発信側サービスで、発信先サービスとのメッセージ交換を開始する必要があります。 BEGIN DIALOG CONVERSATION ステートメントで指定した情報は文字である上のアドレスに似ています[!INCLUDE[ssSB](../../includes/sssb-md.md)]情報を使用して、正しいサービスにメッセージを配信します。 TO SERVICE 句で指定するサービスは、メッセージの送信先アドレスです。 FROM SERVICE 句で指定するサービスは、メッセージの返信先アドレスです。  
  
 メッセージ交換の発信先で BEGIN DIALOG CONVERSATION を呼び出す必要はありません。 [!INCLUDE[ssSB](../../includes/sssb-md.md)]発信側からメッセージ交換の最初のメッセージが到着したときに、メッセージ交換ターゲット データベースを作成します。  
  
 ダイアログを開始すると、発信側サービスのデータベースにメッセージ交換のエンドポイントは作成されますが、発信先サービスをホストしているインスタンスへのネットワーク接続は作成されません。 最初のメッセージが送信されるまでは、[!INCLUDE[ssSB](../../includes/sssb-md.md)] でダイアログの発信先との通信は確立されません。  
  
 関連するメッセージ交換または関連するメッセージ交換グループの場合は、BEGIN DIALOG CONVERSATION ステートメントが指定されなかったときに[!INCLUDE[ssSB](../../includes/sssb-md.md)]新しいメッセージ交換用の新しいメッセージ交換グループを作成します。  
  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ交換の任意のグループ化は許可されません。 メッセージ交換グループのすべてのメッセージ交換に対しては、FROM 句を使って、メッセージ交換の発信側または発信先のサービスを指定する必要があります。  
  
 BEGIN DIALOG CONVERSATION コマンドが含まれているメッセージ交換グループをロック、 *dialog_handle*が返されます。 コマンドに RELATED_CONVERSATION_GROUP 句、メッセージ交換グループが含まれてとき*dialog_handle*で指定されたメッセージ交換グループ、 *related_conversation_group_id*パラメーター。 コマンドに RELATED_CONVERSATION 句、メッセージ交換グループが含まれてとき*dialog_handle*メッセージ交換グループに関連付けられている、 *related_conversation_handle*指定します。  
  
 BEGIN DIALOG CONVERSATION は、ユーザー定義の関数では無効です。  
  
## <a name="permissions"></a>権限  
 ダイアログを開始するには、現在のユーザーに、コマンドの FROM 句で指定したサービス用のキューに対する RECEIVE 権限と、指定したコントラクトの REFERENCES 権限が与えられている必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-beginning-a-dialog"></a>A. ダイアログを開始する  
 次の例は、ダイアログ メッセージ交換を開始し、ダイアログの識別子を格納`@dialog_handle.`、`//Adventure-Works.com/ExpenseClient`サービスは、ダイアログの発信側と`//Adventure-Works.com/Expenses`サービスには、ダイアログ ボックスのターゲットです。 このダイアログはコントラクト `//Adventure-Works.com/Expenses/ExpenseSubmission` に従います。  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission] ;  
```  
  
### <a name="b-beginning-a-dialog-with-an-explicit-lifetime"></a>B. 有効期間を明示してダイアログを開始する  
 次の例では、ダイアログ メッセージ交換を開始し、`@dialog_handle` にダイアログの識別子を格納します。 `//Adventure-Works.com/ExpenseClient` サービスはダイアログの発信側で、`//Adventure-Works.com/Expenses` サービスはダイアログの発信先です。 このダイアログはコントラクト `//Adventure-Works.com/Expenses/ExpenseSubmission` に従います。 ダイアログ ボックスが内で END CONVERSATION コマンドによってクローズされていないかどうかは`60`(秒単位)、ブローカーは、エラー ダイアログを終了します。  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH LIFETIME = 60 ;  
```  
  
### <a name="c-beginning-a-dialog-with-a-specific-broker-instance"></a>C. 特定のブローカー インスタンスとのダイアログを開始する  
 次の例では、ダイアログ メッセージ交換を開始し、`@dialog_handle` にダイアログの識別子を格納します。 `//Adventure-Works.com/ExpenseClient` サービスはダイアログの発信側で、`//Adventure-Works.com/Expenses` サービスはダイアログの発信先です。 このダイアログはコントラクト `//Adventure-Works.com/Expenses/ExpenseSubmission` に従います。 ここでは、ブローカーによって、このダイアログから GUID `a326e034-d4cf-4e8b-8d98-4d7e1926c904.` で指定されたブローカーにメッセージがルートされます。  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses',   
              'a326e034-d4cf-4e8b-8d98-4d7e1926c904'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission] ;  
```  
  
### <a name="d-beginning-a-dialog-and-relating-it-to-an-existing-conversation-group"></a>D. ダイアログを開始し、そのダイアログを既存のメッセージ交換グループに関連付ける  
 次の例では、ダイアログ メッセージ交換を開始し、`@dialog_handle` にダイアログの識別子を格納します。 `//Adventure-Works.com/ExpenseClient` サービスはダイアログの発信側で、`//Adventure-Works.com/Expenses` サービスはダイアログの発信先です。 このダイアログはコントラクト `//Adventure-Works.com/Expenses/ExpenseSubmission` に従います。 ブローカーによって識別されるメッセージ交換グループにダイアログが関連付けられます`@conversation_group_id`新しいメッセージ交換グループを作成する代わりにします。  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER ;  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
SET @conversation_group_id = <retrieve conversation group ID from database>  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH RELATED_CONVERSATION_GROUP = @conversation_group_id ;  
```  
  
### <a name="e-beginning-a-dialog-with-an-explicit-lifetime-and-relating-the-dialog-to-an-existing-conversation"></a>E. 有効期間を明示してダイアログを開始し、そのダイアログと既存のメッセージ交換を関連付ける  
 次の例では、ダイアログ メッセージ交換を開始し、`@dialog_handle` にダイアログの識別子を格納します。 `//Adventure-Works.com/ExpenseClient` サービスはダイアログの発信側で、`//Adventure-Works.com/Expenses` サービスはダイアログの発信先です。 このダイアログはコントラクト `//Adventure-Works.com/Expenses/ExpenseSubmission` に従います。 新しいダイアログは、`@existing_conversation_handle` が属するメッセージ交換グループと同じメッセージ交換グループに属します。 ダイアログ ボックスが内で END CONVERSATION コマンドによってクローズされていないかどうかは`600`秒、[!INCLUDE[ssSB](../../includes/sssb-md.md)]エラー ダイアログを終了します。  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER  
DECLARE @existing_conversation_handle UNIQUEIDENTIFIER  
  
SET @existing_conversation_handle = <retrieve conversation handle from database>  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH RELATED_CONVERSATION = @existing_conversation_handle  
   LIFETIME = 600 ;  
```  
  
### <a name="f-beginning-a-dialog-with-optional-encryption"></a>F. 暗号化のオプションを指定してダイアログを開始する  
 次の例では、ダイアログを開始し、`@dialog_handle` にダイアログの識別子を格納します。 `//Adventure-Works.com/ExpenseClient` サービスはダイアログの発信側で、`//Adventure-Works.com/Expenses` サービスはダイアログの発信先です。 このダイアログはコントラクト `//Adventure-Works.com/Expenses/ExpenseSubmission` に従います。 この例のメッセージ交換では、暗号化が利用できない場合に、暗号化していないメッセージをネットワークを介して送信できます。  
  
```  
DECLARE @dialog_handle UNIQUEIDENTIFIER  
  
BEGIN DIALOG CONVERSATION @dialog_handle  
   FROM SERVICE [//Adventure-Works.com/ExpenseClient]  
   TO SERVICE '//Adventure-Works.com/Expenses'  
   ON CONTRACT [//Adventure-Works.com/Expenses/ExpenseSubmission]  
   WITH ENCRYPTION = OFF ;  
```  
  
## <a name="see-also"></a>参照  
 [BEGIN CONVERSATION TIMER &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/begin-conversation-timer-transact-sql.md)   
 [END CONVERSATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/end-conversation-transact-sql.md)   
 [メッセージ交換の移動 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/move-conversation-transact-sql.md)   
 [sys.conversation_endpoints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)  
  
  

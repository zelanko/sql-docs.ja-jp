---
title: "キュー (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- QUEUE_TSQL
- CREATE QUEUE
- QUEUE
- CREATE_QUEUE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE QUEUE statement
- internal activation [Service Broker]
- stored procedure activation [Service Broker]
- message retention [Service Broker]
- unavailable queues [Service Broker]
- activation stored procedures [Service Broker]
- queues [Service Broker], creating
ms.assetid: fce80faf-2bdc-475d-8ca1-31438ed41fb0
caps.latest.revision: 67
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 59e7140970b80d2be64c15aefebca90bf45977e7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-queue-transact-sql"></a>CREATE QUEUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースに新しいキューを作成します。 キューにはメッセージが格納されます。 サービス用のメッセージを受信すると、そのメッセージは [!INCLUDE[ssSB](../../includes/sssb-md.md)] によって、サービスに関連付けられているキューに格納されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
CREATE QUEUE <object>  
   [ WITH  
     [ STATUS = { ON | OFF }  [ , ] ]  
     [ RETENTION = { ON | OFF } [ , ] ]   
     [ ACTIVATION (  
         [ STATUS = { ON | OFF } , ]   
           PROCEDURE_NAME = <procedure> ,  
           MAX_QUEUE_READERS = max_readers ,   
           EXECUTE AS { SELF | 'user_name' | OWNER }   
            ) [ , ] ]  
     [ POISON_MESSAGE_HANDLING (  
         [ STATUS = { ON | OFF } ] ) ] 
    ]  
     [ ON { filegroup | [ DEFAULT ] } ]  
[ ; ]  
  
<object> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]  
        queue_name  
}   
  
<procedure> ::=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]  
        stored_procedure_name  
}  
  
```  
  
## <a name="arguments"></a>引数  
 *database_name* (オブジェクト)  
 新しいキューを作成するデータベースの名前を指定します。 *database_name*既存のデータベースの名前を指定する必要があります。 ときに*database_name*が提供されていない場合、現在のデータベースにキューを作成します。  
  
 *schema_name* (オブジェクト)  
 新しいキューが所属するスキーマの名前を指定します。 省略すると、ステートメントを実行するユーザーの既定のスキーマが使用されます。 Sysadmin 固定サーバー ロールのメンバーが CREATE QUEUE ステートメントが実行されるかによって指定されたデータベースの固定データベース ロールを db_dbowner または db_ddladmin のメンバー場合*database_name*、 *schema_name* 、現在の接続のログインに関連付けられている以外のスキーマを指定できます。 それ以外の場合、 *schema_name*ステートメントを実行しているユーザーの既定のスキーマをする必要があります。  
  
 *queue_name*  
 作成するキューの名前を指定します。 この名前は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 識別子のガイドラインに従っている必要があります。  
  
 STATUS (Queue)   
 キューが使用可能 (ON) か、使用不可能 (OFF) かを指定します。 キューが使用不可能な場合、キューにメッセージを追加したり、キューからメッセージを削除することはできません。 ALTER QUEUE ステートメントによってキューが使用可能になるまでキューにメッセージが届かないようにする場合は、キューを使用不可能な状態で作成できます。 この句を省略すると、既定値の ON が使用され、キューは使用可能になります。  
  
 RETENTION   
 キューのメッセージ保有期間の設定を指定します。 場合は保有期間に、このキューを使用するメッセージ交換で送信または受信がキューに保持されて、メッセージ交換が終了するまでのすべてのメッセージを = です。 このことにより、監査目的でメッセージを保有したり、エラーが発生した場合に補正するトランザクションを実行することができます。 この句を指定しない場合、保有期間の設定は既定で OFF になります。  
  
> [!NOTE]  
>  保有期間設定 = ON パフォーマンスが低下することができます。 この設定はアプリケーションに必要な場合にのみ使用してください。  
  
 ACTIVATION  
 このキュー内のメッセージを処理するために開始する必要があるストアド プロシージャの情報を指定します。  
  
 STATUS (Activation)   
 指定するかどうか[!INCLUDE[ssSB](../../includes/sssb-md.md)]ストアド プロシージャを開始します。 STATUS = ON の場合は、現在実行中のプロシージャの数が MAX_QUEUE_READERS より少なく、ストアド プロシージャによるメッセージの受信よりも早くメッセージがキューに到着する場合に、PROCEDURE_NAME で指定されるストアド プロシージャがキューによって開始されます。 STATUS = OFF の場合は、キューによってストアド プロシージャは開始されません。 この句を指定しない場合、既定値は ON になります。  
  
 PROCEDURE_NAME =\<手順 >  
 このキュー内のメッセージを処理するために開始するストアド プロシージャの名前を指定します。 この値である必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子。  
  
 *database_name*(プロシージャ)  
 ストアド プロシージャを含むデータベースの名前を指定します。  
  
 *schema_name*(プロシージャ)  
 ストアド プロシージャを含むスキーマの名前を指定します。  
  
 *procedure_name*  
 ストアド プロシージャの名前を指定します。  
  
 MAX_QUEUE_READERS =*max_readers*  
 キューで同時に開始する、アクティブ化ストアド プロシージャの最大インスタンス数を指定します。 値*max_readers*間の数値でなければなりません**0**と**32767**です。  
  
 EXECUTE AS  
 アクティブ化ストアド プロシージャを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ユーザー アカウントを指定します [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キューがストアド プロシージャを開始時にこのユーザーのアクセス許可を確認できる必要があります。 ドメイン ユーザーの場合は、プロシージャが開始されるかアクティブ化が失敗したとき、サーバーがドメインに接続している必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーの場合は、サーバーで常に権限を確認できます。  
  
 SELF  
 現在のユーザーとしてストアド プロシージャを実行します。 (対象の CREATE QUEUE ステートメントを実行しているデータベース プリンシパル。)  
  
 '*user_name*'  
 ストアド プロシージャを実行するユーザーの名前を指定します。 *User_name*パラメーターを有効にする必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]として指定されたユーザー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子。 現在のユーザーの IMPERSONATE 権限が必要、 *user_name*指定します。  
  
 OWNER  
 キューの所有者としてストアド プロシージャを実行します。  
  
 POISON_MESSAGE_HANDLING  
 キューに対する有害なメッセージの処理が有効かどうかを指定します。 既定値は ON です。  
  
 有害なメッセージの処理が OFF に設定されているキューは、トランザクションのロールバックが連続して 5 回実行されても無効になりません。 これにより、カスタムの有害なメッセージの処理システムをアプリケーションで定義できます。  
  
 ON *filegroup |*[**既定**]  
 指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ファイル グループをこのキューを作成します。 使用することができます、 *filegroup*ファイル グループを識別または service broker データベースの既定のファイル グループを使用する既定の識別子を使用するパラメーターです。 この句のコンテキストでは、DEFAULT はキーワードとして扱われないため、識別子として区切り記号で区切る必要があります。 ファイル グループを指定しない場合、キューの作成ではデータベースの既定のファイル グループが使用されます。  
  
## <a name="remarks"></a>解説  
 キューは SELECT ステートメントの対象にすることができますが、 キューの内容を変更するには、SEND、RECEIVE、END CONVERSATION など、[!INCLUDE[ssSB](../../includes/sssb-md.md)] のメッセージ交換で動作するステートメントを使用する必要があります。 キューは、INSERT、UPDATE、DELETE、または TRUNCATE ステートメントの対象にすることはできません。  
  
 キューは一時オブジェクトとして指定できません。 したがって、キューの名前で始まる **#** が無効です。  
  
 キューを使用不可能な状態で作成した場合、サービス用のインフラストラクチャを配置してから、キューでメッセージを受信することができます。  
  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)]キューにメッセージがない場合にアクティブ化ストアド プロシージャは停止しません。 アクティブ化ストアド プロシージャは、しばらくの間キューに使用できるメッセージがないときには終了してください。  
  
 アクティブ化ストアド プロシージャの権限は、キューの作成時ではなく、[!INCLUDE[ssSB](../../includes/sssb-md.md)] によってストアド プロシージャが開始されるときに確認されます。 CREATE QUEUE ステートメントでは、EXECUTE AS 句で指定したユーザーに、PROCEDURE NAME 句で指定したストアド プロシージャの実行権限があるかどうかは確認されません。  
  
 キューが使用できないときに[!INCLUDE[ssSB](../../includes/sssb-md.md)]はデータベースの転送キューにキューを使用するサービスのメッセージを保持します。 カタログ ビュー sys.transmission_queue では、転送キューのビューが提供されます。  
  
 キューはスキーマが所有するオブジェクトです。 キューは、sys.objects カタログ ビューに表示されます。  
  
 次の表は、キューの列の一覧です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|ステータス|**tinyint**|メッセージの状態。 RECEIVE ステートメントの状態であるすべてのメッセージが返されます**1**です。 メッセージの保有が指定されている場合は、status が 0 に設定されます。 メッセージの保有が指定されていない場合は、メッセージがキューから削除されます。 キュー内のメッセージには、次の値のいずれかを含めることができます。<br /><br /> **0**保持されている受信メッセージを =<br /><br /> **1**= 受信準備完了<br /><br /> **2**= 未完了<br /><br /> **3**= 保持されているメッセージを送信|  
|priority|**tinyint**|このメッセージに割り当てられている優先度レベル。|  
|queuing_order|**bigint**|キュー内のメッセージの順序番号。|  
|conversation_group_id|**uniqueidentifier**|このメッセージが属するメッセージ交換グループの識別子。|  
|conversation_handle|**uniqueidentifier**|メッセージが属するメッセージ交換のハンドル。|  
|message_sequence_number|**bigint**|メッセージ交換内でのメッセージのシーケンス番号。|  
|service_name|**nvarchar(512)**|メッセージ交換の対象サービスの名前。|  
|service_id|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メッセージ交換のサービスのオブジェクト識別子です。|  
|service_contract_name|**nvarchar (256)**|メッセージ交換が従うコントラクトの名前。|  
|service_contract_id|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メッセージ交換が従うコントラクトのオブジェクト識別子です。|  
|message_type_name|**nvarchar (256)**|メッセージの種類を示すメッセージ型の名前。|  
|message_type_id|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]メッセージを記述するメッセージの種類のオブジェクト識別子です。|  
|validation|**nchar(2)**|メッセージに使用される検証。<br /><br /> E = 空<br /><br /> N = なし<br /><br /> X = XML|  
|message_body|**varbinary(max)**|メッセージの内容。|  
|message_id|**uniqueidentifier**|メッセージの一意識別子。|  
  
## <a name="permissions"></a>Permissions  
 キューを作成する権限では、db_ddladmin 固定データベース ロールまたは db_owner 固定データベース ロールのメンバー、および sysadmin 固定サーバー ロールのメンバーを使用します。  
  
 キューに対する REFERENCES 権限は、既定ではキューの所有者、db_ddladmin 固定データベース ロールまたは db_owner 固定データベース ロールのメンバー、および sysadmin 固定サーバー ロールのメンバーに与えられています。  
  
 キューに対する RECEIVE 権限は、既定ではキューの所有者、db_owner 固定データベース ロールのメンバー、および sysadmin 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-queue-with-no-parameters"></a>A. パラメーターなしでキューを作成する  
 次の例では、メッセージの受信に使用できるキューを作成します。 キューにアクティブ化ストアド プロシージャは指定しません。  
  
```  
CREATE QUEUE ExpenseQueue ;  
```  
  
### <a name="b-creating-an-unavailable-queue"></a>B. 使用できないキューを作成する  
 次の例では、メッセージの受信に使用できないキューを作成します。 キューにアクティブ化ストアド プロシージャは指定しません。  
  
```  
CREATE QUEUE ExpenseQueue WITH STATUS=OFF ;  
```  
  
### <a name="c-creating-a-queue-and-specify-internal-activation-information"></a>C. キューを作成し、内部アクティブ化情報を指定する  
 次の例では、メッセージの受信に使用できるキューを作成します。 キューがストアド プロシージャを開始`expense_procedure`メッセージがキューに入ったとき。 ストアド プロシージャ、ユーザーとして実行`ExpenseUser`です。 キューの最大の開始`5`ストアド プロシージャのインスタンス。  
  
```  
CREATE QUEUE ExpenseQueue  
    WITH STATUS=ON,  
    ACTIVATION (  
        PROCEDURE_NAME = expense_procedure,  
        MAX_QUEUE_READERS = 5,  
        EXECUTE AS 'ExpenseUser' ) ;  
```  
  
### <a name="d-creating-a-queue-on-a-specific-filegroup"></a>D. 特定のファイル グループにキューを作成する  
 次の例では、キューを作成したファイル グループに`ExpenseWorkFileGroup`です。  
  
```  
CREATE QUEUE ExpenseQueue  
    ON ExpenseWorkFileGroup ;  
```  
  
### <a name="e-creating-a-queue-with-multiple-parameters"></a>E. 複数のパラメーターでキューを作成する  
 次の例でキューを作成、`DEFAULT`ファイル グループ。 このキューは使用不可能な状態になります。 メッセージは、そのメッセージ交換が終わるまでキューに保持されます。 ALTER QUEUE を使用してキューを使用できるようにすると、キューによってストアド プロシージャ `2008R2.dbo.expense_procedure` が開始され、メッセージが処理されます。 ストアド プロシージャを実行したユーザーとして実行、`CREATE QUEUE`ステートメントです。 キューの最大の開始`10`ストアド プロシージャのインスタンス。  
  
```  
CREATE QUEUE ExpenseQueue  
    WITH STATUS = OFF,  
      RETENTION = ON,  
      ACTIVATION (  
          PROCEDURE_NAME = AdventureWorks2012.dbo.expense_procedure,  
          MAX_QUEUE_READERS = 10,  
          EXECUTE AS SELF )  
    ON [DEFAULT] ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER QUEUE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-queue-transact-sql.md)   
 [CREATE SERVICE &#40;Transact-SQL&#41;](../../t-sql/statements/create-service-transact-sql.md)   
 [DROP QUEUE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-queue-transact-sql.md)   
 [受信 (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/receive-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


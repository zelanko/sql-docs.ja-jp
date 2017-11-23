---
title: "イベント通知 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_EVENT_NOTIFICATION_TSQL
- NOTIFICATION_TSQL
- EVENT
- NOTIFICATION
- CREATE EVENT NOTIFICATION
- EVENT_TSQL
dev_langs: TSQL
helpviewer_keywords:
- CREATE EVENT NOTIFICATION statement
- events [SQL Server], notifications
- event notifications [SQL Server], creating
ms.assetid: dbbff0e8-9e25-4f12-a1ba-e12221d16ac2
caps.latest.revision: "64"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 48d7a50927d6fc3e193b54e85dd534aa859d13fa
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="create-event-notification-transact-sql"></a>CREATE EVENT NOTIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベース イベントやサーバー イベントに関する情報を Service Broker サービスに送信するオブジェクトを作成します。 イベント通知の作成のみを使用して[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE EVENT NOTIFICATION event_notification_name   
ON { SERVER | DATABASE | QUEUE queue_name }   
[ WITH FAN_IN ]  
FOR { event_type | event_group } [ ,...n ]  
TO SERVICE 'broker_service' , { 'broker_instance_specifier' | 'current database' }  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *event_notification_name*  
 イベント通知の名前を指定します。 イベント通知名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)が作成されたスコープ内で一意にする必要があります。 サーバー、データベース、または*object_name*です。  
  
 SERVER  
 イベント通知のスコープを現在の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに適用します。 インスタンスで任意の場所を FOR 句で指定したイベントが発生するたびに通知が行われた場合は、指定された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 DATABASE  
 イベント通知のスコープを現在のデータベースに適用します。 指定した場合、FOR 句で指定したイベントがデータベースで発生するたびに、通知が行われます。  
  
 QUEUE  
 通知のスコープを現在のデータベースの特定のキューに適用します。 QUEUE を指定できるのは、FOR QUEUE_ACTIVATION または FOR BROKER_QUEUE_DISABLED を指定した場合だけです。  
  
 *queue_name*  
 イベント通知を適用するキューの名前を指定します。 *queue_name*のみ指定できますキューが指定されているかどうか。  
  
 WITH FAN_IN   
 指示[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]イベントごとの 1 つだけのメッセージを送信するサービスすべてのイベント通知を指定します。  
  
-   同じイベントで作成されたイベント通知  
  
-   同じプリンシパルによって作成された (同じ SID で識別される) イベント通知  
  
-   同じサービスを指定し、 *broker_instance_specifier*です。  
  
-   WITH FAN_IN を指定するイベント通知  
  
 たとえば、3 つのイベント通知が作成されたとします。 すべてのイベント通知は同じ SID によって作成され、FOR ALTER_TABLE、WITH FAN_IN、および同じ TO SERVICE 句が指定されています。 この場合、ALTER TABLE ステートメントを実行すると、これら 3 つのイベント通知で作成されたメッセージは 1 つにマージされます。 したがって、対象サービスはイベント メッセージを 1 つだけ受信します。  
  
 *event_type*  
 イベント通知を実行するイベントの種類の名前を指定します。 *event_type*できます、 [!INCLUDE[tsql](../../includes/tsql-md.md)] DDL イベントの種類、SQL トレース イベントの種類または[!INCLUDE[ssSB](../../includes/sssb-md.md)]イベントの種類。 条件を満たすの一覧については[!INCLUDE[tsql](../../includes/tsql-md.md)]DDL イベントの種類を参照してください[DDL イベント](../../relational-databases/triggers/ddl-events.md)です。 [!INCLUDE[ssSB](../../includes/sssb-md.md)] イベントの種類は QUEUE_ACTIVATION と BROKER_QUEUE_DISABLED です。 詳しくは、「 [Event Notifications](../../relational-databases/service-broker/event-notifications.md)」をご覧ください。  
  
 *event_group*  
 定義済みグループの名前を指定[!INCLUDE[tsql](../../includes/tsql-md.md)]または SQL トレース イベントの種類。 イベント通知は、イベント グループに属するイベントが実行された後に実行されます。 DDL イベント グループの一覧については、[!INCLUDE[tsql](../../includes/tsql-md.md)]イベントの対象、およびスコープを定義できますを参照してください。 [DDL イベント グループ](../../relational-databases/triggers/ddl-event-groups.md)です。  
  
 *event_group*もはマクロとして機能し、CREATE EVENT NOTIFICATION ステートメントが完了したら、イベントの種類を追加することで説明を**sys.events**カタログ ビューです。  
  
 **'** *broker_service* **'**  
 イベント インスタンスのデータを受信する対象サービスを指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]イベント通知の対象サービスに 1 つまたは複数のメッセージ交換が開きます。 このサービスは、同じを受け付ける必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]イベントのメッセージ型とコントラクト、メッセージを送信するために使用します。  
  
 メッセージ交換は、イベント通知が削除されるまで開いたままになります。 特定のエラーが発生すると、メッセージ交換が予定よりも早く閉じる場合があります。 明示的にメッセージ交換の一部または全部を終了することで、対象サービスでそれ以上メッセージを受信しないようにできます。  
  
 { **'***broker_instance_specifier***'** | **'current database'** }  
 対象となる service broker インスタンスを指定*broker_service*は解決します。 クエリを実行して、特定のサービス ブローカーの値を取得することができます、 **service_broker_guid**の列、 **sys.databases**カタログ ビューです。 使用して**'current database'**を現在のデータベースで service broker インスタンスを指定します。 **'current database'**は大文字と小文字の文字列リテラルです。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージの種類およびイベント通知専用のコントラクトを含まれています。 そのため、Service Broker が発信側サービスが既に存在するため、作成するには、次のコントラクト名を指定します。`http://schemas.microsoft.com/SQL/Notifications/PostEventNotification`  
  
 イベント通知を受け取る対象サービスは、この既存のコントラクトに従う必要があります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSB](../../includes/sssb-md.md)] ダイアログ セキュリティを構成する必要があります。 ダイアログ セキュリティは完全なセキュリティ モデルに基づいて手動で構成する必要があります。 詳細については、次を参照してください。[イベント通知のダイアログ セキュリティを構成する](../../relational-databases/service-broker/configure-dialog-security-for-event-notifications.md)です。  
  
 通知を有効にしたイベント トランザクションがロールバックされた場合、イベント通知の送信もロールバックされます。 トランザクションがトリガー内でコミットまたはロールバックされた場合、トリガーで定義された操作によってイベント通知が行われることはありません。 トレース イベントはトランザクションでバインドされないため、トレース イベントに基づくイベント通知は、イベント通知を有効にするトランザクションがロールバックされたかどうかに関係なく送信されます。  
  
 イベント通知が行われた後で、サーバーと対象サービスの間のメッセージ交換が解除された場合は、エラーがレポートされ、イベント通知は削除されます。  
  
 通知を起動したイベント トランザクションが、イベント通知送信の成功または失敗によって影響を受けることはありません。  
  
 イベント通知の送信が失敗した場合はログに記録されます。  
  
## <a name="permissions"></a>Permissions  
 データベース スコープ (ON DATABASE) のイベント通知を作成するには、現在のデータベースの CREATE DATABASE DDL EVENT NOTIFICATION 権限が必要です。  
  
 サーバー スコープ (ON SERVER) の DDL ステートメントのイベント通知を作成するには、サーバーの CREATE DDL EVENT NOTIFICATION 権限が必要です。  
  
 トレース イベントのイベント通知を作成するには、サーバーの CREATE TRACE EVENT NOTIFICATION 権限が必要です。  
  
 キュー スコープのイベント通知を作成するには、キューの ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
> [!NOTE]  
>  以下に示す A と B の例では、`TO SERVICE 'NotifyService'` 句の GUID ('8140a771-3c4b-4479-8ac0-81008ab17984') は、例をセットアップしたコンピューターに固有の値です。 ここで示した例の場合は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースの GUID です。  
>   
>  をコピーし、これらの例を実行する必要があります、コンピューターからこの GUID に置き換えると[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンス。 上記の「引数」セクションで説明を取得できます、 **'***broker_instance_specifier***'** sys.databases の service_broker_guid 列にクエリを実行してカタログ ビューです。  
  
### <a name="a-creating-an-event-notification-that-is-server-scoped"></a>A. サーバー スコープのイベント通知を作成する  
 次の例は、サービスを使用してターゲットを設定する必要なオブジェクトを作成[!INCLUDE[ssSB](../../includes/sssb-md.md)]です。 対象サービスでは、イベント通知専用の開始サービスのメッセージ型とコントラクトが参照されます。 通知を送信する対象のサービスでイベント通知が作成されるたびに、`Object_Created`のインスタンスでトレース イベントが発生した[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
```tsql  
--Create a queue to receive messages.  
CREATE QUEUE NotifyQueue ;  
GO  
--Create a service on the queue that references  
--the event notifications contract.  
CREATE SERVICE NotifyService  
ON QUEUE NotifyQueue  
([http://schemas.microsoft.com/SQL/Notifications/PostEventNotification]);  
GO  
--Create a route on the service to define the address   
--to which Service Broker sends messages for the service.  
CREATE ROUTE NotifyRoute  
WITH SERVICE_NAME = 'NotifyService',  
ADDRESS = 'LOCAL';  
GO  
--Create the event notification.  
CREATE EVENT NOTIFICATION log_ddl1   
ON SERVER   
FOR Object_Created   
TO SERVICE 'NotifyService',  
    '8140a771-3c4b-4479-8ac0-81008ab17984' ;  
```  
  
### <a name="b-creating-an-event-notification-that-is-database-scoped"></a>B. データベース スコープのイベント通知を作成する  
 次の例では、前の例と同じ対象サービスに対してイベント通知を作成します。 イベント通知を起動した後、`ALTER_TABLE`イベントで発生する、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]サンプル データベース。  
  
```tsql  
CREATE EVENT NOTIFICATION Notify_ALTER_T1  
ON DATABASE  
FOR ALTER_TABLE  
TO SERVICE 'NotifyService',  
    '8140a771-3c4b-4479-8ac0-81008ab17984';  
```  
  
### <a name="c-getting-information-about-an-event-notification-that-is-server-scoped"></a>C. サーバー スコープのイベント通知に関する情報を取得する  
 次の例では、`sys.server_event_notifications` カタログ ビューをクエリして、サーバー スコープで作成されたイベント通知 `log_ddl1` に関するメタデータを取得します。  
  
```  
SELECT * FROM sys.server_event_notifications  
WHERE name = 'log_ddl1';  
```  
  
### <a name="d-getting-information-about-an-event-notification-that-is-database-scoped"></a>D. データベース スコープのイベント通知に関する情報を取得する  
 次の例のクエリ、`sys.event_notifications`カタログのイベント通知に関するメタデータのビュー`Notify_ALTER_T1`データベース スコープで作成されました。  
  
```tsql  
SELECT * FROM sys.event_notifications  
WHERE name = 'Notify_ALTER_T1';  
```  
  
## <a name="see-also"></a>参照  
 [イベント通知](../../relational-databases/service-broker/event-notifications.md)   
 [DROP EVENT NOTIFICATION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-event-notification-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.event_notifications &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)   
 [sys.server_event_notifications &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)   
 [sys.events &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-events-transact-sql.md)   
 [sys.server_events &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-server-events-transact-sql.md)  
  
  

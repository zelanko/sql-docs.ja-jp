---
title: sys.dm_qn_subscriptions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_qn_subscriptions
- dm_qn_subscriptions_TSQL
- sys.dm_qn_subscriptions
- sys.dm_qn_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_qn_subscriptions dynamic management view
ms.assetid: a3040ce6-f5af-48fc-8835-c418912f830c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2cbfdd765681f99e50b38efcdb5c7c61c8cbd08b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834710"
---
# <a name="query-notifications---sysdmqnsubscriptions"></a>クエリ通知 - sys.dm_qn_subscriptions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーのアクティブ クエリ通知サブスクリプションに関する情報を返します。 このビューは、サーバーまたは指定したデータベース内のアクティブなサブスクリプションを確認したり、指定したサーバー プリンシパルを確認する際に使用できます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|サブスクリプションの ID。|  
|**database_id**|**int**|通知クエリが実行されたデータベースの ID。 このデータベースには、サブスクリプションに関連する情報が格納されています。|  
|**sid**|**varbinary(85)**|このサブスクリプションを作成して所有しているサーバー プリンシパルのセキュリティ ID。|  
|**object_id**|**int**|サブスクリプションのパラメーターに関する情報を格納している内部テーブルの ID。|  
|**created**|**datetime**|サブスクリプションを作成した日時。|  
|**timeout**|**int**|サブスクリプションのタイムアウト値 (秒単位)。 この時間が経過した後、通知が行われます。<br /><br /> 注: 実際の実行時間は、指定されたタイムアウトを超えることがあります。指定したタイムアウト時刻が経過してからサブスクリプションが起動するまでの間に、サブスクリプションが無効になる変更が発生した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではこの変更時に必ず通知が行われます。|  
|**status**|**int**|サブスクリプションの状態を示します。 コードの一覧については、「解説」の表を参照してください。|  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|基準|型|  
|----------|--------|--------|----------|  
|**sys.dm_qn_subscriptions**|**sys.databases**|**database_id**|多対一|  
|**sys.dm_qn_subscriptions**|**sys.internal_tables**|**object_id**|多対一|  
  
## <a name="remarks"></a>コメント  
 状態コードが 0 の場合は、未定義の状態であることを示します。  
  
 次の状態コードは、変更によりサブスクリプションが起動したことを示します。  
  
|コード|マイナー状態|Info|  
|----------|------------------|----------|  
|65798|データが変更されたため、サブスクリプションが起動しました|挿入によってサブスクリプションがトリガーされました|  
|65799|データが変更されたため、サブスクリプションが起動しました|DELETE|  
|65800|データが変更されたため、サブスクリプションが起動しました|Update|  
|65801|データが変更されたため、サブスクリプションが起動しました|Merge|  
|65802|データが変更されたため、サブスクリプションが起動しました|テーブルを切り捨てる|  
|66048|タイムアウトが発生したため、サブスクリプションが起動しました|未定義の info モード|  
|66315|オブジェクトが変更されたため、サブスクリプションが起動しました|オブジェクトまたはユーザーが削除されました|  
|66316|オブジェクトが変更されたため、サブスクリプションが起動しました|オブジェクトが変更されました|  
|66565|データベースがデタッチまたは削除されたため、サブスクリプションが起動しました|サーバーまたはデータベースが再起動されました|  
|66571|データベースがデタッチまたは削除されたため、サブスクリプションが起動しました|オブジェクトまたはユーザーが削除されました|  
|66572|データベースがデタッチまたは削除されたため、サブスクリプションが起動しました|オブジェクトが変更されました|  
|67341|サーバーのリソースが不足しているため、サブスクリプションがトリガーされました|サーバーのリソースが不足しているため、サブスクリプションがトリガーされました|  
  
 次の状態コードは、サブスクリプションを作成できなかったことを示します。  
  
|コード|マイナー状態|Info|  
|----------|------------------|----------|  
|132609|ステートメントがサポートされていないため、サブスクリプションを作成できませんでした|クエリが複雑すぎます|  
|132610|ステートメントがサポートされていないため、サブスクリプションを作成できませんでした|サブスクリプションのステートメントが無効です|  
|132611|ステートメントがサポートされていないため、サブスクリプションを作成できませんでした|サブスクリプションの設定オプションが無効です|  
|132612|ステートメントがサポートされていないため、サブスクリプションを作成できませんでした|分離レベルが無効です|  
|132622|ステートメントがサポートされていないため、サブスクリプションを作成できませんでした|内部使用|  
|132623|ステートメントがサポートされていないため、サブスクリプションを作成できませんでした|テーブルごとのテンプレートの上限を超えました|  
  
 次の状態コードは内部で使用され、check kill モードおよび init モードとして分類されます。  
  
|コード|マイナー状態|Info|  
|----------|------------------|----------|  
|198656|内部使用: check kill モードおよび init モード|未定義の info モード|  
|198928|サブスクリプションが破棄されました|データベースがアタッチされたため、サブスクリプションが起動しました|  
|198929|サブスクリプションが破棄されました|ユーザーが削除されたため、サブスクリプションが起動しました|  
|198930|サブスクリプションが破棄されました|再サブスクリプションのため、サブスクリプションが削除されました|  
|198931|サブスクリプションが破棄されました|サブスクリプションが強制終了されました|  
|199168|サブスクリプションがアクティブです|未定義の info モード|  
|199424|サブスクリプションが初期化されていますが、まだアクティブではありません|未定義の info モード|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
> [!NOTE]  
>  ユーザーに VIEW SERVER STATE 権限がない場合、このビューでは現在のユーザーが所有するサブスクリプションに関する情報が返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-return-active-query-notification-subscriptions-for-the-current-user"></a>A. 現在のユーザーのアクティブなクエリ通知サブスクリプションを返す  
 次の例では、現在のユーザーのアクティブなクエリ通知サブスクリプションを返します。 ユーザーが VIEW SERVER STATE 権限を所有している場合は、サーバー内のアクティブなサブスクリプションがすべて返されます。  
  
```  
SELECT id, database_id, sid, object_id, created, timeout, status  
FROM sys.dm_qn_subscriptions;  
GO  
```  
  
### <a name="b-returning-active-query-notification-subscriptions-for-a-specified-user"></a>B. 指定したユーザーのアクティブなクエリ通知サブスクリプションを返す  
 次の例では、ログイン `Ruth0` によってサブスクライブされたアクティブなクエリ通知サブスクリプションを返します。  
  
```  
SELECT id, database_id, sid, object_id, created, timeout, status  
FROM sys.dm_qn_subscriptions  
WHERE sid = SUSER_SID('Ruth0');  
GO  
```  
  
### <a name="c-returning-internal-table-metadata-for-query-notification-subscriptions"></a>C. クエリ通知サブスクリプションに関する内部テーブルのメタデータを返す  
 次の例では、クエリ通知サブスクリプションに関する内部テーブルのメタデータを返します。  
  
```  
SELECT qn.id AS query_subscription_id  
    ,it.name AS internal_table_name  
    ,it.object_id AS internal_table_id  
FROM sys.internal_tables AS it  
JOIN sys.dm_qn_subscriptions AS qn ON it.object_id = qn.object_id  
WHERE it.internal_type_desc = 'QUERY_NOTIFICATION';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [通知関連の動的管理ビューに対してクエリを&#40;TRANSACT-SQL&#41;](http://msdn.microsoft.com/library/92eb22d8-33f3-4c17-b32e-e23acdfbd8f4)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION &#40;TRANSACT-SQL&#41;](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)  
  
  

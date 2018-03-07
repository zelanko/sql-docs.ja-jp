---
title: "ALTER キュー (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/01/2016
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
- ALTER_QUEUE_TSQL
- ALTER QUEUE
dev_langs:
- TSQL
helpviewer_keywords:
- number of queue readers
- modifying queues
- ALTER QUEUE statement
- queue readers [SQL Server]
- queues [Service Broker], modifying
- unavailable queues [SQL Server]
- activation stored procedures [Service Broker]
ms.assetid: d54aa325-8761-4cd4-8da7-acf33df12296
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f97bd0a341ecc5e960c94c4c8bdabe30b572fd9
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="alter-queue-transact-sql"></a>ALTER QUEUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  キューのプロパティを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ALTER QUEUE <object>   
   queue_settings  
   | queue_action  
[ ; ]  
  
<object> : :=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]  
        queue_name  
}   
  
<queue_settings> : :=  
WITH  
   [ STATUS = { ON | OFF } [ , ] ]  
   [ RETENTION = { ON | OFF } [ , ] ]  
   [ ACTIVATION (  
       { [ STATUS = { ON | OFF } [ , ] ]   
         [ PROCEDURE_NAME = <procedure> [ , ] ]  
         [ MAX_QUEUE_READERS = max_readers [ , ] ]  
         [ EXECUTE AS { SELF | 'user_name'  | OWNER } ]  
       |  DROP }  
          ) [ , ]]  
         [ POISON_MESSAGE_HANDLING (  
          STATUS = { ON | OFF } )  
         ]   
  
<queue_action> : :=  
   REBUILD [ WITH <query_rebuild_options> ]  
   | REORGANIZE [ WITH (LOB_COMPACTION = { ON | OFF } ) ]  
   | MOVE TO { file_group | "default" }  
  
<procedure> : :=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]  
        stored_procedure_name  
}  
  
<queue_rebuild_options> : :=  
{  
   ( MAXDOP = max_degree_of_parallelism )  
}  
  
```  
  
## <a name="arguments"></a>引数  
 *database_name* (object)  
 変更するキューを含むデータベースの名前を指定します。 ない場合*database_name*は提供された場合、既定値は、現在のデータベースです。  
  
 *schema_name* (object)  
 新しいキューが所属するスキーマの名前を指定します。 ない場合*schema_name*は提供された場合、既定値は、現在のユーザーの既定のスキーマです。  
  
 *queue_name*  
 変更するキューの名前を指定します。  
  
 STATUS (Queue)   
 キューが使用可能 (ON) か、使用不可能 (OFF) かを指定します。 キューが使用不可能な場合、キューにメッセージを追加したり、キューからメッセージを削除することはできません。  
  
 RETENTION   
 キューのメッセージ保有期間の設定を指定します。 RETENTION = ON の場合、このキューを使用するメッセージ交換で送信または受信されるすべてのメッセージは、メッセージ交換が終了するまでキュー内に保有されます。 これにより、監査目的でメッセージを保有したり、エラーが発生した場合に補正するトランザクションを実行することができます。  
  
> [!NOTE]  
>  RETENTION = ON に設定すると、パフォーマンスが低下する場合があります。 この設定は、アプリケーションのサービス レベル契約を満たす必要がある場合にのみ使用してください。  
  
 ACTIVATION  
 このキューに到着するメッセージを処理するため、アクティブになっているストアド プロシージャについての情報を指定します。  
  
 STATUS (Activation)   
 キューがストアド プロシージャをアクティブにするかどうかを指定します。 STATUS = ON の場合は、現在実行中のプロシージャの数が MAX_QUEUE_READERS より少なく、ストアド プロシージャによるメッセージの受信よりも早くメッセージがキューに到着する場合に、PROCEDURE_NAME で指定されるストアド プロシージャがキューによって開始されます。 STATUS = OFF の場合は、キューによってストアド プロシージャはアクティブになりません。  
  
 REBUILD [ WITH \<queue_rebuild_options> ]  
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 キューの内部テーブルのすべてのインデックスを再構築します。 負荷が高いため、断片化の問題が発生した場合は、この機能を使用します。 MAXDOP は、唯一サポートされているキューの rebuild オプションです。 再構築は、常にオフライン操作です。  
  
 REORGANIZE [ WITH ( LOB_COMPACTION = { ON | OFF } ) ]  
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 キューの内部テーブルのすべてのインデックスを再編成します。   
ユーザー テーブルに再編成とは異なり、キューに再編成は常に実行オフライン操作としてページ レベルのロックがキューで明示的に無効になっています。  
  
> [!TIP]  
>  インデックスの断片化に関する一般的なガイダンス断片化が 5% ~ 30% には、インデックスが再編成します。 断片化が 30% を超える場合、インデックスを再構築します。 ただし、これらの番号、専用環境の開始点として一般的なガイダンスです。 インデックスの断片化の量を調べるには使用[sys.dm_db_index_physical_stats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md) -例については、該当するアーティクル内の例 G を参照してください。  
  
 MOVE TO { *file_group* | "default" }  
 **適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 (インデックス) のキューの内部テーブルをユーザー指定のファイル グループに移動します。  読み取り専用のファイル グループにはできません。  
  
 PROCEDURE_NAME = \<procedure>  
 処理するメッセージがキューに含まれているときにアクティブにするストアド プロシージャの名前を指定します。 この値である必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子。  
  
 *database_name* (プロシージャ)  
 ストアド プロシージャを含むデータベースの名前を指定します。  
  
 *schema_name* (プロシージャ)  
 ストアド プロシージャを所有するスキーマの名前を指定します。  
  
 *stored_procedure_name*  
 ストアド プロシージャの名前を指定します。  
  
 MAX_QUEUE_READERS =*max_reader*  
 キューで同時に開始するアクティブ化ストアド プロシージャのインスタンスの最大数を指定します。 値*max_readers* 0 から 32767 までの数値でなければなりません。  
  
 EXECUTE AS  
 アクティブ化ストアド プロシージャを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース ユーザー アカウントを指定します [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]キューがストアド プロシージャをアクティブ化時にこのユーザーのアクセス許可を確認できる必要があります。 Microsoft Windows ドメイン ユーザーの場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がドメインに接続している必要があり、プロシージャがアクティブ化されたとき、またはアクティブ化が失敗したときに、指定したユーザーの権限を検証できる必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーの場合は、サーバーで常に権限を確認できます。  
  
 SELF  
 現在のユーザーとしてストアド プロシージャを実行します。 (対象の ALTER QUEUE ステートメントを実行しているデータベース プリンシパル)。  
  
 '*user_name*'  
 ストアド プロシージャを実行するユーザーの名前です。 *user_name*は有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]として指定されたユーザー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子。 現在のユーザーの IMPERSONATE 権限が必要、 *user_name*指定します。  
  
 OWNER  
 キューの所有者としてストアド プロシージャを実行します。  
  
 DROP  
 キューに関連付けられているすべてのアクティブ化情報を削除します。  
  
 POISON_MESSAGE_HANDLING  
 有害なメッセージの処理が有効かどうかを指定します。 既定値は ON です。  
  
 有害なメッセージの処理が OFF に設定されているキューは、トランザクションのロールバックが連続して 5 回実行されても無効になりません。 これにより、カスタムの有害なメッセージの処理システムをアプリケーションで定義できます。  
  
## <a name="remarks"></a>解説  
 指定されたアクティブ化ストアド プロシージャが存在するキューにメッセージが含まれている場合は、アクティブ化状態を OFF から ON に変更すると、すぐにアクティブ化ストアド プロシージャがアクティブになります。 アクティブ化状態を ON から OFF に変更すると、ストアド プロシージャのインスタンスのアクティブ化処理は停止しますが、現在実行中のストアド プロシージャのインスタンスは停止しません。  
  
 キューにアクティブ化ストアド プロシージャを追加しても、キューのアクティブ化の状態は変わりません。 キューのアクティブ化ストアド プロシージャを変更しても、現在実行中のアクティブ化ストアド プロシージャのインスタンスには影響しません。  
  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] では、アクティブ化処理の一部として、キューに設定されているキュー リーダーの最大数が確認されます。 したがって、キューに対してキュー リーダーの最大数を増やすと、[!INCLUDE[ssSB](../../includes/sssb-md.md)] ではすぐにアクティブ化ストアド プロシージャのインスタンスを追加起動できるようになります。 キューに対してキュー リーダーの最大数を減らしても、現在実行中のアクティブ化ストアド プロシージャのインスタンスには影響しませんが、 ただし、[!INCLUDE[ssSB](../../includes/sssb-md.md)]はストアド プロシージャをアクティブ化のインスタンス数まで、ストアド プロシージャの新しいインスタンスが構成されている最大数を下回る開始されません。  
  
 キューが使用できないときに[!INCLUDE[ssSB](../../includes/sssb-md.md)]はデータベースの転送キューにキューを使用するサービスのメッセージを保持します。 [Sys.transmission_queue](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)カタログ ビューは、転送キューのビューを提供します。  
  
 RECEIVE ステートメントまたは GET CONVERSATION GROUP ステートメントが使用できないキューを指定する場合、ステートメントは失敗し、[!INCLUDE[tsql](../../includes/tsql-md.md)]エラーです。  
  
## <a name="permissions"></a>権限  
 既定では、キューを変更する権限は、キューの所有者、db_ddladmin 固定データベース ロールまたは db_owner 固定データベース ロールのメンバー、および sysadmin 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-making-a-queue-unavailable"></a>A. キューを利用できないようにする  
 次の例では、`ExpenseQueue` キューをメッセージの受信に利用できないようにします。  
  
```  
ALTER QUEUE ExpenseQueue WITH STATUS = OFF ;  
```  
  
### <a name="b-changing-the-activation-stored-procedure"></a>B. アクティブ化ストアド プロシージャを変更する  
 次の例では、キューによって開始されるストアド プロシージャを変更します。 ストアド プロシージャを実行したユーザーとして実行、`ALTER QUEUE`ステートメントです。  
  
```  
ALTER QUEUE ExpenseQueue  
    WITH ACTIVATION (  
        PROCEDURE_NAME = new_stored_proc,  
        EXECUTE AS SELF) ;  
```  
  
### <a name="c-changing-the-number-of-queue-readers"></a>C. キュー リーダーの数を変更する  
 次の例では、このキュー用に [!INCLUDE[ssSB](../../includes/sssb-md.md)] で起動されるストアド プロシージャ インスタンスの最大数を `7` に設定します。  
  
```  
ALTER QUEUE ExpenseQueue WITH ACTIVATION (MAX_QUEUE_READERS = 7) ;  
```  
  
### <a name="d-changing-the-activation-stored-procedure-and-the-execute-as-account"></a>D. アクティブ化ストアド プロシージャと EXECUTE AS アカウントを変更する  
 次の例は、ストアド プロシージャを変更する[!INCLUDE[ssSB](../../includes/sssb-md.md)]を開始します。 ストアド プロシージャ、ユーザーとして実行`SecurityAccount`です。  
  
```  
ALTER QUEUE ExpenseQueue  
    WITH ACTIVATION (  
        PROCEDURE_NAME = AdventureWorks2012.dbo.new_stored_proc ,  
        EXECUTE AS 'SecurityAccount') ;  
```  
  
### <a name="e-setting-the-queue-to-retain-messages"></a>E. メッセージを保持するようキューを設定する  
 次の例では、メッセージを保持するようキューを設定します。 このキューでは、キューを使用するサービス間で送信または受信されるすべてのメッセージが、そのメッセージ交換が終わるまで保持されます。  
  
```  
ALTER QUEUE ExpenseQueue WITH RETENTION = ON ;  
```  
  
### <a name="f-removing-activation-from-a-queue"></a>F. キューからアクティブ化情報を削除する  
 次の例では、キューからすべてのアクティブ化情報を削除します。  
  
```  
ALTER QUEUE ExpenseQueue WITH ACTIVATION (DROP) ;  
```  
  
### <a name="g-rebuilding-queue-indexes"></a>G. キューのインデックスの再構築  
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 次の例は、キューのインデックスを再構築します。  
  
```  
ALTER QUEUE ExpenseQueue REBUILD WITH (MAXDOP = 2)   
```  
  
### <a name="h-reorganizing-queue-indexes"></a>H. キューのインデックスを再構成します。  
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 次の例は、キューのインデックスを再編成します。  
  
```  
ALTER QUEUE ExpenseQueue REORGANIZE   
```  
  
### <a name="i-moving-queue-internal-table-to-another-filegroup"></a>I: キューの内部テーブルを別のファイル グループに移動します。  
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
ALTER QUEUE ExpenseQueue MOVE TO [NewFilegroup]   
```  
  
## <a name="see-also"></a>参照  
 [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md)   
 [DROP QUEUE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-queue-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
  
  

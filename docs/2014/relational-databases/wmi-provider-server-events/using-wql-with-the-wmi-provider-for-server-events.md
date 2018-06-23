---
title: WMI provider for Server Events の WQL の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Server Events, WQL
ms.assetid: 58b67426-1e66-4445-8e2c-03182e94c4be
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ddf3b6610fc9abc4e9103536363620a927477e67
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177942"
---
# <a name="using-wql-with-the-wmi-provider-for-server-events"></a>WMI Provider for Server Events と WQL の使用
  管理アプリケーションは WQL (WMI Query Language) ステートメントを実行することにより、WMI Provider for Server Events を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントにアクセスすることができます。 WQL は、WMI 特有の拡張機能を複数持つ、構造化照会言語 (SQL) の単純化されたサブセットです。 WQL を使用した場合、アプリケーションは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンス、データベース、またはデータベース オブジェクト (現在サポートされているオブジェクトはキューのみ) に対してイベントの種類を取得します。 WMI Provider for Server Events は、クエリをターゲット データベースまたはデータベース スコープまたはオブジェクト スコープのイベント通知用に作成されるイベント通知に変換、**マスター**サーバー スコープのイベント用のデータベース通知です。  
  
 たとえば、次の WQL クエリがあるとします。  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS WHERE DatabaseName = 'AdventureWorks'  
```  
  
 このクエリから、WMI プロバイダーは、このイベント通知と同等のものを対象サーバー上に生成しようとします。  
  
```  
USE AdventureWorks ;  
GO  
  
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9  
    ON DATABASE  
    WITH FAN_IN  
    FOR DDL_DATABASE_LEVEL_EVENTS  
    TO SERVICE   
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0',  
        'A7E5521A-1CA6-4741-865D-826F804E5135';  
GO  
```  
  
 WQL クエリ (`FROM`) の `DDL_DATABASE_LEVEL_EVENTS` 句の引数には、イベント通知を作成できる有効なイベントを指定することができます。 `SELECT` 句および `WHERE` 句の引数は、イベントまたはその親イベントに関連付けられたイベント プロパティを指定することができます。 有効なイベントとイベントのプロパティの一覧は、次を参照してください。[イベント通知 (データベース エンジン)](http://technet.microsoft.com/library/ms182602.aspx)です。  
  
 次の WQL 構文は、WMI Provider for Server Events によって明示的にサポートされます。 追加の WQL 構文を指定することもできますが、このプロバイダーに特有ではないため、代わりに WMI ホスト サービスによって解析されます。 WMI Query Language の詳細については、Microsoft Developer Network (MSDN) の WQL のドキュメントを参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
SELECT { event_property [ ,...n ] | * }  
FROM event_type   
WHERE where_condition  
```  
  
## <a name="arguments"></a>引数  
 *event_property*  
 イベントのプロパティ。 例には、`PostTime`、`SPID`、および `LoginName` が含まれています。 表示されている各イベントを検索[WMI Provider for Server Events のクラスとプロパティ](wmi-provider-for-server-events-classes-and-properties.md)を保持しているプロパティを特定します。 たとえば、DDL_DATABASE_LEVEL_EVENTS イベントには、`DatabaseName` プロパティおよび `UserName` プロパティがあります。 また、親イベントから `SQLInstance` プロパティ、`LoginName` プロパティ、`PostTime` プロパティ、`SPID` プロパティ、および `ComputerName` プロパティを継承しています。  
  
 **、** *.. .n*  
 示します*event_property*照会できる、複数回コンマで区切っています。  
  
 \*  
 イベントに関連付けられたすべてのプロパティを照会することを指定します。  
  
 *event_type*  
 イベント通知を作成できるイベント。 使用可能なイベントの一覧は、次を参照してください。 [WMI Provider for Server Events のクラスとプロパティ](http://technet.microsoft.com/library/ms186449.aspx)です。 なお*イベントの種類*に同じ名前が対応して*event_type* | *event_group*イベント通知を手動で作成するときに指定できます。CREATE EVENT NOTIFICATION を使用します。 例として*イベントの種類*CREATE_TABLE、LOCK_DEADLOCK、DDL_USER_EVENTS、TRC_DATABASE が含まれます。  
  
> [!NOTE]  
>  DDL に似た操作を実行する一部のシステム ストアド プロシージャもイベント通知を起動することができます。 イベント通知はテストして、実行されているシステム ストアド プロシージャに応答するかどうか、確認してください。 たとえば、CREATE TYPE ステートメントと**sp_addtype**ストアド プロシージャはどちらも起動 CREATE_TYPE イベントで作成されるイベント通知を取得します。 ただし、 **sp_rename**ストアド プロシージャでは、イベント通知は発生しません。 詳細については、次を参照してください。[DDL イベント](../triggers/ddl-events.md)です。  
  
 *where_condition*  
 WHERE 句クエリ述語での構成は、 *event_property*名と論理演算子と比較演算子です。 *Where_condition*対応するイベント通知がターゲット データベースに登録されているスコープを決定します。 特定のスキーマまたはクエリを元のオブジェクトを対象フィルターとしても機能できます*event_type です。* 詳細については、このトピックの後半の「解説」セクションを参照してください。  
  
 `DatabaseName`、`SchemaName`、および `ObjectName` と共に使用できるのは、`=` オペランドのみです。 その他の式は、これらのイベント プロパティと共に使用することはできません。  
  
## <a name="remarks"></a>コメント  
 *Where_condition* WMI Provider for Server Events の構文は、次を決定します。  
  
-   プロバイダーが、指定した取得を試みますスコープ*event_type*: サーバー レベル、データベース レベル、またはオブジェクト レベル (現在サポートされている唯一のオブジェクトはキュー)。 最終的に、このスコープは対象データベースで作成されたイベント通知の種類を決定します。 このプロセスは、イベント通知登録と呼ばれます。  
  
-   データベース、スキーマ、オブジェクトのうちの適切な登録場所。  
  
 WMI Provider for Server Events は、bottom-up および first-fit アルゴリズムを使用して、基になる EVENT NOTIFICATION に対してできるだけ小さなスコープを生成します。 アルゴリズムにより、サーバーの内部的な利用状況、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスと WMI ホスト プロセス間のネットワーク トラフィックが最小になるように試行されます。 プロバイダーを調べ、 *event_type* FROM 句と WHERE 句の条件で指定し、できるだけ狭いスコープで、基になるイベント通知を登録しようとしています。 プロバイダーが最も狭いスコープで登録できない場合は、登録が正常に終了するまで、順次より高いスコープでの登録が試行されます。 最も高いスコープ (サーバーレベル) に到達して失敗した場合、エラーがコンシューマーに返されます。  
  
 たとえば場合、DatabaseName =**'** AdventureWorks **'** でイベント通知を登録すると、プロバイダー、WHERE 句で指定されて、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベース。 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースが存在し、呼び出し側クライアントが、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] のイベント通知を作成するために必要な権限を持っている場合、登録は正常に完了します。 それ以外の場合は、イベント通知をサーバー レベルで登録しようとします。 WMI クライアントが必要な権限を持っている場合、登録は正常に終了します。 ただし、このシナリオでは、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースが作成されるまで、イベントはクライアントに返されません。  
  
 *Where_condition*さらに、クエリを特定のデータベース、スキーマ、またはオブジェクトを制限するフィルターとしても機能できます。 たとえば、次の WQL クエリがあるとします。  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
 登録プロセスの結果によっては、この WQL クエリは、データベース レベルまたはサーバー レベルのどちらかに登録されます。 ただし、サーバー レベルに登録された場合でも、プロバイダーは、`ALTER_TABLE` テーブルには適用されない `AdventureWorks.Sales.SalesOrderDetail` イベントを最終的にフィルターします。 つまり、プロバイダーは、この特定のテーブル上で発生した `ALTER_TABLE` イベントのプロパティのみを返します。  
  
 `DatabaseName='AW1'` OR `DatabaseName='AW2'` などの複合式が指定された場合、2 つの異なるイベント通知ではなく、サーバー スコープで 1 つのイベント通知の登録が試行されます。 呼び出し側クライアントが権限を持っている場合、登録は正常に終了します。  
  
 場合`SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'`がすべてで指定された、`WHERE`句、しようとしましたが、直接オブジェクトに関するイベント通知を登録`Z`スキーマ`X`です。 クライアントが権限を持っている場合、登録は正常に終了します。 現時点では、オブジェクト レベルのイベントは、サポートされてキューにのみ、のみ、QUEUE_ACTIVATION *event_type*です。  
  
 ある特定のスコープでは、すべてのイベントを照会できるわけではないことに注意してください。 たとえば、Lock_Deadlock など、トレース イベント上の WQL クエリ、または TRC_LOCKS などのトレース イベント グループは、サーバー レベルでのみ登録できます。 同様に、CREATE_ENDPOINT イベントおよび DDL_ENDPOINT_EVENTS イベント グループも、サーバー レベルでのみ登録できます。 イベントを登録するための適切なスコープの詳細については、次を参照してください。[イベント通知のデザイン](http://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx)です。 WQL を登録しようとすると、クエリの*event_type*しか登録できないサーバーでレベルが常に、サーバー レベルで作成します。 WMI クライアントが権限を持っている場合、登録は正常に終了します。 それ以外の場合は、クライアントにエラーが返されます。 ただし、WHERE 句は、イベントに対応するプロパティに基づいたサーバー レベル イベントに対するフィルターとして使用できる場合もあります。 たとえば、多くのトレース イベントに含まれている `DatabaseName` プロパティは、WHERE 句でフィルターとして使用できます。  
  
 サーバー スコープのイベント通知で作成された、**マスター**データベースし、を使用して、メタデータを照会することができます、 [sys.server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)カタログ ビューです。  
  
 データベース スコープまたはオブジェクト スコープのイベント通知は、指定されたデータベースに作成されを使用して、メタデータを照会することができます、 [sys.event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)カタログ ビューです。 (カタログ ビューのプレフィックスには、対応するデータベース名を使用する必要があります)。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-querying-for-events-at-the-server-scope"></a>A. サーバー スコープのイベントを照会する  
 次の WQL クエリは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス上で発生する `SERVER_MEMORY_CHANGE` トレース イベントのイベント プロパティをすべて取得します。  
  
```  
SELECT * FROM SERVER_MEMORY_CHANGE  
```  
  
### <a name="b-querying-for-events-at-the-database-scope"></a>B. データベース スコープのイベントを照会する  
 次の WQL クエリは、`AdventureWorks` データベース内で発生し、`DDL_DATABASE_LEVEL_EVENTS` イベント グループに存在するイベントの特定のイベント プロパティを取得します。  
  
```  
SELECT SPID, SQLInstance, DatabaseName FROM DDL_DATABASE_LEVEL_EVENTS   
WHERE DatabaseName = 'AdventureWorks'   
```  
  
### <a name="c-querying-for-events-at-the-database-scope-filtering-by-schema-and-object"></a>C. データベース スコープのイベントを照会し、スキーマおよびオブジェクトでフィルター処理を行う  
 次のクエリは、テーブル `ALTER_TABLE` 上で発生する `AdventureWorks.Sales.SalesOrderDetail` イベントのイベント プロパティを取得します。  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
## <a name="see-also"></a>参照  
 [WMI Provider for Server Events の概念](http://technet.microsoft.com/library/ms180560.aspx)   
 [イベント通知 (データベース エンジン)](http://technet.microsoft.com/library/ms182602.aspx)  
  
  

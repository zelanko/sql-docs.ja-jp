---
title: "ユーザー セッション (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0425cef2-de4d-4f42-91c5-cb1cd4bb1265
caps.latest.revision: "15"
ms.openlocfilehash: 11c9325b6a16f92ca4d39438fef2a829af3c14b3
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="user-sessions"></a>ユーザー セッション
適切な権限を持つログインは、これらのアクションの実行を含む、SQL Server PDW アプライアンス上のすべてのログインのセッションを管理できます。  
  
-   作業中とアイドル状態の両方のセッションを含め、アプライアンス上の現在のセッションを表示します。  
  
-   セッションのアクティブおよび最近使用したクエリを表示します。  
  
-   アクティブなセッションを終了します。  
  
いずれかを使用してこれらの操作を実行することができます、[アプライアンスを管理コンソールを使用して監視](monitor-the-appliance-by-using-the-admin-console.md)または[システム ビュー](tsql-system-views.md) SQL コマンドを次のように使用します。  
  
いずれかの方法を使用してセッションを管理するために必要なアクセス許可が同じに記載されて[ログインの管理、ユーザー、およびデータベース ロールにアクセス許可を付与](grant-permissions.md#grant-permissions-to-manage-logins-users-and-database-roles)です。  
  
## <a name="manage-sessions-by-using-the-admin-console"></a>管理者コンソールを使用してセッションを管理します。  
  
### <a name="to-view-current-sessions-by-using-the-admin-console"></a>管理コンソールを使用して現在のセッションを表示するには  
  
1.  上部のメニューをクリックして**セッション**です。  
  
2.  結果のリストには、最近のすべてのセッションが表示されます。 'Active' または 'アイドル' セッションのみを表示する をクリックして、**ステータス**状態で並べ替えると結果に列ヘッダー。  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-the-admin-console"></a>管理者コンソールを使用して、セッションのアクティブおよび最新のクエリを表示するには  
  
1.  上部のメニューをクリックして**セッション**です。  
  
2.  結果の一覧で、目的のセッションのセッション ID をクリックします。  
  
3.  クエリの結果の一覧は、セッションの最新のクエリを示します。 クエリの詳細を表示する方法については、次を参照してください。[アクティブなクエリの監視](monitoring-active-queries.md)です。  
  
### <a name="to-end-sessions-by-using-the-admin-console"></a>管理者コンソールを使用してセッションを終了するには  
  
1.  上部のメニューをクリックして**セッション**です。  
  
2.  キャンセルするセッションのセッションの ID を検索します。  
  
3.  赤いをクリックして**X**セッションを終了するセッション ID の左側にします。 'Active' または 'アイドル' の状態とのセッションで、赤はのみ**X**; のみこれらのセッションを終了することができます。  
  
## <a name="manage-sessions-by-using-system-views-and-sql-commands"></a>システム ビューと SQL コマンドを使用してセッションを管理します。  
  
### <a name="to-view-current-sessions-by-using-system-views"></a>システム ビューを使用して現在のセッションを表示するには  
使用して[sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)現在のセッションの一覧を生成します。  
  
この例では、すべてのセッション状態の 'Active' または 'アイドル' session_id、login_name、および状態を返します。  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions WHERE status='Active' OR status='Idle';  
```  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-system-views"></a>システム ビューを使用して、セッションのアクティブおよび最新のクエリを表示するには  
使用するセッションに関連付けられているアクティブおよび最近完了したクエリを表示する、 [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)と[sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)ビュー。 このクエリは、すべてのアクティブまたはアイドル状態のセッションと各セッション ID に関連付けられているすべてのアクティブまたは最近使用したクエリの一覧を返します。  
  
```sql  
SELECT es.session_id, es.login_name, es.status AS sessionStatus,   
er.request_id, er.status AS requestStatus, er.command   
FROM sys.dm_pdw_exec_sessions es   
LEFT OUTER JOIN sys.dm_pdw_exec_requests er   
ON (es.session_id=er.session_id)   
WHERE (es.status='Active' OR es.status='Idle') AND   
(er.status!= 'Completed' AND er.status!= 'Failed' AND er.status!= 'Cancelled');  
```  
  
### <a name="to-end-sessions-by-using-sql-commands"></a>SQL コマンドを使用してセッションを終了するには  
使用して、 [KILL](../t-sql/language-elements/kill-transact-sql.md)を現在のセッションを終了するコマンド。 使用して取得できますが、終了するプロセスのセッション ID が必要、 [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)ビュー。  
  
この例では login_name、session_id、ログイン名に基づいてセッションを検索する状態の値を選択します。  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions;  
```  
  
KILL コマンドを使用して、'Active' または 'アイドル' 状態でセッションを終了できます。  
  
```sql  
KILL 'SID137';  
```  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  

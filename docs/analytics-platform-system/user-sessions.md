---
title: Analytics Platform System でのユーザー セッション |Microsoft Docs"
description: Analytics Platform System の Parallel Data Warehouse でのユーザー セッション。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 49c8ea2479c0114364958b18ac299794511154d5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959798"
---
# <a name="user-sessions-in-analytics-platform-system"></a>Analytics Platform System でのユーザー セッション
適切な権限を持つログインは、これらのアクションの実行を含む、SQL Server PDW アプライアンス上のすべてのログインのセッションを管理できます。  
  
-   アクティブなとアイドル状態の両方のセッションを含め、アプライアンス上の現在のセッションを表示します。  
  
-   セッションのアクティブおよび最近使用したクエリを表示します。  
  
-   アクティブなセッションを終了します。  
  
いずれかを使用してこれらのアクションを実行できる、[アプライアンスの監視、管理コンソールを使用して](monitor-the-appliance-by-using-the-admin-console.md)または[システム ビュー](tsql-system-views.md) SQL コマンドを次に示すようを使用します。  
  
いずれかの方法を使用してセッションを管理するために必要なアクセス許可は同じと記載されて[ログインの管理、ユーザー、およびデータベース ロールにアクセス許可の付与](grant-permissions.md#grant-permissions-to-manage-logins-users-and-database-roles)します。  
  
## <a name="manage-sessions-by-using-the-admin-console"></a>管理コンソールを使用してセッションを管理します。  
  
### <a name="to-view-current-sessions-by-using-the-admin-console"></a>管理コンソールを使用して現在のセッションを表示するには  
  
1.  上部のメニューでクリックして**セッション**します。  
  
2.  結果の一覧には、最近使用したすべてのセッションが表示されます。 'アクティブ' または 'アイドル' セッションのみを表示する をクリックして、**状態**列ヘッダーを状態で結果を並べ替えます。  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-the-admin-console"></a>管理者コンソールを使用して、セッションのアクティブおよび最近使用したクエリを表示するには  
  
1.  上部のメニューでクリックして**セッション**します。  
  
2.  結果の一覧で目的のセッションのセッション ID をクリックします。  
  
3.  結果として得られるクエリの一覧は、セッションの最新のクエリを示します。 クエリの詳細を表示する方法については、次を参照してください。[アクティブなクエリの監視](monitoring-active-queries.md)します。  
  
### <a name="to-end-sessions-by-using-the-admin-console"></a>管理者コンソールを使用してセッションを終了するには  
  
1.  上部のメニューでクリックして**セッション**します。  
  
2.  キャンセルするセッションのセッションの ID を検索します。  
  
3.  赤いをクリックして**X**セッションを終了するセッション ID の左側にします。 'アクティブ' または 'アイドル' の状態でセッションの赤いはだけ**X**; のみこれらのセッションを終了できます。  
  
## <a name="manage-sessions-by-using-system-views-and-sql-commands"></a>システム ビューと SQL コマンドを使用してセッションを管理します。  
  
### <a name="to-view-current-sessions-by-using-system-views"></a>システム ビューを使用して現在のセッションを表示するには  
使用[sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)を現在のセッションの一覧を生成します。  
  
この例では、すべてのセッション状態の 'Active' または 'アイドル' session_id、login_name、および状態を返します。  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions WHERE status='Active' OR status='Idle';  
```  
  
### <a name="to-view-active-and-recent-queries-for-a-session-by-using-system-views"></a>システム ビューを使用してセッションのアクティブなおよび最近のクエリを表示するには  
使用するセッションに関連付けられているアクティブおよび最近完了したクエリを表示する、 [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)と[sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)ビュー。 このクエリは、すべてのアクティブまたはアイドル状態のセッションと各セッション ID に関連付けられているアクティブなまたは最近のクエリの一覧を返します  
  
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
使用して、 [KILL](../t-sql/language-elements/kill-transact-sql.md)コマンドを現在のセッションを終了します。 使用して取得できますが、終了するプロセスのセッション ID が必要ですが、 [sys.dm_pdw_exec_sessions](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)ビュー。  
  
この例では、login_name、session_id、およびログイン名に基づいてセッションを検索する状態値を選択します。  
  
```sql  
SELECT session_id, login_name, status FROM sys.dm_pdw_exec_sessions;  
```  
  
KILL コマンドを使用して、'アクティブ' または 'アイドル' 状態でセッションを終了できます。  
  
```sql  
KILL 'SID137';  
```  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  

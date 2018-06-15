---
title: ワークロードの管理タスクの Analytics Platform System |Microsoft ドキュメント
description: Analytics Platform System でワークロードの管理タスク。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 16206cb5cefd68b19e1640592b903890808b5a31
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538792"
---
# <a name="workload-management-tasks-in-analytics-platform-system"></a>Analytics Platform System でのワークロードの管理タスク
Analytics Platform System でワークロードの管理タスク。

## <a name="view-login-members-of-each-resource-class"></a>各リソースのクラスのログインのメンバーを表示
SQL Server PDW で各リソース クラスのサーバー ロールのログインのメンバーを表示する方法について説明します。 このクエリを使用すると、各ログインで送信された要求の使用可能なリソースのクラスを確認します。  
  
リソース クラスの説明を参照してください。[ワークロード管理](workload-management.md)です。  
  
このクエリは、各リソースのクラスのメンバーシップの一覧を表示します。 次の 3 つのリソース クラス、mediumrc、largerc、および xlargerc があります。  
  
```sql  
SELECT l.name AS [member], r.name AS [server role]  
FROM sys.server_role_members AS rm  
JOIN sys.server_principals AS l  
  ON l.principal_id = rm.member_principal_id  
JOIN  
  sys.server_principals AS r  
  ON r.principal_id = rm.role_principal_id  
WHERE  
  ( l.[type] = 'S' OR l.[type] = 'U' OR l.[type] = 'G' )  
  AND r.[type] = 'R'  
  AND r.[name] in ('mediumrc', 'largerc', 'xlargerc');  
```  
  
ログインがこの一覧にない場合は、その要求は既定のリソースを受信します。 ログインが 1 つ以上のリソース クラスのメンバーである場合は、最大のクラスは、優先順位をいます。  
  
リソース割り当ては、「[ワークロード管理](workload-management.md)です。  
  
## <a name="change-the-system-resources-allocated-to-a-request"></a>変更要求に割り当てられたシステム リソース
リソースを把握する方法について説明で、SQL Server PDW 要求が実行されるクラスとし、その要求のシステム リソースを変更する方法です。 メンバーシップの変更、リソース クラスを使用して、要求を送信するログインの要求のリソースを変更すると、 [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md)ステートメントです。  
  
### <a name="step-1-determine-the-resource-class-for-the-login-running-the-request"></a>手順 1: では、要求を実行しているログインのリソース クラスを決定します。  
このクエリは、リソース クラスのサーバー ロールのメンバーシップのメンバーであるログインを表示します。 次の 3 つのリソース クラスがある**mediumrc**、 **largerc**、および**xlargerc**です。  
  
> [!IMPORTANT]  
> このクエリを持つログインによって実行される必要があります**CONTROL SERVER**権限です。 ログインなしで実行された場合**CONTROL SERVER**アクセス許可は、次のクエリのみが返されます、現在のログインのロールのメンバーシップ。  
  
```sql  
SELECT l.name AS [member], r.name AS [server role]  
FROM sys.server_role_members AS rm  
JOIN sys.server_principals AS l  
  ON l.principal_id = rm.member_principal_id  
JOIN  
  sys.server_principals AS r  
  ON r.principal_id = rm.role_principal_id  
WHERE  
  l.[type] = 'S'   
  AND r.[type] = 'R'  
  AND r.[name] in ('mediumrc', 'largerc', 'xlargerc');  
GO  
```  
  
リソース クラスのサーバー ロールのメンバーであるログインがない場合、結果のテーブルが空になります。 ここでは、クエリを返す場合 Ching をという名前のログイン、し Ching が、要求を送信するときに要求を受け取ります既定のシステム リソース、リソース クラスのシステム リソースよりも小さい。 ログインが 1 つ以上のリソース クラスのメンバーである場合は、最大のクラスは、優先順位をいます。  
  
各リソースのクラスのリソース割り当ての一覧は、次を参照してください。[ワークロード管理](workload-management.md)です。  
  
### <a name="step-2-run-the-request-under-a-login-with-different-resource-class-membership"></a>手順 2: 別のリソース クラスのメンバーシップを持つログインで要求を実行します。  
これには、拡大または縮小のシステム リソースと要求を実行する 2 つの方法があります。  
  
-   拡大または縮小のリソース クラスのメンバーである別のログインで要求を実行します。  
  
-   リソース クラスの役割のいずれかに必要なログインを追加します。 注意が必要です。 このオプションを選択します。ログインのリソース クラスを変更すると、ログインによって送信されるすべての要求に対するシステム リソースのレベルが変更されます。  
  
Ching largerc サーバー ロールのメンバーであるとします。 次の例では、ログイン Ching xlargerc サーバーの役割を追加する方法を示します。  
  
```sql  
ALTER SERVER ROLE xlargerc ADD MEMBER Ching;  
```  
  
Ching は、largerc と xlargerc サーバー ロールのメンバーであるようになりました。 Ching 要求を送信すると、要求 xlargerc のシステム リソースが表示されます。  
  
次の例は、戻る、Ching を mediumrc サーバーの役割に移動します。  新しいロールを変更するには、ログインを xlargerc、および largerc サーバーの役割から削除され、mediumrc サーバー ロールに追加する必要があります。  
  
```sql  
-- Move login Ching back to using medium system resources for requests.  
ALTER SERVER ROLE xlargerc DROP MEMBER Ching;  
ALTER SERVER ROLE largerc DROP MEMBER Ching;  
ALTER SERVER ROLE mediumrc ADD MEMBER Ching;  
```  
  
Ching は mediumrc サーバー ロールのメンバーであるようになりました。  次の例では、要求の既定のシステム リソースを Ching を変更します。  
  
```sql  
-- Move login Ching to use the default system resources for requests.  
ALTER SERVER ROLE mediumrc DROP MEMBER Ching;  
```  
  
リソース クラスのロールのメンバーシップを変更する方法の詳細については、次を参照してください。 [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md)です。  

## <a name="change-a-login-to-the-default-system-resources-for-its-requests"></a>ログインを要求の既定のシステム リソースに変更します。
既定値への SQL Server PDW ログインに割り当てられたシステム リソースの割り当てを変更する方法について説明します。 
  
リソース クラスの説明を参照してください[ワークロードの管理。](workload-management.md)  
  
ログインは、どのリソース クラスのサーバー ロールのメンバーではない、ログインで送信された要求は、既定のシステム リソース量に表示されます。  
  
Matt 現在リソース クラスのすべてのサーバー ロールのメンバーは、既定のリソースのみが表示される要求に戻すには、ログインがあるとします。  次の例は、すべての 3 つのリソース クラス サーバー ロールのメンバーシップを削除することにより、Matt の要求に既定のリソースを割り当てます。  
  
```sql  
--Give the requests submitted by Matt the default system resources   
--by dropping Matt from all resource class server roles.  
ALTER SERVER ROLE XLargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE LargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE MediumRC DROP MEMBER Matt;  
```  
  
## <a name="display-the-number-of-concurrency-slots-needed-for-a-waiting-request"></a>同時実行スロットの数に必要な待機中の要求の表示
スロットは、SQL Server PDW の実行を待機している要求で必要な同時実行の数を確認する方法について説明します。  
  
詳細については、次を参照してください。[ワークロード管理](workload-management.md)です。  
  
要求は、実行されることがなく長時間待機している可能性があります。 要求が必要な同時実行スロットの番号を確認要求をトラブルシューティングする方法の 1 つです。  次の例では、各待機中の要求で必要な同時実行スロットの数を示します。  
  
```sql  
--Display the number of concurrency slots required   
--for each request that is waiting to run.  
SELECT request_id, concurrency_slots_used AS [Slots Needed], resource_class AS [Resource Class]  
FROM sys.dm_pdw_resource_waits;  
```  
  
  
## <a name="see-also"></a>参照  
[ワークロードの管理](workload-management.md)  
  

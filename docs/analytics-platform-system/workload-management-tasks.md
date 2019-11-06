---
title: ワークロードの管理タスク - Analytics Platform System |Microsoft Docs
description: Analytics Platform System でワークロードの管理タスク。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ea6b3785914781e73a8570c1282741f7c4b56298
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959753"
---
# <a name="workload-management-tasks-in-analytics-platform-system"></a>Analytics Platform System でワークロードの管理タスク
Analytics Platform System でワークロードの管理タスク。

## <a name="view-login-members-of-each-resource-class"></a>各リソース クラスのログインのメンバーの表示
SQL Server PDW で各リソース クラスのサーバー ロールのログインのメンバーを表示する方法について説明します。 各ログインによって送信された要求の許可されているリソースのクラスを確認するには、このクエリを使用します。  
  
リソース クラスの説明を参照してください。[ワークロード管理](workload-management.md)します。  
  
このクエリでは、各リソース クラスのメンバーシップの一覧が表示されます。 次の 3 つのリソース クラス、mediumrc、largerc、および xlargerc があります。  
  
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
  
ログインがこの一覧にない場合は、その要求は既定のリソースを受信します。 ログインが 1 つ以上のリソース クラスのメンバーである場合は、最大クラスは、優先順位をいます。  
  
リソース割り当ては、「[ワークロード管理](workload-management.md)します。  
  
## <a name="change-the-system-resources-allocated-to-a-request"></a>変更要求に割り当てられたシステム リソース
どのリソースを把握する方法について説明します、SQL Server PDW の要求が実行されているクラスとし、その要求のシステム リソースを変更する方法。 リソースの変更要求を使用して、要求を送信するログインのリソース クラスのメンバーシップを変更する必要があります、 [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md)ステートメント。  
  
### <a name="step-1-determine-the-resource-class-for-the-login-running-the-request"></a>手順 1:要求を実行しているログインのリソース クラスを決定します。  
このクエリは、リソース クラスのサーバー ロールのメンバーシップのメンバーであるログインを表示します。 次の 3 つのリソース クラスがある**mediumrc**、 **largerc**、および**xlargerc**します。  
  
> [!IMPORTANT]  
> このクエリを持つログインによって実行される必要があります**CONTROL SERVER**権限。 ログインなしで実行する場合**CONTROL SERVER**権限、このクエリのみが返されます、現在のログインのロールのメンバーシップ。  
  
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
  
リソース クラスのサーバー ロールのメンバーであるログインがない場合、結果のテーブルが空になります。 ここでは、クエリ Ching という名前のログインを返す場合、Ching、要求を送信すると、要求を受け取ります既定のシステム リソース、リソース クラスのシステム リソースよりも小さい。 ログインが 1 つ以上のリソース クラスのメンバーである場合は、最大クラスは、優先順位をいます。  
  
各リソース クラスのリソース割り当ての一覧は、次を参照してください。[ワークロード管理](workload-management.md)します。  
  
### <a name="step-2-run-the-request-under-a-login-with-different-resource-class-membership"></a>手順 2:別のリソース クラスのメンバーシップを持つログインで要求を実行します。  
いずれかの拡大または縮小のシステム リソースで要求を実行する 2 つの方法はあります。  
  
-   大きいまたは小さいリソース クラスのメンバーである別のログインで要求を実行します。  
  
-   リソース クラスのロールのいずれかに必要なログインを追加します。 注意が必要です。 このオプションを選択します。ログインのリソース クラスを変更すると、システムのリソース レベルのログインによって送信されたすべての要求が変更されます。  
  
Ching largerc のサーバー ロールのメンバーであるとします。 次の例では、ログイン Ching xlargerc サーバーの役割を追加する方法を示します。  
  
```sql  
ALTER SERVER ROLE xlargerc ADD MEMBER Ching;  
```  
  
Ching は largerc、および xlargerc のサーバーの役割のメンバーであるようになりました。 Ching では、要求を送信するときに、要求 xlargerc のシステム リソースが表示されます。  
  
次の例は、戻る、Ching を mediumrc サーバーの役割に移動します。  新しいロールを変更するには、ログインを xlargerc のと largerc のサーバーの役割から削除され、mediumrc のサーバー ロールに追加する必要があります。  
  
```sql  
-- Move login Ching back to using medium system resources for requests.  
ALTER SERVER ROLE xlargerc DROP MEMBER Ching;  
ALTER SERVER ROLE largerc DROP MEMBER Ching;  
ALTER SERVER ROLE mediumrc ADD MEMBER Ching;  
```  
  
Ching は mediumrc のサーバー ロールのメンバーであるようになりました。  次の例では、要求の既定のシステム リソースを用意する Ching を変更します。  
  
```sql  
-- Move login Ching to use the default system resources for requests.  
ALTER SERVER ROLE mediumrc DROP MEMBER Ching;  
```  
  
リソース クラス ロールのメンバーシップを変更する方法についての詳細については、次を参照してください。 [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md)します。  

## <a name="change-a-login-to-the-default-system-resources-for-its-requests"></a>ログインを要求の既定のシステム リソースに変更します。
既定値へのログインを SQL Server PDW に割り当てられたシステム リソースの割り当てを変更する方法について説明します。 
  
リソース クラスの説明を参照してください[ワークロード管理。](workload-management.md)  
  
ログインは、どのリソース クラスのサーバー ロールのメンバーではない、ログインで送信された要求に既定のシステム リソースの量が表示されます。  
  
ログイン Matt は、現在リソース クラスのすべてのサーバー ロールのメンバーと既定のリソースのみを受信する要求に戻す必要があるとします。  次の例 3 つのリソース クラスのすべてのサーバー ロールからのメンバーシップを削除することにより、Matt の要求に既定のリソースを割り当てます。  
  
```sql  
--Give the requests submitted by Matt the default system resources   
--by dropping Matt from all resource class server roles.  
ALTER SERVER ROLE XLargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE LargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE MediumRC DROP MEMBER Matt;  
```  
  
## <a name="display-the-number-of-concurrency-slots-needed-for-a-waiting-request"></a>待ちの要求についての同時実行スロットの数に必要な表示
同時実行スロットは、SQL Server PDW の実行を待機している要求で必要な数を把握する方法について説明します。  
  
詳細については、次を参照してください。[ワークロード管理](workload-management.md)します。  
  
要求は、実行されることがなく長時間待機している可能性があります。 要求が必要な同時実行スロットの数を確認要求をトラブルシューティングする方法の 1 つです。  次の例では、各待機中の要求で必要な同時実行スロットの数を示します。  
  
```sql  
--Display the number of concurrency slots required   
--for each request that is waiting to run.  
SELECT request_id, concurrency_slots_used AS [Slots Needed], resource_class AS [Resource Class]  
FROM sys.dm_pdw_resource_waits;  
```  
  
  
## <a name="see-also"></a>参照  
[ワークロード管理](workload-management.md)  
  

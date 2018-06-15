---
title: sys.dm_external_script_execution_stats |Microsoft ドキュメント
ms.custom: ''
ms.date: 09/16/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_execution_stats
- sys.dm_external_script_execution_stats_TSQL
- dm_external_script_execution_stats
- dm_external_script_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_execution_stats dynamic management view
ms.assetid: 2e99f026-ceb2-42a2-a549-c71d31ed0cf4
caps.latest.revision: 5
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: 01380a29665d848fff1620787a97aabbcdac4033
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34468358"
---
# <a name="sysdmexternalscriptexecutionstats"></a>sys.dm_external_script_execution_stats
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]


  外部スクリプト要求の種類ごとに 1 つの行を返します。 外部スクリプト要求は、サポートされている外部スクリプト言語でグループ化されます。 登録されている外部スクリプト関数ごとに 1 つの行が生成されます。 `rxExec`など、任意の外部スクリプト関数は、親プロセスによって送信された場合を除き、記録されません。

 
  
> [!NOTE]  
>  この DMV は、外部スクリプト実行をサポートする機能をインストールして有効にした場合にのみ使用できます。 R スクリプトでこれを行う方法については、「[SQL Server R Services (In-Database) をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)」をご覧ください。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|language|**nvarchar**|登録されている外部スクリプト言語の名前です。 各外部スクリプトは、スクリプト要求で言語を指定して、関連付けられているランチャーを開始する必要があります。 |  
|counter_name|**nvarchar**|登録されている外部スクリプト関数の名前です。 NULL 値は許可されません。|  
|counter_value|**整数 (integer)**|登録されている外部スクリプト関数がサーバーで呼び出されたインスタンスの合計数です。 この値は、機能がインスタンスにインストールされてからの累積値で、リセットすることはできません。|  

  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
> [!NOTE]  
>  外部スクリプトを実行するユーザーはさらに EXECUTE ANY EXTERNAL SCRIPT 権限も持っている必要がありますが、管理者はこの権限がなくてもこの DMV を使用できます。 
  
## <a name="remarks"></a>解説  
  この DMV は、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] で提供される新しい外部スクリプト実行機能の全体的な使用状況を監視するために、内部テレメトリ用に提供されます。 登録されている外部スクリプト関数が呼び出されるたびにスタート パッドがディスクベースのカウンターを増分すると、テレメトリ サービスが開始します。

一般に、パフォーマンス カウンターは、それを生成したプロセスがアクティブな間だけ有効です。 したがって、DMV に対するクエリは、実行を停止したサービスの詳細なデータを表示できません。 たとえば、ランチャーが外部スクリプトを実行し、極めて短い時間でそれを完了した場合、従来の DMV ではデータが何も表示されない可能性があります。

したがって、インスタンスがシャットダウンされた場合でも、この DMV によって追跡されるカウンターは実行状態を維持し、sys.dm_external_script_requests の状態はディスクへの書き込みを使用して保持されます。

   
  
### <a name="r-counter-values"></a>R カウンターの値
 現在、[!INCLUDE[ssCurrent_md](../../includes/sscurrent-md.md)] でサポートされている唯一の外部スクリプト言語は R です。R 言語に対する外部スクリプト要求は、[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] によって処理されます。 

R、この DMV はインスタンスで行われる R 呼び出しの数を追跡します。 たとえば、 `rxLinMod` が呼び出されて並列で実行された場合、このカウンターは 1 だけ増やされます。
 
R 言語の場合、 *counter_name* フィールドに表示されるカウンターの値は、登録されている ScaleR 関数の名前を表します。 *counter_value* フィールドの値は、特定の ScaleR 関数を呼び出したインスタンスの累積数を表します。 

インスタンスで機能がインストールされて有効にされるとカウントが開始し、状態を保持しているファイルが削除されるか、管理者によって上書きされるまで、カウントは累積されます。 したがって、 *counter_value*の値をリセットすることは通常は不可能です。 セッション、カレンダーの時間、またはその他の間隔で使用状況を監視する必要がある場合は、カウントをテーブルに取得することをお勧めします。

### <a name="registration-of-external-script-functions"></a>外部スクリプト関数の登録

R 言語は任意のスクリプトをサポートし、R コミュニティでは多数のパッケージが提供されており、それぞれが独自の関数とメソッドを含んでいます。 ただし、この DMV は、SQL Server R Services でインストールされた ScaleR 関数のみを監視します。

これらの関数の登録は機能がインストールされると実行され、登録された関数を追加または削除することはできません。

## <a name="examples"></a>使用例  
  
### <a name="viewing-the-number-of-r-scripts-run-on-the-server"></a>サーバー上で実行されている R スクリプトの数を表示する  
 次の例は、R 言語の外部スクリプト実行の累積数を表示します。  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'R';
```  

  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md) 
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  


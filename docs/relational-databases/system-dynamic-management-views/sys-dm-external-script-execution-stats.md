---
title: sys.dm_external_script_execution_stats |Microsoft Docs
ms.custom: ''
ms.date: 10/28/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
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
author: HeidiSteen
ms.author: heidist
manager: cgronlund
ms.openlocfilehash: 8bdbaf1fdb0fb0c27127611ace0fac00d861838f
ms.sourcegitcommit: c2322c1a1dca33b47601eb06c4b2331b603829f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "50743137"
---
# <a name="sysdmexternalscriptexecutionstats"></a>sys.dm_external_script_execution_stats
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

外部スクリプト要求の種類ごとに 1 つの行を返します。 外部スクリプト要求は、サポートされている外部スクリプト言語でグループ化されます。 登録されている外部スクリプト関数ごとに 1 つの行が生成されます。 `rxExec`など、任意の外部スクリプト関数は、親プロセスによって送信された場合を除き、記録されません。
  
> [!NOTE]  
> この動的管理ビュー (DMV) は、インストールして、外部スクリプトの実行をサポートする機能を有効になっている場合にのみ使用できます。 詳細については、[SQL Server 2016 R Services](../../advanced-analytics/r/sql-server-r-services.md)と[SQL Server 2017 での Machine Learning サービス (R、Python)](../../advanced-analytics/what-is-sql-server-machine-learning.md)を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|language|**nvarchar**|登録されている外部スクリプト言語の名前です。 各外部スクリプトは、スクリプト要求で言語を指定して、関連付けられているランチャーを開始する必要があります。 |  
|counter_name|**nvarchar**|登録されている外部スクリプト関数の名前です。 NULL 値は許可されません。|  
|counter_value|**整数 (integer)**|登録されている外部スクリプト関数がサーバーで呼び出されたインスタンスの合計数です。 この値は、機能がインスタンスにインストールされてからの累積値で、リセットすることはできません。|  

  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
> [!NOTE]  
>  外部スクリプトを実行するユーザーはさらに EXECUTE ANY EXTERNAL SCRIPT 権限も持っている必要がありますが、管理者はこの権限がなくてもこの DMV を使用できます。 
  
## <a name="remarks"></a>コメント  
  この DMV は、[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] で提供される新しい外部スクリプト実行機能の全体的な使用状況を監視するために、内部テレメトリ用に提供されます。 登録されている外部スクリプト関数が呼び出されるたびにスタート パッドがディスクベースのカウンターを増分すると、テレメトリ サービスが開始します。

一般に、パフォーマンス カウンターは、それを生成したプロセスがアクティブな間だけ有効です。 したがって、DMV に対するクエリは、実行を停止したサービスの詳細なデータを表示できません。 たとえば、起動ツールでは、外部スクリプトを実行すると、まだそれを非常に高速に完了した、従来の DMV 可能性がありますすべてのデータは表示されません。

したがって、インスタンスがシャットダウンされた場合でも、この DMV によって追跡されるカウンターは実行状態を維持し、sys.dm_external_script_requests の状態はディスクへの書き込みを使用して保持されます。

   
  
### <a name="counter-values"></a>カウンターの値
SQL Server 2016 でサポートされている唯一の外部の言語は R と、外部スクリプト要求で処理されます[!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]します。 SQL Server 2017 では、R と Python の両方がサポートされている外部の言語と外部スクリプト要求で処理されます[!INCLUDE[rsql_productname_md](../../includes/rsql-productnamenew-md.md)]します。

R では、この DMV はインスタンスで行われた R 呼び出しの数を追跡します。 たとえば、 `rxLinMod` が呼び出されて並列で実行された場合、このカウンターは 1 だけ増やされます。
 
R 言語の場合、 *counter_name* フィールドに表示されるカウンターの値は、登録されている ScaleR 関数の名前を表します。 *counter_value* フィールドの値は、特定の ScaleR 関数を呼び出したインスタンスの累積数を表します。 

Python の場合は、この DMV は、インスタンスで行われる Python の呼び出しの数を追跡します。

インスタンスで機能がインストールされて有効にされるとカウントが開始し、状態を保持しているファイルが削除されるか、管理者によって上書きされるまで、カウントは累積されます。 したがって、 *counter_value*の値をリセットすることは通常は不可能です。 セッション、カレンダーの時間、またはその他の間隔で使用状況を監視する必要がある場合は、カウントをテーブルに取得することをお勧めします。

### <a name="registration-of-external-script-functions-in-r"></a>R の外部スクリプト関数の登録

R は、任意のスクリプトをサポートし、R コミュニティがそれぞれ独自の関数とメソッドを持つ多く数千のパッケージを提供します。 ただし、この DMV は、SQL Server R Services でインストールされた ScaleR 関数のみを監視します。

これらの関数の登録は機能がインストールされると実行され、登録された関数を追加または削除することはできません。

## <a name="examples"></a>使用例  
  
### <a name="viewing-the-number-of-r-scripts-run-on-the-server"></a>サーバー上で実行されている R スクリプトの数を表示する  
 次の例は、R 言語の外部スクリプト実行の累積数を表示します。  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'R';
```  

### <a name="viewing-the-number-of-python-scripts-run-on-the-server"></a>サーバー上のスクリプト実行の Python の数を表示します。  
 次の例では、Python 言語用の外部スクリプト実行の累積数が表示されます。  
  
```  
SELECT counter_name, counter_value   
FROM sys.dm_external_script_execution_stats   
WHERE language = 'Python';
```  

  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md) 
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  


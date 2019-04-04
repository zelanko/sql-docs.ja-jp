---
title: sys.dm_external_script_requests |Microsoft Docs
ms.custom: ''
ms.date: 10/28/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_requests
- sys.dm_external_script_requests_TSQL
- dm_external_script_requests
- dm_external_script_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_requests dynamic management view
ms.assetid: e7e7c50f-b8b2-403c-b8c8-1955da5636c3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 54c572acac645146e3db18195a0dbe5b794effdc
ms.sourcegitcommit: c2322c1a1dca33b47601eb06c4b2331b603829f1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2018
ms.locfileid: "50743190"
---
# <a name="sysdmexternalscriptrequests"></a>sys.dm_external_script_requests
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

外部スクリプトを実行しているアクティブなワーカー アカウントごとに行を返します。
  
> [!NOTE] 
>  
> この動的管理ビュー (DMV) は、インストールして、外部スクリプトの実行をサポートする機能を有効になっている場合にのみ使用できます。 詳細については、[SQL Server 2016 R Services](../../advanced-analytics/r/sql-server-r-services.md)と[SQL Server 2017 での Machine Learning サービス (R、Python)](../../advanced-analytics/what-is-sql-server-machine-learning.md)を参照してください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**一意識別子**|外部スクリプト要求を送信したプロセスの ID です。 これは、ID に対応するプロセスが受信すると [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]|  
|language|**nvarchar**|サポートされているスクリプト言語を表すキーワードです。 |  
|degree_of_parallelism|**int**|作成された並列処理の数を示す数値です。 この値は、要求された並列処理の数と異なる場合があります。|  
|external_user_name|**nvarchar**|スクリプトが実行されたときの Windows ワーカー アカウント。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
> [!NOTE]
>   
>  外部スクリプトを実行するユーザーはさらに EXECUTE ANY EXTERNAL SCRIPT 権限も持っている必要がありますが、管理者はこの権限がなくてもこの DMV を使用できます。 
  
## <a name="remarks"></a>コメント  

このビューは、スクリプト言語の識別子を使用してフィルター処理することができます。

このビューはまた、スクリプトが実行されているワーカー アカウントも返します。 外部のスクリプトで使用されるワーカー アカウントについては、(SQLRUserGroup)」セクションの処理に使用される Id を参照してください。[は、SQL Server Machine Learning Services の機能拡張フレームワークのセキュリティの概要](../../advanced-analytics/concepts/security.md#sqlrusergroup)します。

**external_script_request_id** フィールドに返される GUID はまた、一時ファイルが格納されている、セキュリティで保護されたディレクトリのファイル名も表します。 MSSQLSERVER01 などの各ワーカー アカウントは、単一の SQL ログインまたは Windows ユーザーを表します。複数のスクリプト要求を実行するために使用される場合があります。 既定では、これらの一時ファイルは、要求したスクリプトが完了するとクリーンアップされます。
 
この DMV は、アクティブなプロセスを監視するだけであり、既に完了しているスクリプトをレポートすることはできません。 スクリプトの期間を追跡する必要がある場合は、スクリプト内にタイミング情報を追加し、スクリプトの実行の一部としてキャプチャすることをお勧めします。

## <a name="examples"></a>使用例  
  
### <a name="viewing-the-currently-active-r-scripts-for-a-particular-process"></a>特定のプロセスで現在アクティブな R スクリプトを表示する 
 次の例では、現在のインスタンスで実行されている外部スクリプト実行の数を表示します。  
  
```  
SELECT external_script_request_id 
  , [language]
  , degree_of_parallelism
  , external_user_name
FROM sys.dm_external_script_requests; 
```  

[結果]  


external_script_request_id  |language  |degree_of_parallelism  |external_user_name  
---------|---------|---------|---------
183EE6FC-7399-4318-AA2E-7A6C68E435A8     |     R    |      1   |  MSSQLSERVER01       


  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  


---
title: sys.dm_external_script_requests |Microsoft Docs
ms.custom: ''
ms.date: 06/24/2016
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
ms.openlocfilehash: fb5597a9163ac87e9f6c08421025340cf8263b44
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47843470"
---
# <a name="sysdmexternalscriptrequests"></a>sys.dm_external_script_requests
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

外部スクリプトを実行しているアクティブなワーカー アカウントごとに行を返します。
 
  
> [!NOTE] 
>  
>  この DMV は、外部スクリプト実行をサポートする機能をインストールして有効にした場合にのみ使用できます。 R スクリプトでこれを行う方法については、「[SQL Server R Services (In-Database) をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)」をご覧ください。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**一意識別子**|外部スクリプト要求を送信したプロセスの ID です。 これは、ID に対応するプロセスが受信すると [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]|  
|language|**nvarchar**|サポートされているスクリプト言語を表すキーワードです。 現時点では、 `R` のみサポートされています。|  
|degree_of_parallelism|**int**|作成された並列処理の数を示す数値です。 この値は、要求された並列処理の数と異なる場合があります。|  
|external_user_name|**nvarchar**|スクリプトが実行されたときの Windows ワーカー アカウント。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
> [!NOTE]
>   
>  外部スクリプトを実行するユーザーはさらに EXECUTE ANY EXTERNAL SCRIPT 権限も持っている必要がありますが、管理者はこの権限がなくてもこの DMV を使用できます。 
  
## <a name="remarks"></a>Remarks  

このビューは、スクリプト言語の識別子を使用してフィルター処理することができます。

このビューはまた、スクリプトが実行されているワーカー アカウントも返します。 R スクリプトで使用するワーカー アカウントについては、「[SQL Server R サービスのユーザー アカウント プールを変更する](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)」を参照してください。

**external_script_request_id** フィールドに返される GUID はまた、一時ファイルが格納されている、セキュリティで保護されたディレクトリのファイル名も表します。 MSSQLSERVER01 などの各ワーカー アカウントは、単一の SQL ログインまたは Windows ユーザーを表します。複数のスクリプト要求を実行するために使用される場合があります。 既定では、これらの一時ファイルは、要求したスクリプトが完了するとクリーンアップされます。 これらのファイルを一定期間、デバッグ目的で保持する必要がある場合は、トピック「[高度な分析拡張機能の構成および管理](../../advanced-analytics/r-services/configure-and-manage-advanced-analytics-extensions.md)」の説明に従ってクリーンアップ フラグを変更することができます。  
 
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


  
## <a name="see-also"></a>関連項目  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  


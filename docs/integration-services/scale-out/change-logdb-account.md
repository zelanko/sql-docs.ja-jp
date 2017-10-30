---
title: "スケール アウト SSIS ログ記録のアカウントの変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ec785459e5f9585776d83cde3f460c1e79367e46
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="change-the-account-for-scale-out-logging"></a>スケール アウト ログのアカウントを変更します。
をスケール アウトでのパッケージを実行するときにイベント メッセージはログに記録 SSISDB に自動的に作成されたユーザーに**## MS_SSISLogDBWorkerAgentLogin ##**です。 このユーザーのログインは、SQL Server 認証を使用します。 アカウントを変更し、次のように、次の手順。

## <a name="1-create-a-user-of-ssisdb"></a>1.SSISDB のユーザーを作成します。
データベース ユーザーを作成する手順については、次を参照してください。[データベース ユーザーを作成](../../relational-databases/security/authentication-access/create-a-database-user.md)です。

## <a name="2-add-the-user-to-database-role-ssisclusterworker"></a>2.データベース ロール ssis_cluster_worker にユーザーを追加します。

データベース ロールに参加する手順については、次を参照してください。[ロールの追加](../../relational-databases/security/authentication-access/join-a-role.md)です。

## <a name="3-update-logging-information-in-ssisdb"></a>3.SSISDB にログ情報を更新します。
[カタログ] のストアド プロシージャを呼び出します。[update_logdb_info] Sql Server 名と接続文字列パラメーターとして使用します。

#### <a name="example"></a>例
```sql
SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
EXEC [internal].[update_logdb_info] @serverName, @connectionString
GO
```

## <a name="4-restart-scale-out-worker-service"></a>4.スケール アウト Worker サービスを再起動します。

> [!NOTE]
> ログ記録用の Windows ユーザー アカウントを使用する場合、スケール アウト Worker サービスを実行している同じアカウントがあります。 それ以外の場合、SQL Server にログインが失敗します。


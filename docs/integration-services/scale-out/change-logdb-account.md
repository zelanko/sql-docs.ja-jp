---
title: "Scale Out ログのアカウントの変更 | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dcedbe0d2c2ef2c2089af1e2a8b31fbeb75ce2fc
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="change-the-account-for-scale-out-logging"></a>Scale Out ログのアカウントの変更
スケール アウトでパッケージを実行すると、自動作成ユーザーの **##MS_SSISLogDBWorkerAgentLogin##** を利用し、イベント メッセージが SSISDB にログ記録されます。 このユーザーのログインでは、SQL Server 認証が使用されます。 アカウントを変更するには、以下の手順を実行します。

## <a name="1-create-a-user-of-ssisdb"></a>1.SSISDB のユーザーを作成する
データベース ユーザーの作成方法については、「[データベース ユーザーの作成](../../relational-databases/security/authentication-access/create-a-database-user.md)」を参照してください。

## <a name="2-add-the-user-to-database-role-ssisclusterworker"></a>2.データベース ロール ssis_cluster_worker にユーザーを追加する

データベース ロールに参加する方法については、「[ロールの追加](../../relational-databases/security/authentication-access/join-a-role.md)」を参照してください。

## <a name="3-update-logging-information-in-ssisdb"></a>3.SSISDB のログイン情報を更新する
Sql Server 名と接続文字列 (パラメーター) を指定し、ストアド プロシージャ [catalog].[update_logdb_info] を呼び出します。

#### <a name="example"></a>例
```sql
SET @serverName = CONVERT(sysname, SERVERPROPERTY('servername'))
SET @connectionString = 'Data Source=' + @serverName + ';Initial Catalog=SSISDB;Integrated Security=SSPI;'
EXEC [internal].[update_logdb_info] @serverName, @connectionString
GO
```

## <a name="4-restart-scale-out-worker-service"></a>4.Scale Out Worker サービスを再起動する

> [!NOTE]
> ログ記録に Windows ユーザー アカウントを使用する場合、Scale Out Worker サービスを実行しているアカウントと同じアカウントにする必要があります。 同じ出ない場合、SQL Server にログインできません。

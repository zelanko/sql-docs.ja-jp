---
title: データベース メールと電子メール アラートは、Linux 上の SQL エージェントの |Microsoft Docs
description: この記事は、SQL Server on Linux でのデータベース メールと電子メール アラートを使用する方法を説明します
author: meet-bhagdev
ms.author: meetb
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: tbd
ms.openlocfilehash: 2d9abbc37a576ad86823cfd8b3cb5f8401dca71d
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52394845"
---
# <a name="db-mail-and-email-alerts-with-sql-agent-on-linux"></a>データベース メールと Linux 上の SQL エージェントと電子メール アラート

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

次の手順は、データベース メールを設定し、SQL Server エージェントで使用する方法を説明 (**mssql server エージェント**) Linux 上。 

## <a name="1-enable-db-mail"></a>1.データベース メールを有効にします。

```sql
USE master 
GO 
sp_configure 'show advanced options',1 
GO 
RECONFIGURE WITH OVERRIDE 
GO 
sp_configure 'Database Mail XPs', 1 
GO 
RECONFIGURE  
GO  
```

## <a name="2-create-a-new-account"></a>2.[新しいアカウントを作成する]
```sql
EXECUTE msdb.dbo.sysmail_add_account_sp 
@account_name = 'SQLAlerts', 
@description = 'Account for Automated DBA Notifications', 
@email_address = 'sqlagenttest@gmail.com', 
@replyto_address = 'sqlagenttest@gmail.com', 
@display_name = 'SQL Agent', 
@mailserver_name = 'smtp.gmail.com', 
@port = 587, 
@enable_ssl = 1, 
@username = 'sqlagenttest@gmail.com', 
@password = '<password>' 
GO
```

## <a name="3-create-a-default-profile"></a>3.既定のプロファイルを作成します。

```sql
EXECUTE msdb.dbo.sysmail_add_profile_sp 
@profile_name = 'default', 
@description = 'Profile for sending Automated DBA Notifications' 
GO
```

## <a name="4-add-the-database-mail-account-to-a-database-mail-profile"></a>4.データベース メール プロファイルへのデータベース メール アカウントを追加します。
```sql
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp 
@profile_name = 'default', 
@principal_name = 'public', 
@is_default = 1 ; 
 ```
 
## <a name="5-add-account-to-profile"></a>5.アカウントをプロファイルに追加します。 
```sql
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp   
@profile_name = 'default',   
@account_name = 'SQLAlerts',   
@sequence_number = 1;  
 ```
 
## <a name="6-send-test-email"></a>6.テスト電子メールを送信します。
> [!NOTE]
> 電子メール クライアントに移動し、"安全性が低いクライアント許可メールを送信します"を有効にする必要があります。 すべてのクライアントは、電子メール、デーモンとしてデータベース メールを認識します。

```
EXECUTE msdb.dbo.sp_send_dbmail 
@profile_name = 'default', 
@recipients = 'recipient-email@gmail.com', 
@Subject = 'Testing DBMail', 
@Body = 'This message is a test for DBMail' 
GO
```

## <a name="7-set-db-mail-profile-using-mssql-conf-or-environment-variable"></a>7.Mssql conf または環境変数を使用してデータベース メール プロファイルの設定
Mssql conf ユーティリティまたは環境変数を使用すると、データベース メール プロファイルを登録します。 この場合、既定のプロファイルがましょう。

```bash
# via mssql-conf
sudo /opt/mssql/bin/mssql-conf set sqlagent.databasemailprofile default
# via environment variable
MSSQL_AGENT_EMAIL_PROFILE=default
```

## <a name="8-set-up-an-operator-for-sqlagent-job-notifications"></a>8.SQLAgent ジョブ通知のオペレーターを設定します。 

```sql
EXEC msdb.dbo.sp_add_operator 
@name=N'JobAdmins',  
@enabled=1, 
@email_address=N'recipient-email@gmail.com',  
@category_name=N'[Uncategorized]' 
GO 
```

## <a name="9-send-email-when-agent-test-job-succeeds"></a>9.'エージェントのテスト ジョブ' が成功したときに電子メールを送信します。 

```
EXEC msdb.dbo.sp_update_job 
@job_name='Agent Test Job', 
@notify_level_email=1, 
@notify_email_operator_name=N'JobAdmins' 
GO
```

## <a name="next-steps"></a>次の手順
SQL Server エージェントを使用して、作成、スケジュール、およびジョブを実行する方法の詳細については、[Linux 上の SQL Server エージェント ジョブの実行](sql-server-linux-run-sql-server-agent-job.md)を参照してください。

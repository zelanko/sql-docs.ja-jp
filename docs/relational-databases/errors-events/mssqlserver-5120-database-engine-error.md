---
title: MSSQLSERVER_5228 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5120 (Database Engine error)
ms.assetid: ''
author: PijoCoder
ms.author: mathoma
ms.openlocfilehash: ff8fb262b643390f2914a4a5e6c42dcc887206f8
ms.sourcegitcommit: 66407a7248118bb3e167fae76bacaa868b134734
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/21/2020
ms.locfileid: "81728619"
---
# <a name="mssqlserver_5120"></a>MSSQLSERVER_5120
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|5120|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DSK_FCB_FAILURE|  
|メッセージ テキスト|テーブル エラー:物理ファイル "%.*ls" を開けません。 オペレーティング システム エラー %d: "%ls"。|  
  
## <a name="explanation"></a>説明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でデータベース ファイルを開けませんでした。  メッセージに示されたオペレーティング システム エラーにより、エラーのより具体的な根本原因が示されます。 このエラーは、[17204](mssqlserver-17204-database-engine-error.md) や [17207](mssqlserver-17207-database-engine-error.md) などの他のエラーと共に表示されることがよくあります
  
## <a name="user-action"></a>ユーザーの操作  
  
  オペレーティング システム エラーを診断して修正してから、操作を再試行してください。 Microsoft で領域の発生している製品の領域を絞り込むのに役立つ、複数の状態があります。 
  
### <a name="access-is-denied"></a>アクセスが拒否されました 
```Access is Denied``` オペレーティング システム エラー = 5 を取得している場合は、次の方法を検討してください。
   -  エクスプローラーでファイルのプロパティを参照して、ファイルに設定されているアクセス許可を確認します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、Windows グループを使用して、さまざまなファイル リソースに Access Control をプロビジョニングします。 適切なグループ [SQLServerMSSQLUser$ComputerName$MSSQLSERVER や SQLServerMSSQLUser$ComputerName$InstanceName などの名前] に、エラー メッセージで言及されているデータベース ファイルに対して必要なアクセス許可が付与されていることを確認します。 詳細については、「[データベース エンジン アクセスのファイル システム権限の構成](../../2014/database-engine/configure-windows/configure-file-system-permissions-for-database-engine-access.md)」を参照してください。 Windows グループに、実際に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス開始アカウントまたはサービス SID が含まれていることを確認します。
   -  現在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスの実行に使用されているユーザー アカウントを確認します。 Windows タスク マネージャーを使用して、この情報を取得できます。 実行可能ファイル "sqlservr.exe" の "ユーザー名" の値を探します。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントを最近変更した場合は、[SQL Server 構成マネージャー](../sql-server-configuration-manager.md) ユーティリティを使用してこの操作を実行する方法がサポートされています。 
   -  操作の種類 (サーバー起動中にデータベースを開く、データベースのアタッチ、データベースの復元など) によっては、偽装とデータベース ファイルへのアクセスに使用されるアカウントが異なる場合があります。 トピック「[データ ファイルとログ ファイルのセキュリティ保護](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms189128(v=sql.105)?redirectedfrom=MSDN)」を確認して、どの操作によってどのアクセス許可が、どのアカウントに設定されるかを理解してください。 Windows SysInternals [Process Monitor](https://docs.microsoft.com/sysinternals/downloads/procmon) などのツールを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのサービス開始アカウント [またはサービス SID]、または偽装されたアカウントのセキュリティ コンテキストにおいて、ファイルへのアクセスが行われているかどうかを把握します。

      [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって、ALTER DATABASE または CREATE DATABASE 操作を実行するログインのユーザー資格情報が偽装されている場合は、Process Monitor ツールに次の情報が表示されます (一例)。
        ```Date & Time:      3/27/2010 8:26:08 PM
        Event Class:        File System
        Operation:          CreateFile
        Result:                ACCESS DENIED
        Path:                  C:\Program Files\Microsoft SQL Server\MSSQL13.SQL2016\MSSQL\DATA\attach_test.mdf
        TID:                   4288
        Duration:             0.0000366
        Desired Access:Generic Read/Write
        Disposition:        Open
        Options:            Synchronous IO Non-Alert, Non-Directory File, Open No Recall
        Attributes:          N
        ShareMode:       Read
        AllocationSize:   n/a
        Impersonating: DomainName\UserName```
  
  
### Attaching Files that Reside on a Network-attached storage  
If you cannot re-attach a database that resides on network-attached storage, a message like this may be logged in the Application log:

```Msg 5120, Level 16, State 101, Line 1 Unable to open the physical file "\\servername\sharename\filename.mdf". Operating system error 5: (Access is denied.).```

This problem occurs because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resets the file permissions when the database is detached. When you try to reattach the database, a failure occurs because of limited share permissions.

To resolve, follow these steps:
1. Use the -T startup option to start [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Use this startup option to turn on trace flag 1802 in [SQL Server Configuration Manager](../sql-server-configuration-manager.md) (see [Trace Flags](../../t-sql/database-console-commands/dbcc-traceon-transact-sql.md) for information on 1802). For more information about how to change the startup parameters, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)

2. Use the following command to detach the database.
```tsql
 exec sp_detach_db DatabaseName
 go 
```

3. 次のコマンドを使用して、データベースを再アタッチします。
```tsql
exec sp_attach_db DatabaseName, '\\Network-attached storage_Path\DatabaseMDFFile.mdf', '\\Network-attached storage_Path\DatabaseLDFFile.ldf'
go
```
 

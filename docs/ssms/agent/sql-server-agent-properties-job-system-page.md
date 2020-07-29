---
title: '[SQL Server エージェントのプロパティ] ダイアログ ボックス ([ジョブ システム] ページ)'
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.job.f1
ms.assetid: e171d13e-1302-4f0e-88be-67d656aec8d3
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a0e33eb0b4999c608f2083d3023f046a2ecc640a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755124"
---
# <a name="sql-server-agent-properties-job-system-page"></a>[SQL Server エージェントのプロパティ] ダイアログ ボックス ([ジョブ システム] ページ)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスによるジョブの管理方法を表示および変更できます。  
  
## <a name="options"></a>オプション  
**[シャットダウン タイムアウト間隔 (秒)]**  
シャットダウンの前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがジョブの完了を待つ時間を秒数で指定します。 指定した時間が過ぎてもジョブが実行されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって強制的にジョブが停止されます。  
  
**[管理者以外のプロキシ アカウントを使用する]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントに管理者以外のプロキシ アカウントを設定します。 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] 以降のバージョンでは複数のプロキシがサポートされるため、このオプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] エージェントを管理する場合にのみ適用できます。  
  
**ユーザー名**  
管理者以外のプロキシ アカウントのユーザーの名前を入力します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]エージェントを管理する場合にのみ適用できます。  
  
**パスワード**  
管理者以外のプロキシ アカウントのユーザーのパスワードを入力します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]エージェントを管理する場合にのみ適用できます。  
  
**[ドメイン]**  
管理者以外のプロキシ アカウントのユーザーのドメインを入力します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では複数のプロキシがサポートされるため、このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]エージェントを管理する場合にのみ適用できます。  
  
## <a name="see-also"></a>参照  
[ジョブの実装](../../ssms/agent/implement-jobs.md)  
  

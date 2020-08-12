---
title: Resize the Job History Log
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 988035cab9bd8fa4035337068ec15032bb702802
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85644786"
---
# <a name="resize-the-job-history-log"></a>Resize the Job History Log

[!INCLUDE[applies-to-version/_ssnoversion.md](../../includes/applies-to-version/sqlserver.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このトピックでは、[!INCLUDE[msCoName](../../includes/msconame_md.md)] を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] エージェントのジョブ履歴ログのサイズ制限を設定する方法について説明します。

- **作業を開始する準備:**  

    [セキュリティ](#Security)  

- **ジョブ履歴ログのサイズ制限を設定する方法:**  

    [SQL Server Management Studio](#SSMS)

## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>はじめに  

### <a name="security"></a><a name="Security"></a>セキュリティ

詳細については、「 [SQL Server エージェントのセキュリティの実装](../../ssms/agent/implement-sql-server-agent-security.md)」をご覧ください。  

## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>SQL Server Management Studio の使用

"*生のサイズに基づいてジョブ履歴ログをサイズ変更するには*"

1. **オブジェクト エクスプローラー** で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。

2. **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。

3. **[履歴]** ページを選択し、 **[ジョブ履歴ログのサイズを制限する]** がオンになっていることを確認します。

4. **[ジョブ履歴ログの最大サイズ (行)]** ボックスで、ジョブ履歴ログに使用できる最大行数を入力します。

5. **[ジョブごとのジョブ履歴の最大行数]** ボックスで、1 つのジョブに使用できるジョブ履歴の最大行数を入力します。

**時間に基づいてジョブ履歴ログのサイズを変更するには:**

1. **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]のインスタンスに接続し、そのインスタンスを展開します。  

2. **[SQL Server エージェント]** を右クリックし、 **[プロパティ]** を選択します。

3. **[履歴]** ページを選択し、 **[エージェントの履歴を削除する]** を選択します。

4. 適切な **[日]** 、 **[週]** 、または **[月]** を選択します。
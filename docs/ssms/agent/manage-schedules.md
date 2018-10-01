---
title: '[スケジュールの管理] | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: dc219f1a5ec75d98d90168811630a39438a9bbd9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683637"
---
# <a name="manage-schedules"></a>[スケジュールの管理]
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database Managed Instance と SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ スケジュールのプロパティを表示および変更できます。  
  
## <a name="options"></a>[変数]  
**[利用可能なスケジュール]**  
このユーザーが利用可能なスケジュールの一覧を表示します。 ジョブの所有者とスケジュールの所有者は同じである必要があります。 したがって、この一覧には、このジョブの所有者によって所有されているスケジュールだけが表示されます。  
  
**名前**  
スケジュールの名前を表示します。  
  
**有効**  
スケジュールを有効にするには、このオプションを選択します。  
  
**[説明]**  
ジョブを実行するスケジュールの条件を説明します。  
  
**[スケジュール済みのジョブ]**  
スケジュールにアタッチされているジョブの番号を表示します。 番号をクリックすると、ジョブのプロパティが表示されます。  
  
**新規**  
新しいスケジュールを作成するには、このボタンをクリックします。  
  
**削除**  
選択されているスケジュールを削除するには、このボタンをクリックします。  
  
**プロパティ**  
選択されているスケジュールのプロパティを変更するには、このボタンをクリックします。  
  
## <a name="see-also"></a>参照  
[スケジュールの作成とジョブへのアタッチ](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
  

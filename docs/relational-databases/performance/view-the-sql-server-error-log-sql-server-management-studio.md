---
title: "SQL Server エラー ログの表示 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 09/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 7de82937a4bb622190da96b5668318304f641895
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="view-the-sql-server-error-log-sql-server-management-studio"></a>SQL Server エラー ログの表示 (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログには、トラブルシューティングに利用できるユーザー定義のイベントや特定のシステム イベントが含まれています。 

## <a name="view-the-logs"></a>ログの表示

1. SQL Server Management Studio で **[オブジェクト エクスプローラー]** を選択します。 **オブジェクト エクスプローラー**を開くには、F8 キーを押します。 または、上部メニューで **[表示]**、**[オブジェクト エクスプローラー]** の順に選択します。
    
    ![Object_Explorer](../../relational-databases/performance/media/object-explorer.png) 

2. **[オブジェクト エクスプローラー]**で、SQL Server のインスタンスに接続して、そのインスタンスを展開します。
  
3. **[管理]** セクションを探して開きます (表示するアクセス許可が必要です)。

4. **[SQL Server ログ]** を右クリックし、**[表示]**、**[SQL Server ログ]** の順に選択します。

    ![View_SQLServer_Log_SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5. **ログ ファイル ビューアー**でログの一覧が表示されます (少し時間がかかることがあります)。
  
  ## <a name="see-also"></a>参照
  詳細については、[MSSQLTips.com](https://www.mssqltips.com/) の参考になる投稿「[Identify location of the SQL Server Error Log file](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/)」(SQL Server エラー ログ ファイルの場所を探す) を参照してください。


---
title: SQL Server エラー ログの表示 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 09/29/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 38d99822b2d77e25259c793d350e4d329d4c0af7
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582216"
---
# <a name="view-the-sql-server-error-log-sql-server-management-studio"></a>SQL Server エラー ログの表示 (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログには、トラブルシューティングに利用できるユーザー定義のイベントや特定のシステム イベントが含まれています。 

## <a name="view-the-logs"></a>ログの表示

1. SQL Server Management Studio で **[オブジェクト エクスプローラー]** を選択します。 **オブジェクト エクスプローラー**を開くには、F8 キーを押します。 または、上部メニューで **[表示]** 、 **[オブジェクト エクスプローラー]** の順に選択します。
    
    ![Object_Explorer](../../relational-databases/performance/media/object-explorer.png) 

2. **[オブジェクト エクスプローラー]** で、SQL Server のインスタンスに接続して、そのインスタンスを展開します。
  
3. **[管理]** セクションを探して開きます (表示するアクセス許可が必要です)。

4. **[SQL Server ログ]** を右クリックし、 **[表示]** 、 **[SQL Server ログ]** の順に選択します。

    ![View_SQLServer_Log_SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5. **ログ ファイル ビューアー**でログの一覧が表示されます (少し時間がかかることがあります)。

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

  ## <a name="see-also"></a>参照
  詳細については、[MSSQLTips.com](https://www.mssqltips.com/) の参考になる投稿「[Identify location of the SQL Server Error Log file](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/)」(SQL Server エラー ログ ファイルの場所を探す) を参照してください。


---
title: プロジェクトの設定 (Azure SQL DB) (MySQLToSQL) |Microsoft ドキュメント
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8c06420a-533b-4de0-948d-a0c6b368c544
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 46dfaa1f7b35f87d13fc3a88fb00d6a26a1cf27f
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="project-settings-azure-sql-db-mysqltosql"></a>プロジェクトの設定 (Azure SQL DB) (MySQLToSQL)
SQL Azure のプロジェクト設定では、サフィックスを構成する、SQL Azure データベースに接続ダイアログで追加して、SQL Azure 接続でハートビート メカニズムを実装することもできます。  
  
SQL Azure ペインがで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   プロジェクトの設定 ダイアログ ボックスを使用すると、現在のプロジェクトの構成オプションを設定できます。 SQL Azure の設定にアクセスする、**ツール**メニューの [**プロジェクト設定**、] をクリックして**全般**クリックし、左側のウィンドウの下部にある**SQL Azure**です。  
  
-   プロジェクトの既定の設定 ダイアログ ボックスを使用すると、すべてのプロジェクトの構成オプションを設定できます。 SQL Azure の設定にアクセスする、**ツール**メニューの  **DefaultProject 設定**から SQL azure 移行プロジェクトの種類を選択**移行対象のバージョン**SQL Azure のウィンドウでの設定にアクセスするドロップダウン**全般**クリックし、左側のウィンドウの下部にある**SQL Azure**です。  
  
## <a name="options"></a>オプション  
  
## <a name="connectivity"></a>接続  
**ハートビートの間隔**  
  
SQL Azure 接続を維持するハートビート メカニズムを使用する時間間隔を指定 ' 分: 秒の形式です。  
  
**既定値**:' 4:45 '  
  
値を指定する必要がありますで am: ss の形式 (たとえば、' 4:45 'または' 0:50 ')。  
  
**SQL Azure サーバーのサフィックス**  
  
SQL Azure サーバーのサフィックスを指定します  
  
**既定値**: '..database.windows.net を付けて' です。  
  

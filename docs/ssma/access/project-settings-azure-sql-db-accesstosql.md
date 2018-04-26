---
title: プロジェクトの設定 (Azure SQL DB) (AccessToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-access
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
helpviewer_keywords:
- Project Settings dialog box, SQL Azure
- SQL Azure settings
ms.assetid: bbb8a204-d0e4-4f0b-9709-271feb1f136e
caps.latest.revision: 11
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b9034a699a604bfe70ea7c2fb52c7a8b6ee58cc4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="project-settings-azure-sql-db-accesstosql"></a>プロジェクトの設定 (Azure SQL DB) (AccessToSQL)
SQL Azure のプロジェクト設定では、サフィックスを構成する、SQL Azure データベースに接続ダイアログで追加して、SQL Azure 接続でハートビート メカニズムを実装することもできます。  
  
SQL Azure ペインがで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   プロジェクトの設定 ダイアログ ボックスを使用すると、現在のプロジェクトの構成オプションを設定できます。 SQL Azure の設定にアクセスする、**ツール**メニューの [**プロジェクト設定**、] をクリックして**全般**クリックし、左側のウィンドウの下部にある**SQL Azure**です。  
  
-   プロジェクトの既定の設定 ダイアログ ボックスを使用すると、すべてのプロジェクトの構成オプションを設定できます。 SQL Azure の設定にアクセスする、**ツール**メニューの [ **DefaultProject 設定**、"SQL azure"で、プロジェクトの種類を選択**移行対象のバージョン**SQL Azure] ウィンドウで、設定にアクセスするコンボ ボックスのをクリックして**全般**クリックし、左側のウィンドウの下部にある**SQL Azure**です。  
  
## <a name="options"></a>オプション  
  
## <a name="connectivity"></a>接続  
**ハートビートの間隔**  
  
SQL Azure 接続を維持するハートビート メカニズムを使用する時間間隔を指定 ' 分: 秒の形式です。  
  
**既定値**:' 4:45 '  
  
値を指定する必要がありますで am: ss の形式 (たとえば、' 4:45 'または' 0:50 ')。  
  
**SQL Azure サーバーのサフィックス**  
  
SQL Azure サーバーのサフィックスを指定します  
  
**既定値**: '..database.windows.net を付けて' です。  
  

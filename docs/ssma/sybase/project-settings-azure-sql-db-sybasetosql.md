---
title: プロジェクトの設定 (Azure SQL DB) (SybaseToSQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 57002374-0d4d-43c1-b4e9-cbec02355a9c
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 41c429bd09254580e705131988882402e227761c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="project-settings-azure-sql-db--sybasetosql"></a>プロジェクトの設定 (Azure SQL DB) (SybaseToSQL)
Azure SQL DB プロジェクト設定では、サフィックスを構成する、Azure SQL DB データベース、接続ダイアログで追加する Azure SQL DB の接続でハートビート メカニズムを実装することもできます。  
  
Azure SQL DB ペインがで使用できる、**プロジェクト設定**と**プロジェクト設定の既定の** ダイアログ ボックス。  
  
-   プロジェクトの設定 ダイアログ ボックスを使用すると、現在のプロジェクトの構成オプションを設定できます。 Azure SQL DB の設定にアクセスする、**ツール**メニューの [**プロジェクト設定**、] をクリックして**全般**クリックし、左側のウィンドウの下部にある**Azure SQL DB**です。  
  
-   プロジェクトの既定の設定 ダイアログ ボックスを使用すると、すべてのプロジェクトの構成オプションを設定できます。 Azure SQL DB の設定にアクセスする、**ツール**メニューの [ **DefaultProject 設定**、] をクリックして**全般**クリックし、左側のウィンドウの下部にある**Azure SQL DB**です。  
  
## <a name="connectivity"></a>接続  
**ハートビートの間隔**  
  
Azure SQL DB の接続を維持するハートビート メカニズムを使用する時間間隔を指定 ' 分: 秒の形式です。  
  
**既定値**:' 4:45 '  
  
値を指定する必要がありますで am: ss の形式 (たとえば、' 4:45 'または' 0:50 ')。  
  
**Azure SQL DB サーバーのサフィックス**  
  
Azure SQL DB server サフィックスを指定します  
  
**既定値**: '..database.windows.net を付けて' です。  
  

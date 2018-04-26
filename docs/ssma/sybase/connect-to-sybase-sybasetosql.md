---
title: Sybase (SybaseToSQL) への接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 524f95ef-10bd-497c-84ca-c06a0ae794fb
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8aad8b895c7a66dd31f537f6129598b05a8933a4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="connect-to-sybase-sybasetosql"></a>Sybase (SybaseToSQL) への接続します。
使用して、 **Sybase への接続**を移行する Sybase Adaptive Server Enterprise (ASE) インスタンスに接続する ダイアログ ボックス。  
  
このダイアログ ボックスにアクセスする、**ファイル**メニューの  **Sybase への接続**です。 以前接続した場合、コマンドは**sybase 再接続**です。  
  
## <a name="options"></a>オプション  
**プロバイダー**  
Sybase サーバーへの接続用のコンピューターにインストールされているプロバイダーのいずれかを選択します。  
  
**モード**  
どちらの標準または高度な接続モードを選択します。 標準モードでは、入力またはサーバー名、ポート、ユーザー名およびパスワードの値を選択します。 詳細設定モードでは、接続文字列を指定します。  
  
**サーバー名**  
入力するか、名前またはアダプティブ サーバーの IP アドレスを選択します。 既定のサーバー名は、コンピューター名と同じです。 標準モードのオプションです。  
  
**[サーバー ポート]**  
既定以外のポート ASE への接続を使用している場合は、ポート番号を入力します。 既定のポート番号は 5000 です。 標準モードのオプションです。  
  
**ユーザー名**  
ASE への接続に使用されるユーザー名を入力します。 標準モードのオプションです。  
  
**Password**  
ユーザー名に対応するパスワードを入力します。 標準モードのオプションです。  
  
**[接続文字列]**  
ASE を接続の完全な接続文字列を入力します。  
  
接続文字列は、パラメーターの名前と値のペアで構成されます。 パラメーターの名前は、使用されているプロバイダーによって異なります。  
  
**さまざまなプロバイダーの接続パラメーターは次のとおりです。**  
  
1.  接続パラメーター **OLE DB プロバイダー**  
  
    |設定|Sybase 12.5 パラメーター|Sybase 15 パラメーター|  
    |-----------|-------------------------|-----------------------|  
    |サーバー名|[サーバー名]|[サーバー]|  
    |ポート|サーバーのポート アドレス|ポート|  
    |ユーザー名|[ユーザー ID]|[ユーザー ID]|  
    |Password|Password|Password|  
    |プロバイダー|プロバイダー|プロバイダー|  
  
    Sybase ASE 12.5 の接続文字列の例のとおりです。  
  
    `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
    For Sybase ASE 15 では、接続文字列の例のとおりです。  
  
    `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=ASEOLEDB;Port=5000;`  
  
2.  接続パラメーター **ODBC プロバイダー**  
  
    |設定|Sybase 12.5/15 パラメーター|  
    |-----------|-----------------------------|  
    |ドライバー名|ドライバー●どらいば○|  
    |[サーバー名]|[サーバー]|  
    |[ユーザー名]|uid|  
    |Password|Pwd|  
    |[ポート番号]|ポート|  
  
    Sybase ASE 12.5 または 15 では、接続文字列の例のとおりです。  
  
    `driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
3.  接続パラメーター **ADO.NET プロバイダー**  
  
    |設定|Sybase 12.5/15 パラメーター|  
    |-----------|-----------------------------|  
    |[サーバー名]|[サーバー]|  
    |[ユーザー名]|uid|  
    |Password|Pwd|  
    |[ポート番号]|ポート|  
  
    ADO.NET プロバイダーの接続文字列の例は、次のとおりです。  
  
    `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
詳細については、ASE ドキュメントを参照してください。  
  
これは、高度なモード オプションです。  
  

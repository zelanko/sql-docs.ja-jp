---
title: サーバーの全体管理を実行している Web フロント エンド サーバーに ADOMD.NET をインストール |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2372180-e847-4cdb-b267-4befac3faf7e
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: ccedd48fcebab07eeb7b27821917b684d98a11d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077251"
---
# <a name="install-adomdnet-on-web-front-end-servers-running-central-administration"></a>サーバーの全体管理を実行している Web フロント エンド サーバーに ADOMD.NET をインストールします。
  Excel Services または PowerPivot for SharePoint がインストールされていない、サーバーの全体管理のトポロジを持つファームに PowerPivot for SharePoint をインストールするときに、PowerPivot 管理ダッシュボードの組み込みレポートへのフル アクセスが必要な場合は、Microsoft ADOMD.NET クライアント ライブラリをダウンロードしてインストールしてください。 ダッシュボードの一部のレポートでは、ADOMD.NET を使用して、ファームの PowerPivot クエリ処理およびサーバーの状態に関するレポート データを提供する内部データにアクセスします。  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010  
  
 SharePoint 2013 では、プロバイダーは SQL Server 機能パックに含まれています。 SpPowerPivot.msi をダウンロードする方法については、次を参照してください[Microsoft SQL Server 2014 Feature Pack。](http://www.microsoft.com/download/details.aspx?id=35577)  
  
### <a name="download-and-install-the-client-library"></a>クライアント ライブラリのダウンロードとインストール  
  
1.  [SQL Server 2014 Feature Pack ページ](http://go.microsoft.com/fwlink/?LinkID=296473)、Microsoft ADOMD.NET を検索します。  
  
2.  `SQL_AS_ADOMD.msi` インストール プログラムの x64 パッケージをダウンロードします。  
  
3.  .Msi を実行してライブラリをインストールします。  
  
4.  インストールの完了後、IIS をリセットします。 開き、管理コマンド プロンプトの種類**IISRESET**です。  
  
### <a name="verify-installation"></a>インストールの確認  
  
1.  Windows\Assembly に移動します。  
  
2.  Microsoft.AnalysisServices.AdomdClient を右クリックし **プロパティ**です。  
  
3.  **[バージョン]** をクリックします。  
  
4.  バージョンには 12.00 が含まれていることを確認します。\<ビルド番号 > および説明が microsoft.analysisservice.adomdclient になっています。  
  
## <a name="see-also"></a>参照  
 [PowerPivot 管理ダッシュボードと使用状況データ](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)  
  
  
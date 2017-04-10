---
title: "データ サイエンス クライアントのセットアップ | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "r-server"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 14
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# データ サイエンス クライアントのセットアップ
  **R Services (データベース内)** をインストールして、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のインスタンスを構成したら、リモート実行および配置のためにサーバーに接続できる R 開発環境をセットアップします。 
  
  クライアント環境には、Microsoft R Open に加えて、SQL Server 上での R の分散的実行をサポートする RevoScaleR パッケージを含める必要があります。  これらのパッケージは、いくつかの方法でインストールすることができます。
  
+ [Microsoft R クライアントをインストールする](http://aka.ms/rclient/download)
+ Microsoft R Open をインストールします。 Microsoft R Server を入手するには、SQL Server のセットアップまたはスタンドアロン インストーラーを使用します。 詳細については、[「スタンドアロン R Server の作成」](../../advanced-analytics/r-services/create-a-standalone-r-server.md) または [「R Server の概要」](https://msdnstage.redmond.corp.microsoft.com/en-us/microsoft-r/rserver?branch=r-server-nov16-dev) を参照してください。

 ScaleR パッケージを使用して SQL Server に接続する場合の Microsoft R Client の使い方の詳細については、「[ScaleR Getting Started](https://msdn.microsoft.com/microsoft-r/scaler-getting-started#)」 (ScaleR の概要) を参照してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続して R コードをリモートで実行する方法の詳細については、チュートリアル: [「データ サイエンスの詳細: RevoScaleR パッケージの使用」](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md) を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server R Services &#40;データベース内&#41; をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  
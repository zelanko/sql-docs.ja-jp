---
title: "データ サイエンス クライアントをセットアップする | Microsoft Docs"
ms.custom: 
ms.date: 02/10/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0661b2fcf9b23d3c81cb0d80f0424d87dbde7ef8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="set-up--a-data-science-client"></a>データ サイエンス クライアントのセットアップ
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] R Services (データベース内) **をインストールして、**のインスタンスを構成したら、リモート実行および配置のためにサーバーに接続できる R 開発環境をセットアップします。 
  
  この環境には ScaleR パッケージを含める必要があります。また必要に応じてクライアント開発環境を含めることができます。
  
 ## <a name="where-to-get-scaler"></a>ScaleR の入手先 
  
  クライアント環境には、Microsoft R Open に加えて、SQL Server 上での R の分散的実行をサポートする RevoScaleR パッケージを含める必要があります。  これらのパッケージは、いくつかの方法でインストールすることができます。
  
+ [Microsoft R クライアントをインストールする](http://aka.ms/rclient/download) 追加のセットアップ手順については、次を参照してください。[Get Started with Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-get-started) (Microsoft R Client の概要)
+ Microsoft R Server をインストールします。 Microsoft R Server を入手するには、SQL Server のセットアップまたは新しい Windows スタンドアロン インストーラーを使用します。 詳細については、[「Create a Standalone R Server (スタンドアロン R Server の作成)」](../../advanced-analytics/r-services/create-a-standalone-r-server.md)と[「Introduction to R Server (R Server の概要)」](https://msdn.microsoft.com/microsoft-r/rserver) をご覧ください。

R Server のライセンス契約を結んでいる場合は、R 処理スレッドとインメモリ データの制限を回避するために Microsoft R Server (スタンドアロン) を使用することをお勧めします。


## <a name="how-to-set-up-the-r-development-environment"></a>R 開発環境をセットアップする方法

Windows と互換性がある任意の R 開発環境を選択して使用できます。 

+ R Tools for Visual Studio は、Microsoft R Open との統合をサポートしています
+ RStudio は、人気がある無償の環境です  

インストールしたら、既定で Microsoft R Open ライブラリを使用するように環境を再構成する必要があります。再構成しないと ScaleR ライブラリにアクセスすることはできません。 詳細については、「[Getting Started with Microsoft R Client](http://msdn.microsoft.com/microsoft-r/r-client-get-started) (Microsoft R Client の概要)」を参照してください。
 
## <a name="more-resources"></a>その他のリソース
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続して R コードをリモートで実行する方法の詳細については、チュートリアル: [「データ サイエンスの詳細: RevoScaleR パッケージの使用」](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)を参照してください。  
 

SQL Server で Microsoft R Client と ScaleR パッケージを使用するには、[ScaleR の概要](https://msdn.microsoft.com/microsoft-r/scaler-getting-started#)に関する記事を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server R Services &#40;データベース内&#41; をセットアップする](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)  
  
  


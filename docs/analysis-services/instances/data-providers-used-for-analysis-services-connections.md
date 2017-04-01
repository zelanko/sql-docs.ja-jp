---
title: "Analysis Services 接続に使用するデータ プロバイダー | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
caps.latest.revision: 19
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 18
---
# Analysis Services 接続に使用するデータ プロバイダー
  Analysis Services では、サーバーとデータにアクセスするために 3 種類のデータ プロバイダーを用意しています。 Analysis Services に接続するすべてのアプリケーションでは、これらのプロバイダーのいずれかを使用します。 これらのプロバイダーのうち、ADOMD.NET および Analysis Services 管理オブジェクト (AMO) の 2 つは、マネージ データ プロバイダーです。 Analysis Services OLE DB Provider (MSOLAP DLL) は、ネイティブ データ プロバイダーです。  
  
 複数のバージョンの Analysis Services を運用している組織では、Analysis Services データに接続しているユーザー ワークステーションに、最新バージョンのデータ プロバイダーをインストールする必要が生じることがあります。 新しいバージョンの Analysis Services に接続するには、それと同じメジャー リリースのデータ プロバイダーが必要です。 たとえば、 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]に接続するには、各ワークステーションに、同じリリースのデータ プロバイダーが必要です。 Excel では、接続する必要のあるデータ プロバイダーがインストールされますが、提供されるプロバイダーは、使用している Analysis Services と比べて古いことがあります。  
  
 このトピックの内容は次のとおりです。  
  
 [サーバーのバージョンを確認する方法](#bkmk_ServVers)  
  
 [Analysis Services データ プロバイダーのバージョンを確認する方法](#bkmk_LibUpdate)  
  
 [新しいバージョンのデータ プロバイダーを入手する方法](#bkmk_downloadsite)  
  
 [Analysis Services OLE DB Provider](#bkmk_OLE)  
  
 [ADOMD.NET](#bkmk_ADOMD)  
  
 [AMO](#blkmk_AMO)  
  
##  <a name="bkmk_ServVers"></a> サーバーのバージョンを確認する方法  
 Analysis Services インスタンスのバージョンを把握しておくと、組織のワークステーションに新しいバージョンのデータ プロバイダーをインストールする必要があるかどうかを判断するのに役立ちます。  
  
-   SQL Server Management Studio で Analysis Services インスタンスに接続します。 バージョン情報は、 **[サーバーのプロパティ]** > **[全般]** > **[バージョン]**で確認できます。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の初回リリースのメジャー ビルド番号は 13.0.1601.5 です。  
  
  
##  <a name="bkmk_LibUpdate"></a> Analysis Services データ プロバイダーのバージョンを確認する方法  
 データ プロバイダーは、Excel など、日常的に Analysis Services データベースに接続するクライアント アプリケーションによって、Analysis Services と共にインストールされます。  
  
 Office 2010 では SQL Server 2008 のデータ プロバイダーがインストールされます。 Office 2013 では、SQL Server 2012 などのデータ プロバイダーがインストールされます。 複数のバージョンの Office または SQL Server を使用しており、必要な接続または機能を使用できない場合は、新しいバージョンのデータ プロバイダーのインストールが必要になることがあります。 各データ プロバイダーの複数のメジャー バージョンは、同じコンピューター上でサイド バイ サイドで実行できます。  
  
#### OLEDB プロバイダーのファイル バージョンを確認する  
  
1.  \Program Files\Microsoft Analysis Services\AS OLEDB\130 に移動します。  
  
2.  **msolap130で確認できます。dll** > **[プロパティ]** > **[詳細]**で確認できます。  
  
 この場所にファイルが見つからない場合、またはフォルダーのパスに "AS OLEDB\110" または "AS OLEDB\90" が含まれている場合は、使用しているプロバイダーが古いため、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]に接続するには、新しいバージョン (AS OLEDB\11) をインストールする必要があります。  
  
#### ADOMD.NET および AMO のファイル バージョンを確認する  
  
1.  C:\Windows\Assembly に移動します。  
  
2.  Microsoft.AnalysisServices.AdomdClient を右クリックし、 **[プロパティ]**をクリックします。 **[バージョン]**をクリックします。  
  
     AMO の場合は、Microsoft.AnalysisServices を右クリックします。  
  
##  <a name="bkmk_downloadsite"></a> 新しいバージョンのデータ プロバイダーを入手する方法  
 クライアント コンピューターにインストールされているバージョンは、データを提供しているサーバーのメジャー バージョンと一致する必要があります。 インストールされているサーバーが、ネットワーク内のワークステーションにインストールされているデータ プロバイダーより新しい場合は、新しいプロバイダーのインストールが必要になることがあります。  
  
#### ダウンロード サイトでデータ プロバイダーを探す  
  
1.  [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/p/?LinkID=296473)にアクセスします。  
  
2.  **[インストール方法]**を展開します。 ADOMD.NET、OLE DB Provider、および AMO が一覧にあります。 各ライブラリには、32 ビット版と 64 ビット版が用意されています。 64 ビット オペレーティング システムを実行しているサーバーと新しいワークステーションには、64 ビット版が必要になります。  
  
##  <a name="bkmk_OLE"></a> Analysis Services OLE DB Provider  
 Analysis Services OLE DB Provider は、Analysis Services データベース接続に使用されるネイティブ プロバイダーです。 MSOLAP は、接続要求をデータ プロバイダーに委任するために、ADOMD.NET および AMO の両方で間接的に使用します。 また、アプリケーション コードから OLE DB プロバイダーを直接呼び出すこともできます。この操作は、ソリューションの要件によってマネージ API を使用できない場合などに行います。  
  
 Analysis Services OLE DB Provider は、Analysis Services データベースにアクセスするためによく使用される SQL Server セットアップ、Excel などのアプリケーションによって自動的にインストールされます。 これは、ダウンロード センターからダウンロードして、手動でインストールすることもできます。 既定では、このプロバイダーは \Program Files\Microsoft Analysis Services フォルダーに置かれています。 このプロバイダーは、Analysis Services データへのアクセスに使用されるすべてのワークステーションにインストールする必要があります。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に付属する Analysis Services OLE DB プロバイダーのバージョンは、MSOLAP130.dll です。 最近のバージョンには、MSOLAP110.dll (SQL Server 2008 および 2008 R2) と MSOLAP90.dll (SQL Server 2005) があります。  
  
 OLE DB プロバイダーは多くの場合、接続文字列で指定されます。 Analysis Services 接続文字列では、別の用語体系を使用して OLE DB Provider を表します (MSOLAP.\<バージョン>.dll)。  
  
 Excel 2013 と同時にインストールされる最新の Analysis Services OLE DB Provider は、MSOLAP.5.dll です。 以前のバージョンの Excel を実行しているワークステーションでは、多くの場合、MSOLAP.4.dll や MSOLAP.3.dll など、以前のバージョンを使用しています。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] アドインなど、一部の Analysis Services 機能では、特定のバージョンの OLE DB Provider が必要です。 詳細については、「[接続文字列プロパティ (Analysis Services)](../../analysis-services/instances/connection-string-properties-analysis-services.md)」を参照してください。  
  
##  <a name="bkmk_ADOMD"></a> ADOMD.NET  
 ADOMD.NET は、Analysis Services データの照会に使用するマネージ データ プロバイダーです。 Excel では、特定の Analysis Services キューブに接続する場合に、ADOMD.NET を使用します。 Excel に表示される接続文字列は、ADOMD.NET 接続の接続文字列です。  
  
 SQL Server セットアップによりインストールされた ADOMD.NET を SQL Server クライアント アプリケーションが使用して、Analysis Services に接続します。 Excel からのデータ接続をサポートするために、Office にこのライブラリがインストールされます。 SQL Server に含まれる他のデータ プロバイダーと同様に、カスタム コードでこのプロバイダーを使用している場合は ADOMD.NET を再配布することができます。 新しいバージョンの AMO をダウンロードして手動でインストールすることもできます (このトピックの「 [Analysis Services データ プロバイダーのバージョンを確認する方法](#bkmk_LibUpdate) 」を参照)。  
  
 ファイルのバージョン情報を確認するには、グローバル アセンブリ キャッシュで ADOMD.NET を参照してください。グローバル アセンブリ キャッシュには `Microsoft.AnalysisServices.AdomdClient`という名前で記載されています。  
  
 データベースに接続する場合、3 つすべてのライブラリの接続文字列プロパティはほぼ同じです。 ADOMD.NET (<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>) 用に定義した接続文字列のほとんどは、AMO および Analysis Services OLE DB Provider にも使用できます。 詳細については、「[接続文字列プロパティ (Analysis Services)](../../analysis-services/instances/connection-string-properties-analysis-services.md)」を参照してください。  
  
 プログラムからの接続の詳細については、「[ADOMD.NET での接続の確立](../Topic/Establishing%20Connections%20in%20ADOMD.NET.md)」を参照してください。  
  
##  <a name="blkmk_AMO"></a> AMO  
 AMO は、サーバー管理およびデータ定義に使用するマネージ データ プロバイダーです。 たとえば、SQL Server Management Studio では AMO を使用して Analysis Services に接続します。  
  
 SQL Server セットアップによりインストールされた AMO を SQL Server クライアント アプリケーションが使用して、Analysis Services に接続します。 カスタム コードで AMO を使用する際に、AMO をダウンロードして手動でインストールすることもできます (このトピックの「 [Analysis Services データ プロバイダーのバージョンを確認する方法](#bkmk_LibUpdate) 」を参照)。 AMO は、グローバル アセンブリ キャッシュに `Microsoft.AnalysisServices` という名前で記載されています。  
  
 AMO を使用した接続は、通常、"data source=\<サーバー名>" で構成される最小の接続です。 接続が確立されたら、API を使用して、データベース コレクションおよび主要なオブジェクトを操作します。 SSDT と SSMS では、どちらも AMO を使用して、Analysis Services インスタンスに接続します。  
  
 プログラムによる接続の詳細については、「 [AMO 基本オブジェクトのプログラミング](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-fundamental-objects.md)」を参照してください。  
  
## 参照  
 [Analysis Services への接続](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  
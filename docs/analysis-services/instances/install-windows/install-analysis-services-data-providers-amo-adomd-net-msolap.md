---
title: "Analysis Services データ プロバイダー (AMO、ADOMD.NET、MSOLAP) のインストール |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7aedabc-6af9-4698-a7a4-98f894001476
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bd6aa812228cce132b4180a8537ba853f3ea92a2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="install-analysis-services-data-providers-amo-adomdnet-msolap"></a>Analysis Services データ プロバイダー (AMO、ADOMD.NET、MSOLAP) をインストールする
  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] は、ADOMD.Net、AMO、MSOLAP から成る Analysis Services データ プロバイダーのバージョンの更新です。  
  
 ほとんどのクエリ ベースのデータ アクセス シナリオでは、クライアント システムに既にインストールされている古いバージョンのデータ プロバイダーを使用して、SQL Server 2016 Analysis Services インスタンスのテーブル モデルおよび多次元モデルにアクセスすることができます。これには、SQL Server 2016 独自の機能を使用する表形式のモデルも含まれます。 一般的に、Excel、Reporting Services、Tableau などの、クエリを生成するクライアント アプリケーションが Analysis Services モデルにアクセスする場合に最新のデータ プロバイダーが必要とされることはありません。  
  
 モデリングと管理ツールは、少なくともデータ プロバイダーのバージョン要件に関してはその例外となります。 これらのツールでターゲット サーバー上のオブジェクトを操作するには、そのサーバー向けに特別に作成されたデータ プロバイダーが必要です。 幸い、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] とともに出荷されるツールには、サーバーの現在のバージョンに準拠するデータ プロバイダーが自動的に含まれています。  SQL Server Data Tools for Visual Studio 2015 のセットアップにより、SQL Server 2016 Analysis Services のデータ プロバイダーがインストールされます。 同様に、AMO と ADOMD.Net の両方を使用する SQL Server 2016 Management Studio では、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]を対象とする両方のデータ プロバイダーがインストールされます。  
  
 データ プロバイダーの手動インストールを呼び出しを行うシナリオには、Analysis Services 管理オブジェクト (AMO) を使用するカスタムのアプリケーションまたはスクリプトがあります。 このリリースには、サーバーやデータベースなどの主要なオブジェクトを、Microsoft.AnalysisServices.dll アセンブリの一部である新しい名前空間 (Microsoft.AnalysisServices.Core) に移動する、リファクタリングされた名前空間が導入されています。 AMO を使用するカスタムのコードまたはスクリプトがある場合は、コードを再コンパイルして、Analysis Services の SQL Server 2016 インスタンスに AMO を使用して直接接続するすべてのサーバーとクライアント ワークステーションで AMO を手動で更新する必要があります。  
  
## <a name="provider-list"></a>プロバイダーの一覧  
 次の表では、各プロバイダーについて説明します。  
  
||||  
|-|-|-|  
|プロバイダー|Filename|バージョン|  
|Analysis Services 管理オブジェクト (AMO)|Microsoft.AnalysisServices.dll|13.0.0.0|  
|Analysis Services コア|Microsoft.AnalysisServices.Core.dll|13.0.0.0|  
|Analysis Services (ADOMD.NET)|Microsoft.AnalysisServices.AdomdClient.dll|13.0.0.0|  
|OLE DB Provider for Analysis Services (MSOLAP)|MSOLAP130.dll|13.0.0.0|  
  
## <a name="download-and-install-data-provider"></a>データ プロバイダーのダウンロードとインストール  
  
1.  「 [Feature Pack download page for SQL Server 2016 (SQL Server 2016 の Feature Pack のダウンロード ページ)](http://go.microsoft.com/fwlink/?LinkID=398150)」に移動します。  
  
2.  **[ダウンロード]** をクリックして、個々 のコンポーネントのインストールを有効にします。  
  
3.  64 ビットのコンピューターでは、次のすべてまたは一部を選択します (または x86 と同等のものを選択します)。  
  
    -   ENU\x64\SQL_AS_ADOMD.msi  
  
    -   ENU\x64\SQL_AS_AMO.msi  
  
    -   ENU\x64\SQL_AS_OLEDB.msi  
  
4.  **[次へ]** をクリックして、ファイルをダウンロードします。  
  
5.  各プログラムを実行して、プロバイダーをインストールします。 ADO.MD と AMO のアセンブリは C:\Windows\assembly\GAC_MSIL にインストールされます。 Analysis Services OLE DB プロバイダーは C:\Program Files\Microsoft Analysis Services\AS OLEDB\130 にインストールされます。  
  
## <a name="verify-installation"></a>インストールの確認  
  
1.  ファイル エクスプ ローラーで C:\Windows\Assembly に移動します。  
  
2.  Microsoft.AnalysisServices を右クリックし、 **[プロパティ]**をクリックします。  
  
3.  **[バージョン]** をクリックして、最新のビルドが含まれていることを確認します。  
  
  

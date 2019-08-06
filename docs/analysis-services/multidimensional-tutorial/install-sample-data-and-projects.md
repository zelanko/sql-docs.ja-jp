---
title: Analysis Services サンプルデータおよびプロジェクトのインストール |Microsoft Docs
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2c89ee3edf9338c4f74b0738d930ee74dbec7244
ms.sourcegitcommit: bcc3b2c7474297aba17b7a63b17c103febdd0af9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/05/2019
ms.locfileid: "68794980"
---
# <a name="install-sample-data-and-multidimensional-projects"></a>サンプルデータと多次元プロジェクトのインストール 
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

この記事に記載されている手順とリンクを使用して、Analysis Services チュートリアルで使用するデータとプロジェクトファイルをインストールします。 
  
## <a name="step-1-install-prerequisites"></a>手順 1:必須コンポーネントのインストール 
このチュートリアルのレッスンでは、次のソフトウェアをインストール済みであることを前提としています。 すべての機能を1台のコンピューターにインストールすることができます。 これらの機能をインストールするには、SQL Server セットアップを実行して [機能の選択] ページから機能を選択します。  
  
-   SQL Server データベース エンジン  
  
-   SQL Server Analysis Services (SSAS) 
  
    Analysis Services は、次のエディションでのみ使用できます。評価、エンタープライズ、ビジネスインテリジェンス、標準。 多次元モデルは、Azure Analysis Services ではサポートされていません。
  
    既定では、Analysis Services 2016 以降が表形式のインスタンスとしてインストールされます。これは、インストールウィザードの [サーバーの構成] ページで [多次元サーバーモード] を選択することで上書きできます。
  
## <a name="step-2-download-and-install-developer-and-management-tools"></a>手順 2:開発者ツールと管理ツールをダウンロードしてインストールする
SQL Server Data Tools (SSDT) for Visual Studio は、他の SQL Server 機能とは別にダウンロードおよびインストールされます。 BI モデルとレポートの作成に使用するデザイナーとプロジェクトテンプレートは、visual Studio 2015 の SSDT、または Visual Studio 2017 の[Nuget パッケージ](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)に含まれています。  
  
[SQL Server Data Tools のダウンロード](http://go.microsoft.com/fwlink/?LinkID=827542)。   

SQL Server Management Studio (SSMS) は、他の SQL Server 機能とは別にダウンロードおよびインストールされます。  

[SQL Server Management Studio のダウンロード](../../ssms/download-sql-server-management-studio-ssms.md)  

チュートリアルを進めていくと、多次元データを参照することがあるので、必要に応じて Excel のインストールを検討してください。 Excel をインストールすると、構築するキューブに接続されているピボットテーブル フィールド リストを使用して Excel を起動する、" **Excel で分析** " 機能が有効になります。 データと対話するためのピボット レポートをすばやく作成できるので、Excel を使用してデータを参照することをお勧めします。  
  
また、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に組み込まれている MDX クエリ デザイナーを使用してデータを参照することもできます。 クエリ デザイナーでも同じデータが返されますが、データがフラットな行セットとして表示される点が異なります。  
  
## <a name="step-3-install-databases"></a>手順 3:データベースのインストール  
Analysis Services 多次元モデルでは、リレーショナル データベース管理システムからインポートしたトランザクション データを使用します。 このチュートリアルでは、次のリレーショナルデータベースをデータソースとして使用します。  
  
-   **AdventureWorksDW2012**以降-これはデータベースエンジンインスタンスで実行されるリレーショナルデータウェアハウスです。 このチュートリアルでは、構築してデプロイする Analysis Services データベースおよびプロジェクトで使用される元のデータを提供します。 このチュートリアルでは、AdventureWorksDW2012 を使用していることを前提としていますが、それ以降のバージョンでは機能します。
  
    このサンプルデータベースは、以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]使用できます。 一般に、データベースエンジンのバージョンと一致するサンプルデータベースのバージョンを使用する必要があります。
  
データベースをインストールするには、次の手順を実行します。  
  
1.  GitHub から[AdventureWorksDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)データベースのバックアップをダウンロードします。  
  
2.  バックアップファイルをローカル SQL Server データベースエンジンインスタンスのデータディレクトリにコピーします。
  
3.  Microsoft SQL Server Management Studio を起動し、データベース エンジン インスタンスに接続します。  
  
4.  データベースを復元します。  
  
## <a name="step-4-grant-database-permissions"></a>手順 4:データベースアクセス許可の付与  
サンプル プロジェクトでは、データがインポートまたは処理されるときのセキュリティ コンテキストを指定する、データ ソースの権限借用設定を使用します。 既定の権限借用設定では、データにアクセスするための Analysis Services サービス アカウントを指定します。 この既定の設定を使用するには、Analysis Services を実行するサービスアカウントに、 **AdventureWorksDW**データベースに対するデータリーダー権限があることを確認する必要があります。  
  
> [!NOTE]  
> 学習のために、既定のサービス アカウントによる権限借用オプションを使用し、SQL Server のサービス アカウントにデータ リーダー権限を与えることをお勧めします。 他の権限借用オプションも使用できますが、それらのすべてが処理操作に適しているわけではありません。 特に、現在のユーザーの資格情報を使用するためのオプションは、処理ではサポートされていません。  
  
1.  サービス アカウントを確認します。 アカウント情報は、SQL Server 構成マネージャーまたは [サービス] コンソール アプリケーションを使用して表示できます。 既定のアカウントを使用して Analysis Services を既定のインスタンスとしてインストールした場合、サービスは **NT Service\MSSQLServerOLAPService**として実行されています。  
  
2.  Management Studio で、データベース エンジン インスタンスに接続します。  
  
3.  [セキュリティ] フォルダーを展開し、[ログイン] を右クリックして **[新しいログイン]** をクリックします。  
  
4.  [全般] ページの [ログイン名] に、「 **NT Service\MSSQLServerOLAPService** 」(またはサービスを実行している任意のアカウント) を入力します。  
  
5.  **[ユーザー マッピング]** をクリックします。  
  
6.  **AdventureWorksDW**データベースの横にあるチェックボックスをオンにします。 ロールのメンバーシップには、 **db_datareader** および **public**が自動的に含まれます。 **[OK]** をクリックして、既定値をそのまま使用します。  
  
## <a name="step-5-install-projects"></a>手順 5:プロジェクトのインストール  

このチュートリアルには、完了した状態のプロジェクトと結果を比較したり、さらに後続のレッスンを開始したりできるように、サンプル プロジェクトが含まれています。  
  
1.  GitHub の Adventure Works for Analysis Services サンプルページから[adventure-works-multidimensional-tutorial-projects](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks-analysis-services)をダウンロードします。  
  
    チュートリアルのプロジェクトは、 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]以降で動作します。  
  
2.  .zip ファイルをルート ドライブ直下のフォルダー (たとえば、C:\Tutorial) に移動します。 この手順では、ダウンロードフォルダー内のファイルを解凍しようとした場合に発生することがある "パスが長すぎる" というエラーが軽減されます。  
  
3.  ファイルを右クリックし、 **[すべて展開]** をクリックして、サンプル プロジェクトを解凍します。 ファイルを抽出したら、レッスン1、2、3、5、6、7、8、9、10完了、レッスン4を開始します。 
  
4.  これらのファイルの読み取り専用権限を削除します。 親フォルダーを右クリックし、 **[プロパティ]** を選択し、 **[読み取り専用]** のチェックボックスをオフにします。 **[OK]** をクリックします。 このフォルダー、サブフォルダー、およびファイルへの変更を適用します。  

5.  使用しているレッスンに対応するソリューション (.sln) ファイルを開きます。 たとえば、Lesson 1 Complete というフォルダーで Analysis Services Tutorial.sln ファイルを開きます。  
  
6.  ソリューションを配置して、データベースのアクセス許可とサーバーの場所の情報が正しく設定されていることを確認します。  
  
    Analysis Services とデータベース エンジンが既定のインスタンス (MSSQLServer) としてインストールされ、すべてのソフトウェアが同じコンピューターで実行されている場合は、[ビルド] メニューの **[ソリューションの配置]** をクリックするとサンプル プロジェクトがビルドされ、ローカルの Analysis Services インスタンスに配置されます。 配置時には、ローカルデータベースエンジンインスタンスの**AdventureWorksDW**データベースからデータが処理 (またはインポート) されます。 データベースエンジンから取得したデータを含む新しい Analysis Services データベースが Analysis Services インスタンスに作成されます。  
  
    エラーが発生した場合は、データベース権限の設定に関する前の手順を確認してください。 さらに、サーバー名の変更も必要になる場合があります。 既定のサーバー名は localhost です。 サーバーがリモート コンピューター上で、または名前付きインスタンスとしてインストールされている場合、インストールに対して有効なサーバー名を使用するように既定値をオーバーライドする必要があります。 さらに、サーバーがリモート コンピューターにある場合は、サーバーへのアクセスを許可するように Windows ファイアウォールの構成が必要になることがあります。  
  
    データベース エンジンに接続するためのサーバー名は、ソリューション エクスプローラーに表示される多次元ソリューション (Adventure Works チュートリアル) の Data Source オブジェクトで指定されます。  
  
    Analysis Services に接続するためのサーバー名は、プロジェクトの [プロパティ ページ] の [配置] タブで指定され、ソリューション エクスプローラーにも表示されます。  
  
7.  SQL Server Management Studio で、Analysis Services に接続します。 **Analysis Services Tutorial** という名前のデータベースがサーバーで実行されていることを確認します。  
  
## <a name="next-step"></a>次の手順  
以上の操作で、チュートリアルを使用する準備が整いました。 開始方法の詳細については、「[多次元モデリング (Adventure Works チュートリアル)](multidimensional-modeling-adventure-works-tutorial.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
[Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)  
[SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
  
  

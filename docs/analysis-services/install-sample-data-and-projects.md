---
title: Analysis Services のサンプル データおよびプロジェクトのインストール |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df7311aad9c356376fffafc8a4882af8e29e746b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62659241"
---
# <a name="install-sample-data-and-multidimensional-projects"></a>サンプル データおよび多次元プロジェクトをインストールします。 
[!INCLUDE[ssas-appliesto-sqlas-all](../includes/ssas-appliesto-sqlas-all.md)]

Analysis Services のチュートリアルで使用されるデータとプロジェクト ファイルをインストールするのに手順については、この記事に記載のリンクを使用します。 
  
## <a name="step-1-install-prerequisites"></a>手順 1:必須コンポーネントのインストール 
このチュートリアルのレッスンでは、次のソフトウェアをインストール済みであることを前提としています。 すべての機能は、1 台のコンピューターにインストールできます。 これらの機能をインストールするには、SQL Server セットアップを実行して [機能の選択] ページから機能を選択します。  
  
-   SQL Server データベース エンジン  
  
-   SQL Server Analysis Services (SSAS) 
  
    Analysis Services は、各エディションでのみ入手できます。Evaluation、Enterprise、Business Intelligence、Standard。 多次元モデルでは、Azure Analysis Services でサポートされていません。
  
    既定では、Analysis Services 2016 以降がインストール ウィザードの構成 ページで、サーバーの多次元サーバー モードを選択してオーバーライドできますが、表形式インスタンスとしてインストールされます。
  
## <a name="step-2-download-and-install-developer-and-management-tools"></a>手順 2:ダウンロードして開発および管理ツールのインストール
Visual Studio の SQL Server Data Tools (SSDT) がダウンロードされ、その他の SQL Server の機能から個別にインストールします。 Visual Studio 2015 またはとしてデザイナーおよび BI モデルとレポートを作成するためのプロジェクト テンプレートが SSDT に含まれる[Nuget パッケージの](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)for Visual Studio 2017。  
  
[SQL Server Data Tools のダウンロード](http://go.microsoft.com/fwlink/?LinkID=827542)。   

SQL Server Management Studio (SSMS) はダウンロードして、その他の SQL Server の機能から個別にインストールします。  

[SQL Server Management Studio のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)  

チュートリアルを進めていくと、多次元データを参照することがあるので、必要に応じて Excel のインストールを検討してください。 Excel をインストールすると、構築するキューブに接続されているピボットテーブル フィールド リストを使用して Excel を起動する、" **Excel で分析** " 機能が有効になります。 データと対話するためのピボット レポートをすばやく作成できるので、Excel を使用してデータを参照することをお勧めします。  
  
また、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に組み込まれている MDX クエリ デザイナーを使用してデータを参照することもできます。 クエリ デザイナーでも同じデータが返されますが、データがフラットな行セットとして表示される点が異なります。  
  
## <a name="step-3-install-databases"></a>手順 3:データベースをインストールします。  
Analysis Services 多次元モデルでは、リレーショナル データベース管理システムからインポートしたトランザクション データを使用します。 このチュートリアルの目的で、次のリレーショナル データベースを使用するデータ ソースとして。  
  
-   **AdventureWorksDW2012 以降**-これは、データベース エンジンのインスタンスで実行されているリレーショナル データ ウェアハウスです。 Analysis Services データベースとプロジェクトをビルドして、チュートリアル全体での展開で使用される元のデータを提供します。 このチュートリアルには、AdventureWorksDW2012 を使用して、ただし、以降のバージョンは機能が前提とします。
  
    このサンプル データベースを使用する[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降。 一般的なデータベース エンジンのバージョンに一致するサンプル データベースのバージョンを使用する必要があります。
  
データベースをインストールするには、次の操作を行います。  
  
1.  ダウンロード、 [AdventureWorkDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) GitHub からのデータベースのバックアップ。  
  
2.  バックアップ ファイルをローカルの SQL Server データベース エンジン インスタンスのデータ ディレクトリにコピーします。
  
3.  Microsoft SQL Server Management Studio を起動し、データベース エンジン インスタンスに接続します。  
  
4.  データベースを復元します。  
  
## <a name="step-4-grant-database-permissions"></a>手順 4:データベースのアクセス許可の付与  
サンプル プロジェクトでは、データがインポートまたは処理されるときのセキュリティ コンテキストを指定する、データ ソースの権限借用設定を使用します。 既定の権限借用設定では、データにアクセスするための Analysis Services サービス アカウントを指定します。 この既定の設定を使用する Analysis Services を実行するサービス アカウントにあるデータ リーダー権限を確認する必要があります、 **AdventureWorksDW**データベース。  
  
> [!NOTE]  
> 学習のために、既定のサービス アカウントによる権限借用オプションを使用し、SQL Server のサービス アカウントにデータ リーダー権限を与えることをお勧めします。 他の権限借用オプションも使用できますが、それらのすべてが処理操作に適しているわけではありません。 特に、現在のユーザーの資格情報を使用するためのオプションは、処理ではサポートされていません。  
  
1.  サービス アカウントを確認します。 アカウント情報は、SQL Server 構成マネージャーまたは [サービス] コンソール アプリケーションを使用して表示できます。 既定のアカウントを使用して Analysis Services を既定のインスタンスとしてインストールした場合、サービスは **NT Service\MSSQLServerOLAPService**として実行されています。  
  
2.  Management Studio で、データベース エンジン インスタンスに接続します。  
  
3.  [セキュリティ] フォルダーを展開し、[ログイン] を右クリックして **[新しいログイン]** をクリックします。  
  
4.  [全般] ページの [ログイン名] に、「 **NT Service\MSSQLServerOLAPService** 」(またはサービスを実行している任意のアカウント) を入力します。  
  
5.  **[ユーザー マッピング]** をクリックします。  
  
6.  次のチェック ボックスをオン、 **AdventureWorksDW**データベース。 ロールのメンバーシップには、 **db_datareader** および **public**が自動的に含まれます。 **[OK]** をクリックして、既定値をそのまま使用します。  
  
## <a name="step-5-install-projects"></a>手順 5:プロジェクトをインストールします。  

このチュートリアルには、完了した状態のプロジェクトと結果を比較したり、さらに後続のレッスンを開始したりできるように、サンプル プロジェクトが含まれています。  
  
1.  ダウンロード、 [adventure-機能-マルチ ディメンション-チュートリアル-projects.zip](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks-analysis-services) GitHub のサンプル ページを Analysis Services 用 Adventure Works から。  
  
    チュートリアルのプロジェクトの作業の[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]以降。  
  
2.  .zip ファイルをルート ドライブ直下のフォルダー (たとえば、C:\Tutorial) に移動します。 この手順では、ダウンロード フォルダーにファイルを解凍しようとした場合にも発生する「パスが長すぎます」エラーを軽減します。  
  
3.  ファイルを右クリックし、 **[すべて展開]** をクリックして、サンプル プロジェクトを解凍します。 後のファイルを抽出するには、レッスン 1、2、3、5、6、7、8、9、フォルダーがあります 10 完了と Lesson 4 Start です。 
  
4.  これらのファイルの読み取り専用権限を削除します。 親フォルダーを右クリックして**プロパティ**のチェック ボックスをオフ**読み取り専用**します。 **[OK]** をクリックします。 このフォルダー、サブフォルダー、およびファイルへの変更を適用します。  

5.  レッスンでは対応するソリューション (.sln) ファイルを開きます。 たとえば、Lesson 1 Complete というフォルダーで Analysis Services Tutorial.sln ファイルを開きます。  
  
6.  データベース権限およびサーバーの場所の情報が正しく設定を確認するソリューションを配置します。  
  
    Analysis Services とデータベース エンジンが既定のインスタンス (MSSQLServer) としてインストールされ、すべてのソフトウェアが同じコンピューターで実行されている場合は、[ビルド] メニューの **[ソリューションの配置]** をクリックするとサンプル プロジェクトがビルドされ、ローカルの Analysis Services インスタンスに配置されます。 デプロイ時に、データが処理 (またはインポート) から、 **AdventureWorksDW**データベース エンジンのローカル インスタンス上のデータベース。 新しい Analysis Services データベースは、データベース エンジンから取得されたデータを含む Analysis Services インスタンスに作成されます。  
  
    エラーが発生した場合は、データベース権限の設定に関する前の手順を確認してください。 さらに、サーバー名の変更も必要になる場合があります。 既定のサーバー名は localhost です。 サーバーがリモート コンピューター上で、または名前付きインスタンスとしてインストールされている場合、インストールに対して有効なサーバー名を使用するように既定値をオーバーライドする必要があります。 さらに、サーバーがリモート コンピューターにある場合は、サーバーへのアクセスを許可するように Windows ファイアウォールの構成が必要になることがあります。  
  
    データベース エンジンに接続するためのサーバー名は、ソリューション エクスプローラーに表示される多次元ソリューション (Adventure Works チュートリアル) の Data Source オブジェクトで指定されます。  
  
    Analysis Services に接続するためのサーバー名は、プロジェクトの [プロパティ ページ] の [配置] タブで指定され、ソリューション エクスプローラーにも表示されます。  
  
7.  SQL Server Management Studio で、Analysis Services に接続します。 **Analysis Services Tutorial** という名前のデータベースがサーバーで実行されていることを確認します。  
  
## <a name="next-step"></a>次の手順  
以上の操作で、チュートリアルを使用する準備が整いました。 開始方法の詳細については、「[多次元モデリング (Adventure Works チュートリアル)](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)  
[SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
  
  
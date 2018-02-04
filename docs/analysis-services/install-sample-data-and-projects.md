---
title: "サンプル データとプロジェクトのインストール |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: fc475b25-cbb2-408a-901f-9299299538c5
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: af6002ed27aabacf1b9e9a08cf3e659559daf5f5
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="install-sample-data-and-multidimensional-projects"></a>サンプル データおよび多次元プロジェクトをインストールします。 
[!INCLUDE[ssas-appliesto-sqlas-all](../includes/ssas-appliesto-sqlas-all.md)]

Analysis Services のチュートリアルで使用されるデータとプロジェクト ファイルをインストールするのに手順とここで指定されたリンクを使用します。  多次元のチュートリアルを実行している場合のみ、このチュートリアルで作成したものと完全に完成したプロジェクトを比較する場合は、サンプル プロジェクトをインストールする必要があります。
  
## <a name="step-1-install-sql-server-software"></a>手順 1: SQL Server ソフトウェアのインストール  
このチュートリアルのレッスンでは、次のソフトウェアをインストール済みであることを前提としています。 すべての機能は、1 台のコンピューターにインストールできます。 これらの機能をインストールするには、SQL Server セットアップを実行して [機能の選択] ページから機能を選択します。  
  
-   データベース エンジン  
  
-   Analysis Services  
  
    Analysis Services は、Evaluation、Enterprise、Business Intelligence、Standard の各エディションでのみ使用できます。  
  
    既定では、インストール ウィザードの構成 ページをサーバーで多次元サーバー モードを選択するをオーバーライドすることができます、表形式のインスタンスとして Analysis Services 2016 以降がインストールされています。 両方のサーバー モードを実行する場合は、同じコンピューター上の SQL Server セットアップを再実行して、他方のモードで Analysis Services の第 2 のインスタンスをインストールします。  
  
-   [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)  
  
チュートリアルを進めていくと、多次元データを参照することがあるので、必要に応じて Excel のインストールを検討してください。 Excel をインストールすると、構築するキューブに接続されているピボットテーブル フィールド リストを使用して Excel を起動する、" **Excel で分析** " 機能が有効になります。 データと対話するためのピボット レポートをすばやく作成できるので、Excel を使用してデータを参照することをお勧めします。  
  
また、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に組み込まれている MDX クエリ デザイナーを使用してデータを参照することもできます。 クエリ デザイナーでも同じデータが返されますが、データがフラットな行セットとして表示される点が異なります。  
  
## <a name="step-2-download-sql-server-data-tools-for-visual-studio"></a>手順 2: Visual Studio 用の SQL Server Data Tools をダウンロードします。 
このリリースでは、SQL Server Data Tools を他の SQL Server 機能とは別にダウンロードしてインストールします。 デザイナーおよび BI モデルとレポートを作成するためのプロジェクト テンプレートが含まれる ssdt for Visual Studio 2015 かとして[Nuget パッケージの](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)Visual Studio 2017 用です。  
  
-   [SQL Server Data Tools のダウンロード](http://go.microsoft.com/fwlink/?LinkID=827542)。 ファイルはダウンロード フォルダーに保存されます。 セットアップを実行してツールをインストールします。  
  
## <a name="step-3-install-databases"></a>手順 3. データベースのインストール  
Analysis Services 多次元モデルでは、リレーショナル データベース管理システムからインポートしたトランザクション データを使用します。 このチュートリアルでは、次のリレーショナル データベースをデータ ソースとして使用します。  
  
-   **2012 以降の AdventureWorksDW** – これは、データベース エンジンのインスタンス上で実行されるリレーショナル データ ウェアハウスです。 このチュートリアルで構築して配置する Analysis Services データベースおよびプロジェクトで使用される元のデータを提供します。  
  
    このサンプル データベースを使用する[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]およびそれ以降。 一般的なデータベース エンジンのバージョンと一致するサンプル データベースのバージョンを使用する必要があります。
  
データベースをインストールするには、次の操作を行います。  
  
1.  ダウンロード、 [AdventureWorkDW](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) GitHub からのデータベースのバックアップ。  
  
2.  バックアップ ファイルをローカルの SQL Server データベース エンジン インスタンスのデータ ディレクトリにコピーします。
  
3.  Microsoft SQL Server Management Studio を起動し、データベース エンジン インスタンスに接続します。  
  
4.  データベースを復元します。  
  
## <a name="step-4-grant-database-permissions"></a>手順 4. データベース権限の許可  
サンプル プロジェクトでは、データがインポートまたは処理されるときのセキュリティ コンテキストを指定する、データ ソースの権限借用設定を使用します。 既定の権限借用設定では、データにアクセスするための Analysis Services サービス アカウントを指定します。 この既定の設定を使用する Analysis Services を実行するサービス アカウントにあるデータ リーダー権限を確認する必要があります、 **AdventureWorksDW2014**データベース。  
  
> [!NOTE]  
> 学習のために、既定のサービス アカウントによる権限借用オプションを使用し、SQL Server のサービス アカウントにデータ リーダー権限を与えることをお勧めします。 他の権限借用オプションも使用できますが、それらのすべてが処理操作に適しているわけではありません。 特に、現在のユーザーの資格情報を使用するためのオプションは、処理ではサポートされていません。  
  
1.  サービス アカウントを確認します。 アカウント情報は、SQL Server 構成マネージャーまたは [サービス] コンソール アプリケーションを使用して表示できます。 既定のアカウントを使用して Analysis Services を既定のインスタンスとしてインストールした場合、サービスは **NT Service\MSSQLServerOLAPService**として実行されています。  
  
2.  Management Studio で、データベース エンジン インスタンスに接続します。  
  
3.  [セキュリティ] フォルダーを展開し、[ログイン] を右クリックして **[新しいログイン]**をクリックします。  
  
4.  [全般] ページの [ログイン名] に、「 **NT Service\MSSQLServerOLAPService** 」(またはサービスを実行している任意のアカウント) を入力します。  
  
5.  **[ユーザー マッピング]**をクリックします。  
  
6.  次のチェック ボックスをオン、 **AdventureWorksDW2014**データベース。 ロールのメンバーシップには、 **db_datareader** および **public**が自動的に含まれます。 **[OK]** をクリックして、既定値をそのまま使用します。  
  
## <a name="step-5-install-projects"></a>手順 5. プロジェクトのインストール  

サンプル プロジェクトでは、多次元モデリング チュートリアルで作成すると比較するために必要なのみです。 これらは、チュートリアルを完了する必要はありません。
  
1.  ダウンロード、 [adventure-works-多次元のモデルの project.zip](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks-analysis-services) GitHub 上の Analysis Services サンプル ページの Adventure Works からです。  
  
    このプロジェクトは、SSAS 2014 以降では動作します。  
  
2.  .zip ファイルをルート ドライブ直下のフォルダー (たとえば、C:\Tutorial) に移動します。 この手順により、ダウンロード フォルダーでファイルを解凍する場合に発生することがある "パスが長すぎる" という内容のエラーを回避できます。  
  
3.  ファイルを右クリックし、 **[すべて展開]**をクリックして、サンプル プロジェクトを解凍します。 
  
4.  これらのファイルの読み取り専用権限を削除します。 親フォルダーを右クリックし、選択**プロパティ**のチェック ボックスをオフ**読み取り専用**です。 **[OK]**をクリックします。 このフォルダー、サブフォルダー、およびファイルへの変更を適用します。  

5.  ソリューション (.sln) ファイルを開く[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]です。  
  
6.  ソリューションを配置して、データベース権限およびサーバーの場所の情報が正しく設定されていることを確認します。  
  
    Analysis Services とデータベース エンジンが既定のインスタンス (MSSQLServer) としてインストールされ、すべてのソフトウェアが同じコンピューターで実行されている場合は、[ビルド] メニューの **[ソリューションの配置]** をクリックするとサンプル プロジェクトがビルドされ、ローカルの Analysis Services インスタンスに配置されます。 展開時に、データすると処理 (またはインポート) から、 **AdventureWorksDW**データベース エンジンのローカル インスタンス上のデータベースです。 データベース エンジンから取得されたデータを含む Analysis Services インスタンス上で新しい Analysis Services データベースが作成されます。  
  
    エラーが発生した場合は、データベース権限の設定に関する前の手順を確認してください。 さらに、サーバー名の変更も必要になる場合があります。 既定のサーバー名は localhost です。 サーバーがリモート コンピューター上で、または名前付きインスタンスとしてインストールされている場合、インストールに対して有効なサーバー名を使用するように既定値をオーバーライドする必要があります。 さらに、サーバーがリモート コンピューターにある場合は、サーバーへのアクセスを許可するように Windows ファイアウォールの構成が必要になることがあります。  
  
    データベース エンジンに接続するためのサーバー名は、ソリューション エクスプローラーに表示される多次元ソリューション (Adventure Works チュートリアル) の Data Source オブジェクトで指定されます。  
  
    Analysis Services に接続するためのサーバー名は、プロジェクトの [プロパティ ページ] の [配置] タブで指定され、ソリューション エクスプローラーにも表示されます。  
  
7.  SQL Server Management Studio で、Analysis Services に接続します。 **Analysis Services Tutorial** という名前のデータベースがサーバーで実行されていることを確認します。  
  
## <a name="next-step"></a>次の手順  
以上の操作で、チュートリアルを使用する準備が整いました。 開始方法の詳細については、「[多次元モデリング (Adventure Works チュートリアル)](../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)  
[SQL Server のアクセスを許可するための Windows ファイアウォールの構成](../sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md)  
  
  
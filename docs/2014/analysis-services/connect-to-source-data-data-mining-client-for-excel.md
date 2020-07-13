---
title: ソースデータへの接続 (Excel 用のデータマイニングクライアント) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- connections
ms.assetid: 548672ce-e403-4aca-b67a-c2c797f053dd
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8c90031f3c1191e99ff6274f6198d513225f0927
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527028"
---
# <a name="connect-to-source-data-data-mining-client-for-excel"></a>ソース データへの接続 (Excel 用データ マイニング クライアント)
  このトピックでは、データ マイニング モデルの保存、および、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] に保存されている外部データへのアクセスに使用する接続の作成方法と使用方法について説明します。  
  
 **データマイニング接続。** アドインの開始時に作成する最初の接続は、アルゴリズムへのアクセス、データ分析、マイニング構造およびモデルの格納に使用されます。  
  
 アドインでモデリング ツールと視覚化ツールを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスへの接続が必要です。なぜなら、アドインは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の高度なアルゴリズムとデータ構造に依存しているためです。  
  
 **外部データ ソースへの接続。** モデルの作成時や結果の保存時に外部データへの接続を作成することもできます。 たとえば、あるサーバー上にデータ マイニング モデルを作成してから、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の別のインスタンス、Excel データ テーブル、または [!INCLUDE[msCoName](../includes/msconame-md.md)] Access のような外部データ ソースに保存されているデータを使用して、作成したデータ マイニング モデルに基づく予測クエリを実行できます。 新しいデータ ソースにアクセスするたびに、ダイアログ ボックスを使用して接続を作成するように求められます。  
  
##  <a name="prerequisites"></a><a name="bkmk_prereq2"></a> 前提条件  
 このバージョンのアドインを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスが SQL Server 2012 であることが必要です。 以前のバージョンの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] に接続する場合、それぞれのバージョンのアドインを使用できます。 SQL Server 2005、SQL Server 2008、SQL Server 2008 R2 をサポートするアドインのバージョンがあります。  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに接続するには、データベース サーバーにアクセスする権限が必要です。 また、データ マイニング セッションが有効にされていて、サーバーに格納されているデータベース オブジェクトに対する読み取り権限または読み取り/書き込み権限を有している必要があります。  
  
##  <a name="creating-data-mining-server-connections"></a><a name="bkmk_connect"></a>データマイニングサーバー接続の作成  
 Excel 用のデータマイニングクライアントおよび Excel 用のテーブル分析ツールの [**接続**] グループには、のインスタンスへの接続を管理するためのツールが用意されて [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] います。  
  
-   アドインをインストールするときに接続を作成できます。後で接続を追加することもできます。  
  
-   モデルの作成中やクエリの実行中でない限り、複数の接続を作成して、接続を随時変更できます。  
  
     データ マイニング モデルの処理中に接続を変更したり閉じたりしないでください。 データ マイニング モデルのデータが失われたり、モデルが使用できなくなる場合があります。  
  
-   有効にできるのは一度に 1 つの接続のみです。  
  
### <a name="connections-in-the-excel-add-ins"></a>Excel アドインでの接続  
 Excel 用のデータマイニングクライアントおよび Excel 用のテーブル分析ツールの [**接続**] グループでは、のインスタンスへの接続を管理し [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。  
  
##### <a name="create-a-new-server-connection-in-the-excel-add-ins"></a>Excel アドインで新しいサーバー接続を作成する  
  
1.  [**分析**] または [**データマイニング**] リボンの [**接続**] ボタンをクリックします。  
  
    > [!NOTE]  
    >  ボタンに表示されるテキストは、接続が存在するかどうかによって異なります。 ワークシートで接続が確立されていない場合、ボタンには "." というテキストが表示され \<No connection> ます。ブックで以前に接続が作成されていた場合は、その接続の名前がボタンに表示されます。  
  
2.  [ **Analysis Services 接続**] ダイアログボックスで、[**新規**] をクリックします。  
  
3.  [**新しい Analysis Services 接続**] ダイアログボックスで、サーバーの名前を入力します。  
  
4.  認証方法を指定します。  
  
5.  [**カタログ名**] ドロップダウンリストからデータベースを選択します。 インスタンスにデータベースが存在しない場合は、[ **(既定)**] を選択します。  
  
6.  接続のフレンドリ名を入力します。  
  
7.  [**接続テスト**] をクリックして、サーバーとデータベースが使用可能であることを確認します。  
  
8.  **[OK]** をクリックし、**[閉じる]** をクリックします。  
  
### <a name="connections-using-a-web-service"></a>Web サービスを使用した接続  
 仮想化アーキテクチャを使用してキューブとデータの参照を有効にする場合は [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Web サービスを使用してサーバーへの接続を構成することもできます。 Web ベース クライアントの定義方法については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックを参照してください。  
  
 Web サービス用に構成されたサーバーにアクセスする場合、最初に接続を作成するときに接続の種類を指定できます。  
  
##### <a name="create-an-http-connection-to-analysis-services"></a>Analysis Services への HTTP 接続を作成する  
  
1.  [**新しい Analysis Services 接続**] ダイアログボックスを開きます。  
  
2.  サーバー名として、http:// の後に続けて、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーに割り当てられた URL を入力します。  
  
3.  Web サービスへのアクセスに必要なユーザー名およびパスワードを入力します。  
  
### <a name="connections-in-the-visio-add-in"></a>Visio アドインでの接続  
 Excel とは異なり、Visio にツール リボンはありません。また、接続の作成または監視専用のボタンもありません。 代わりに、データ マイニング図形を初めて選択して、Visio ページに配置したときに、データ接続が作成されます。 ウィザードの指示に従って、図形のモデルを選択し、その他のオプションを設定します。  
  
 Excel で [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソースへの接続を以前に使用したことがある場合は、その接続が使用可能なデータ ソースとして表示されて、選択することができます。  
  
##### <a name="create-a-connection-for-a-visio-shape"></a>Visio 図形の接続を作成する  
  
1.  データ マイニング テンプレートを開いて、データ マイニング図形を 1 つ選択します。  
  
2.  空のページに図形をドラッグ アンド ドロップします。  
  
3.  [**データソースの選択**] ダイアログボックスで、一覧からデータソースを選択するか、[**新規作成**] をクリックします。  
  
4.  [**新規**] を選択した場合は、前に説明した手順に従って、サーバーとカタログ名を指定するか、Web サービス経由で接続します。  
  
##  <a name="changing-connections"></a><a name="bkmk_change"></a>接続の変更  
 同じワークシート内に複数の接続を作成できますが、一度にアクティブにできるのは 1 つの接続のみです。 現在の接続の名前が [**接続**] ボタンに表示されます。  
  
 Excel 用のデータマイニングクライアントでは、[**トレース**] をクリックし、[**現在の接続**] をクリックして、現在の接続の接続文字列と状態を確認することもできます。  
  
#### <a name="use-a-different-server-connection"></a>別のサーバー接続を使用する  
  
1.  [**接続**] をクリックします。  
  
2.  [ **Analysis Services 接続**] ウィンドウで、[**その他の**接続] ボックスの一覧から接続を選択し、[**最新の設定**] をクリックします。  
  
3.  [**接続テスト**] をクリックして、接続が使用可能であることを確認します。  
  
 マイニング モデルの処理が完了すると、その結果はローカルに保存されます。あるサーバーへの接続を閉じて、別のサーバーに接続しても影響を受けることはありません。 ただし、データ マイニング モデルの処理中に接続を変更したり、接続が切断されたりしないように注意してください。データが破損する可能性があります。  
  
#### <a name="modify-an-existing-server-connection"></a>既存のサーバー接続を変更する  
  
1.  既存の接続は変更できません。別のデータベースまたは別のサーバーに接続する場合は、新しい接続を作成する必要があります。  
  
2.  接続文字列を変更してクエリ タイムアウトの値を増やしたり、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに特有のその他のパラメーターを追加する必要がある場合は、接続文字列が格納されている .dmc ファイルを編集するという方法もあります。  
  
     \<drive:>\ ユーザー \\<myusername \> \AppData\Local\Microsoft\Data マイニングアドイン  
  
##  <a name="connecting-to-external-data-sources"></a><a name="bkmk_extconnections"></a>外部データソースへの接続  
 [**分析**] リボンのツールは Excel のデータと排他的に機能しますが、[**データマイニング**] リボンのツールを使用すると、外部データソースに直接接続して、モデルの入力またはサンプリングとして使用することができます。  
  
 これらのアドインにある以下のツールはデータ マイニング用外部データの使用をサポートしています。  
  
-   [データマイニングアドイン SQL Server &#40;サンプルデータ&#41;](sample-data-sql-server-data-mining-add-ins.md)  
  
-   [分類ウィザード &#40;Excel 用データマイニングアドイン&#41;](classify-wizard-data-mining-add-ins-for-excel.md)  
  
-   [推定ウィザード &#40;Excel 用データマイニングアドイン&#41;](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
-   [クラスターウィザード &#40;Excel 用データマイニングアドイン&#41;](cluster-wizard-data-mining-add-ins-for-excel.md)  
  
-   [予測ウィザード &#40;Excel 用データマイニングアドイン&#41;](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
-   [SQL Server データマイニングアドイン &#40;マイニング構造の作成&#41;](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
-   [精度チャート &#40;SQL Server データマイニングアドイン&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
-   [利益チャート &#40;SQL Server データマイニングアドイン&#41;](profit-chart-sql-server-data-mining-add-ins.md)  
  
-   [分類マトリックス &#40;SQL Server データマイニングアドイン&#41;](classification-matrix-sql-server-data-mining-add-ins.md)  
  
### <a name="using-analysis-services-as-a-data-source"></a>Analysis Services のデータ ソースとしての使用  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] キューブまたはテーブル モデルに格納されたデータに直接アクセスすることはできません。 代わりに、Excel で [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーへの接続を作成し、そのデータを使用してモデルを作成します。  
  
### <a name="relational-data-sources"></a>リレーショナルデータソース  
 モデルへの入力としてリレーショナル ソースのデータを使用する場合は、次のバージョンの SQL Server に接続できます。  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
 また、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] でデータ ソースとしてサポートされている他のリレーショナル データ ソースからデータを取得することもできます。 サポートされているデータソースの詳細については、「[多次元モデルのデータソース](multidimensional-models/data-sources-in-multidimensional-models.md)」を参照してください。  
  
 以下のデータ型はデータ マイニングで使用することができません。モデルの構築時にこのデータ型が含まれていた場合は、エラーが発生します。  
  
-   ntext  
  
-   binary  
  
## <a name="see-also"></a>参照  
 [Excel 用のデータマイニングクライアントのトレース &#40;&#41;](trace-data-mining-client-for-excel.md)  
  
  

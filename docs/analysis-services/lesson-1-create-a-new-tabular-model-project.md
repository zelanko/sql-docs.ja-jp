---
title: 'レッスン 1: 新しいテーブル モデル プロジェクトの作成 |Microsoft ドキュメント'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 61ac5b1a0bac9647e6163a13afd0bce6b251ac03
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34019869"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>レッスン 1: 新しいテーブル モデル プロジェクトの作成
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に新しい空のテーブル モデル プロジェクトを作成します。 新しいプロジェクトが作成されたら、テーブルのインポート ウィザードを使用して、データの追加を開始できます。 このレッスンはオーサリング環境 SSDT で表形式モデルの概要も示します。  
  
このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックは、テーブル モデル作成チュートリアルの最初のレッスンです。 このレッスンを完了するには、SQL Server インスタンスにインストールされている、AdventureWorksDW サンプル データベースが必要です。 詳細については、次を参照してください。[テーブル モデリング&#40;Adventure Works チュートリアル&#41;](../analysis-services/tabular-modeling-adventure-works-tutorial.md)です。  
  
## <a name="create-a-new-tabular-model-project"></a>新しいテーブル モデル プロジェクトの作成  
  
#### <a name="to-create-a-new-tabular-model-project"></a>新しいテーブル モデル プロジェクトを作成するには  
  
1.  SSDT では、上、**ファイル** メニューのをクリックして**新規** > **プロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開**インストール済み** > **Business Intelligence** > **Analysis Services**、クリックして**Analysis Services 表形式プロジェクト**です。  
  
3.  **名前**、型**AW Internet Sales**、プロジェクト ファイルの場所を指定します。  
  
    既定では、 **[ソリューション名]** はプロジェクト名と同じですが、別のソリューション名を入力することもできます。  
  
4.  **[OK]** をクリックします。  
  
5.  **表形式モデル デザイナー**ダイアログ ボックスで、**統合ワークスペース**です。  
  
    ワークスペースは、モデル作成時に、プロジェクトと同じ名前のテーブル モデル データベースをホストします。 統合ワークスペースでは、SSDT を使用して、組み込みのインスタンス モデルを作成するためだけの独立した Analysis Services サーバー インスタンスをインストールする必要がなくなることを意味します。 詳細については、次を参照してください。[ワークスペース データベース](../analysis-services/tabular-models/workspace-database-ssas-tabular.md)です。
      
6.  **[互換性レベル]** で **[SQL Server 2016 (1200)]** が選択されていることを確認し、 **[OK]** をクリックします。   
 
    ![as-tabular-lesson1-tmd](../analysis-services/media/as-tabular-lesson1-tmd.png)
      
    SQL Server 2016 RTM (1200) の互換性レベルのボックスの一覧に表示されない場合は、SQL Server Data Tools の最新バージョンを使用していません。 最新バージョンの入手については、「 [SQL Server Data Tools のインストール](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)」を参照してください。  

    SQL Server 2017 ができます、最新バージョンの SSDT を使用している場合 (1400)。 ただし、完全なレッスン 13 を: 展開する、SQL Server 2017 または Azure サーバーを展開する必要があります。
      
    以前の互換性レベルを選択すると、以前のバージョンの SQL Server を実行している別の Analysis Services インスタンスに完了した、表形式モデルを配置する場合は、のみ推奨されます。 以前の互換性レベルでは、統合されたワークスペースはサポートされていません。 詳しくは、「 [互換性レベル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。   
  
## <a name="understanding-the-ssdt-tabular-model-authoring-environment"></a>SSDT の表形式モデル作成環境についてください。  
これで、新しい表形式モデル プロジェクトを作成した、オーサリング環境 SSDT で表形式モデルの調査にはしばらくを見てみましょう。  
  
プロジェクトを作成すると、SSDT でが開きます。 右側にあるで**表形式モデル エクスプ ローラー**モデル内のオブジェクトのツリー ビューが表示されます。 まだデータをインポートしていないため、フォルダーは空になります。 メニュー バーに同様のアクションを実行するオブジェクトのフォルダーを右クリックすることができます。 このチュートリアルのステップ実行すると、モデル プロジェクトで別のオブジェクトを移動するのに表形式モデル エクスプ ローラーを使用します。

![as-tabular-lesson1-tme](../analysis-services/media/as-tabular-lesson1-tme.png)

クリックして、**ソリューション エクスプ ローラー**タブです。ここが表示されます、 **Model.bim**ファイル。 左側 (空のウィンドウと Model.bim タブ)、デザイナーのウィンドウが表示されないかどうか**ソリューション エクスプ ローラー** **AW Internet Sales プロジェクト**をダブルクリックして、 **Model.bim**ファイル。 Model.bim ファイルには、すべてのモデル プロジェクトのメタデータが含まれています。 

![as-tabular-lesson1-se](../analysis-services/media/as-tabular-lesson1-se.png)
  
モデルのプロパティを見てみましょう。 をクリックして**Model.bim**です。 **プロパティ**ウィンドウが表示されます、[モデル プロパティの](../analysis-services/tabular-models/model-properties-ssas-tabular.md)、最も重要なは、 **DirectQuery モード**プロパティです。 このプロパティは、モデルがインメモリ モード (オフ) と DirectQuery モード (オン) のどちらで配置されるかを指定します。 このチュートリアルでは、インメモリ モードでモデルを作成し、展開します。

![as-tabular-lesson1-properties](../analysis-services/media/as-tabular-lesson1-properties.png)
  
指定できるデータ モデリング設定に従って、新しいモデルを作成するときに特定のモデルのプロパティを自動的に設定、**ツール** > **オプション** ダイアログ ボックス。 データ バックアップ、ワークスペースの保有期間、およびワークスペース サーバーの各プロパティは、ワークスペース データベース (モデル作成データベース) をバックアップ、メモリ内保持、および構築するための方法と場所を指定します。 これらの設定は後で必要に応じて変更できますが、ここではそのままにしておきます。  

**ソリューション エクスプ ローラー**を右クリックして**AW Internet Sales** (プロジェクト) をクリックし、**プロパティ**です。 **AW Internet Sales のプロパティ ページ** ダイアログ ボックスが表示されます。 これらは、高度な[プロジェクト プロパティ](../analysis-services/tabular-models/project-properties-ssas-tabular.md)です。 後で、モデルを配置する準備ができたら、これらのプロパティの一部を設定します。  
  
SSDT をインストールしたときに、いくつかの新しいメニュー項目は、Visual Studio 環境に追加されました。 テーブル モデルの作成に固有のものを見てみましょう。 **[モデル]** メニューをクリックしてください。 ここでは、テーブルのインポート ウィザードを起動、表示し既存の接続を編集、ワークスペース データを更新、Excel で分析機能を Excel でモデルを参照、パースペクティブとロールを作成、モデル ビューを選択して計算オプションを設定します。  
  
**[テーブル]** メニューをクリックしてください。 ここでは、テーブル間のリレーションシップを作成および管理したり、date テーブル設定を指定したり、パーティションを作成したり、テーブル プロパティを編集したりできます。  
  
**[列]** メニューをクリックしてください。 ここでは、テーブル内の列を追加および削除したり、列を固定したり、並べ替え順を指定したりできます。 オート SUM 機能を使用して、選択された列に対する標準集計測定を行うこともできます。 その他のツール バー ボタンは、よく使用される機能やコマンドにすばやくアクセスするために用意されています。  
  
いくつかのダイアログや場所を表示して、テーブル モデルの作成に関連する各種の機能を調べてみてください。 まだアクティブにならない項目もありますが、テーブル モデル作成環境の使用感を確認できます。  


## <a name="additional-resources"></a>その他のリソース
テーブル モデル プロジェクトのさまざまな種類の詳細については、次を参照してください。[表形式モデル プロジェクト](../analysis-services/tabular-models/tabular-model-projects-ssas-tabular.md)です。 表形式モデルの作成環境の詳細については、次を参照してください。[テーブル モデル デザイナー](../analysis-services/tabular-models/tabular-model-designer-ssas.md)です。  
  

## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 2: データを追加](../analysis-services/lesson-2-add-data.md)です。

  
  
  

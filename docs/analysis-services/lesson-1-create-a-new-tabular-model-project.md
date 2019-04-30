---
title: レッスン 1:新しい表形式モデル プロジェクトの作成 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 988a091fa7d536386cadd2ed3412213a2e608564
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63052911"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>レッスン 1:新しいテーブル モデル プロジェクトの作成
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に新しい空のテーブル モデル プロジェクトを作成します。 新しいプロジェクトが作成されたら、テーブルのインポート ウィザードを使用して、データの追加を開始できます。 このレッスンはオーサリング環境 SSDT で表形式モデルの概要も示します。  
  
このレッスンを完了するまでに時間を推定するには。**10 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックは、テーブル モデル作成チュートリアルの最初のレッスンです。 このレッスンを完了するには、SQL Server インスタンスにインストールされている、AdventureWorksDW サンプル データベースが必要です。 詳細についてを参照してください。[テーブル モデリング&#40;Adventure Works チュートリアル&#41;](../analysis-services/tabular-modeling-adventure-works-tutorial.md)します。  
  
## <a name="create-a-new-tabular-model-project"></a>新しいテーブル モデル プロジェクトの作成  
  
#### <a name="to-create-a-new-tabular-model-project"></a>新しいテーブル モデル プロジェクトを作成するには  
  
1.  SSDT での**ファイル** メニューのをクリックして**新規** > **プロジェクト**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開**インストール済み** > **Business Intelligence** > **Analysis Services**、 をクリックし、 **Analysis Services 表形式プロジェクト**します。  
  
3.  **名前**、型**AW Internet Sales**、し、プロジェクト ファイルの場所を指定します。  
  
    既定では、 **[ソリューション名]** はプロジェクト名と同じですが、別のソリューション名を入力することもできます。  
  
4.  **[OK]** をクリックします。  
  
5.  **表形式モデル デザイナー**ダイアログ ボックスで、**統合ワークスペース**します。  
  
    ワークスペースは、モデル作成時に、プロジェクトと同じ名前のテーブル モデル データベースをホストします。 統合ワークスペースでは、SSDT は、組み込みのインスタンスを使用、モデルのオーサリングのためだけに Analysis Services サーバー インスタンスを別途インストールする必要はありませんを意味します。 詳細についてを参照してください。[ワークスペース データベース](../analysis-services/tabular-models/workspace-database-ssas-tabular.md)します。
      
6.  **[互換性レベル]** で **[SQL Server 2016 (1200)]** が選択されていることを確認し、 **[OK]** をクリックします。   
 
    ![as-tabular-lesson1-tmd](../analysis-services/media/as-tabular-lesson1-tmd.png)
      
    SQL Server 2016 RTM (1200) Compatibility level リスト ボックス内に表示されない場合は、SQL Server Data Tools の最新バージョンを使用していません。 最新バージョンの入手については、「 [SQL Server Data Tools のインストール](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)」を参照してください。  

    最新バージョンの SSDT を使用している場合は、SQL Server 2017 も選択できます (1400)。 ただし、完全なレッスン 13: に展開を展開するには、SQL Server 2017 または Azure サーバーを必要があります。
      
    以前の互換性レベルを選択するで以前のバージョンの SQL Server を実行している別の Analysis Services インスタンスに完了した表形式モデルをデプロイする場合のみ推奨します。 統合ワークスペースは、以前の互換性レベルはサポートされていません。 詳しくは、「 [互換性レベル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。   
  
## <a name="understanding-the-ssdt-tabular-model-authoring-environment"></a>SSDT の表形式モデル オーサリング環境を理解します。  
新しいテーブル モデル プロジェクトを作成するので、作成環境を SSDT で表形式モデルを少し探ってをみましょう。  
  
プロジェクトを作成すると、SSDT でが開きます。 右側にあるで**Tabular Model Explorer**モデル内のオブジェクトのツリー ビューが表示されます。 データのインポートはまだ、ので、フォルダーは空になります。 メニュー バーのようなアクションを実行するオブジェクトのフォルダーを右クリックすることができます。 このチュートリアルをステップ実行すると、モデル プロジェクト内の異なるオブジェクトをナビゲートするのに表形式モデル エクスプ ローラーを使用します。

![as-tabular-lesson1-tme](../analysis-services/media/as-tabular-lesson1-tme.png)

をクリックして、**ソリューション エクスプ ローラー**タブ。ここでは、表示されます、 **Model.bim**ファイル。 (空のウィンドウと Model.bim タブ)、左に、デザイナー ウィンドウが表示されないかどうか**ソリューション エクスプ ローラー** **AW Internet Sales プロジェクト**、ダブルクリックして、 **Model.bim**ファイル。 Model.bim ファイルには、すべてのモデル プロジェクトのメタデータが含まれています。 

![as-tabular-lesson1-se](../analysis-services/media/as-tabular-lesson1-se.png)
  
モデルのプロパティを見てみましょう。 クリックして**Model.bim**します。 **プロパティ**ウィンドウが表示されます、[モデル プロパティの](../analysis-services/tabular-models/model-properties-ssas-tabular.md)、最も重要なは、 **DirectQuery モード**プロパティ。 このプロパティは、モデルがインメモリ モード (オフ) と DirectQuery モード (オン) のどちらで配置されるかを指定します。 このチュートリアルでは、インメモリ モードでモデルを作成し、展開します。

![as-tabular-lesson1-properties](../analysis-services/media/as-tabular-lesson1-properties.png)
  
指定できるデータ モデリング設定に従って、自動的に新しいモデルを作成するときに特定のモデル プロパティを設定、**ツール** > **オプション** ダイアログ ボックス。 データ バックアップ、ワークスペースの保有期間、およびワークスペース サーバーの各プロパティは、ワークスペース データベース (モデル作成データベース) をバックアップ、メモリ内保持、および構築するための方法と場所を指定します。 これらの設定は後で必要に応じて変更できますが、ここではそのままにしておきます。  

**ソリューション エクスプ ローラー**を右クリックして**AW Internet Sales** (プロジェクト) をクリックし、**プロパティ**します。 **AW Internet Sales Property Pages**  ダイアログ ボックスが表示されます。 これらは、高度な[プロジェクト プロパティ](../analysis-services/tabular-models/project-properties-ssas-tabular.md)します。 後で、モデルを配置する準備ができたら、これらのプロパティの一部を設定します。  
  
SSDT をインストールしたときに、いくつかの新しいメニュー項目は、Visual Studio 環境に追加されました。 テーブル モデルの作成に固有のものを見てみましょう。 **[モデル]** メニューをクリックしてください。 ここでは、テーブルのインポート ウィザードを起動、表示し既存の接続を編集、ワークスペース データを更新する、excel の Analyze in Excel 機能を使用してモデルを参照して、パースペクティブとロールを作成、､ モデル ビューの選択して計算オプションの設定。  
  
**[テーブル]** メニューをクリックしてください。 ここでは、テーブル間のリレーションシップを作成および管理したり、date テーブル設定を指定したり、パーティションを作成したり、テーブル プロパティを編集したりできます。  
  
**[列]** メニューをクリックしてください。 ここでは、テーブル内の列を追加および削除したり、列を固定したり、並べ替え順を指定したりできます。 オート SUM 機能を使用して、選択された列に対する標準集計測定を行うこともできます。 その他のツール バー ボタンは、よく使用される機能やコマンドにすばやくアクセスするために用意されています。  
  
いくつかのダイアログや場所を表示して、テーブル モデルの作成に関連する各種の機能を調べてみてください。 まだアクティブにならない項目もありますが、テーブル モデル作成環境の使用感を確認できます。  


## <a name="additional-resources"></a>その他の技術情報
テーブル モデル プロジェクトのさまざまな種類の詳細については、次を参照してください。[表形式モデル プロジェクト](../analysis-services/tabular-models/tabular-model-projects-ssas-tabular.md)します。 表形式モデル オーサリング環境についての詳細についてを参照してください。 [Tabular Model Designer](../analysis-services/tabular-models/tabular-model-designer-ssas.md)します。  
  

## <a name="whats-next"></a>次の操作
次のレッスンに移動します。[レッスン 2:データを追加する](../analysis-services/lesson-2-add-data.md)します。

  
  
  

---
title: 'レッスン 1: 新しいテーブルモデルプロジェクトを作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0d2eb34d-78c8-41ff-b92d-49b62c16b2ac
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fb9ca011cdbbe32ebd6c71cb9ca64967cfbccb9e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079305"
---
# <a name="lesson-1-create-a-new-tabular-model-project"></a>レッスン 1: 新しいテーブル モデル プロジェクトの作成
  このレッスンでは、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]に新しい空のテーブル モデル プロジェクトを作成します。 新しいプロジェクトが作成されたら、テーブルのインポート ウィザードを使用して、データの追加を開始できます。 新規プロジェクトの作成に加え、このレッスンでは、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]のテーブル モデル作成環境についても概説します。  
  
 テーブル モデル プロジェクトの種類については、「[テーブル モデル プロジェクト (SSAS テーブル)](tabular-models/tabular-model-projects-ssas-tabular.md)」を参照してください。 テーブルモデル作成環境の詳細については、「[テーブルモデルデザイナー &#40;SSAS 表形式&#41;](tabular-model-designer-ssas-tabular.md)」を参照してください。  
  
 このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは､表形式モデル オーサリング チュートリアルの最初のレッスンです｡ このレッスンを完了するには、SQL Server インスタンス上に AdventureWorksDW データベースがインストールされている必要があります。 詳しくは、「[テーブル モデリング (Adventure Works チュートリアル)](tabular-modeling-adventure-works-tutorial.md)」を参照してください。  
  
## <a name="create-a-new-tabular-model-project"></a>新しいテーブル モデル プロジェクトの作成  
  
#### <a name="to-create-a-new-tabular-model-project"></a>新しい表形式モデル プロジェクトを作成する  
  
1.  
  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]の **[ファイル]** メニューの **[新規作成]** をクリックし、 **[プロジェクト]** をクリックします。  
  
2.  [**新しいプロジェクト**] ダイアログボックスの [**インストールされているテンプレート**] で [**ビジネスインテリジェンス**] をクリックし、[ **Analysis Services**] をクリックして、[**テーブルプロジェクトの Analysis Services**] をクリックします。  
  
3.  [**名前**] に`AW Internet Sales Tabular Model`「」と入力し、プロジェクトファイルの場所を指定します。  
  
     既定では､ **Solution Name** はプロジェクト名と同じですが､別のソリューション名を指定することができます｡  
  
4.  **[OK]** をクリックします。  
  
## <a name="understanding-the-sql-server-data-tools-tabular-model-authoring-environment"></a>SQL Server データ ツールのテーブル モデル作成環境について  
 新しいテーブルモデルプロジェクトを作成したので、(Visual Studio 2010 以降) の[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]テーブルモデル作成環境について説明します。  
  
 プロジェクトを作成すると、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]が開きます。 モデル デザイナーに空のモデルが表示され、 **[ソリューション エクスプローラー]** ウィンドウで **Model.bim** ファイルが選択されます。 データを追加すると、デザイナーにテーブルと列が表示されます。 デザイナー (空のウィンドウと [モデルの bim] タブ) が表示されない場合**** は、ソリューションエクスプローラー `AW Internet Sales Tabular Model`の [] の下にある [] をクリックして、**モデルの bim**ファイルをダブルクリックします。  
  
 プロジェクトの基本プロパティは、 **[プロパティ]** ウィンドウで確認できます。 **ソリューションエクスプローラー**で、[ `AW Internet Sales Tabular Model`] をクリックします。 
  **[プロパティ]** ウィンドウの **[プロジェクト ファイル]** に、 **AW Internet Sales Tabular Model.smproj**と表示されます。 これがプロジェクト ファイル名で、 **[プロジェクト フォルダー]** には、プロジェクト ファイルの場所が表示されます。  
  
 **ソリューションエクスプローラー**で、 `AW Internet Sales Tabular Model`プロジェクトを右クリックし、[**プロパティ**] をクリックします。 
  **[AW Internet Sales Tabular Model プロパティ ページ]** ダイアログ ボックスが表示されます。 これらは詳細なプロジェクト プロパティです｡ 後で、モデルを配置する準備ができたら、これらのプロパティの一部を設定します。  
  
 では、モデルのプロパティを見てみましょう。 
  **[ソリューション エクスプローラー]** で、 **[Model.bim]** をクリックします。 
  **[プロパティ]** ウィンドウにモデルのプロパティが表示されます。特に重要なのは、 **DirectQuery Mode** プロパティです。 このプロパティは､モデルを In-Memory (Off) または DirectQuery (On) のどちらのモードでデプロイするかを指定します｡ このチュートリアルでは､In-Memory モードでモデルをオーサリングし､デプロイします｡  
  
 新しいモデルを作成すると、データ モデリング設定 ([ツール] メニューから開く [オプション] ダイアログ ボックスで指定できます) に応じて、特定のモデル プロパティが自動的に設定されます。 Data Backup と Workspace Retention､および Workspace Server は､それぞれワークスペース データベース (モデル オーサリング用データベース) のバックアップとインメモリー保持､構築の方法と場所を指定するプロパティです｡ これらのプロパティ設定を必要に応じて後で変更できますから､ここでは現在の設定のままにしておいてください｡  
  
 Visual Studio 環境には、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]をインストールした際に、いくつかの新しいメニュー項目が追加されています。 表形式モデルの作成に固有の新しいメニュー項目を見てみましょう。 
  **[モデル]** メニューをクリックします｡ ここから、テーブルのインポート ウィザードを起動したり、既存の接続を編集したり、ワークスペース データを更新したり、"Excel で分析" 機能を使用してモデルを [!INCLUDE[msCoName](../includes/msconame-md.md)] Excel で参照したり、パースペクティブとロールを作成したり、モデル ビューを選択したり、計算オプションを設定したりできます。  
  
 
  **[テーブル]** メニューをクリックします｡ ここでは、テーブル間のリレーションシップを作成および管理したり、date テーブル設定を指定したり、パーティションを作成したり、テーブル プロパティを編集したりできます。  
  
 
  **[列]** メニューをクリックしてください。 ここでは、テーブル内の列を追加および削除したり、列を固定したり、並べ替え順を指定したりできます。 オート SUM 機能を使用して、選択された列に対する標準集計測定を行うこともできます。 ツールバーの他のボタンからは､よく使う機能やコマンドに素早くアクセスできます｡  
  
 表形式モデルに特有のさまざまな機能に用意されているダイアログ ボックスや場所をいくつか探ってみてください｡ 一部項目がまだアクティブになっていませんが､表形式モデルのオーサリング環境を十分に理解できます｡  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン「 [レッスン 2: データの追加](lesson-2-add-data.md)」に進んでください。  
  
  

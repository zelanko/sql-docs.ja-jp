---
title: 'Analysis Services のチュートリアル レッスン 1: 新しいテーブル モデル プロジェクトを作成 |Microsoft ドキュメント'
description: 新しい Analysis Services tutorial プロジェクトを作成する方法について説明します。
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 55213810bdc40bf817b1349715474974d6a72540
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-tabular-model-project"></a>表形式モデル プロジェクトを作成します。

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは 1400 互換性レベルで新しいテーブル モデル プロジェクトを作成するのに SQL Server Data Tools (SSDT) または Microsoft Analysis Services プロジェクトの VSIX と共に Visual Studio 2017 で Visual Studio を使用します。 開始することができます、新しいプロジェクトが作成されると、データを追加して、モデルを作成します。 このレッスンは表形式モデルを Visual Studio での環境を作成の概要も示します。  
  
このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件

この記事では、テーブル モデル作成チュートリアルの最初のレッスンです。 このレッスンを完了するには、必要があります、インプレースいくつかの前提条件があります。 詳細については、次を参照してください。 [Analysis Services - Adventure Works チュートリアル](../tutorial-tabular-1400/as-adventure-works-tutorial.md)です。  
  
## <a name="create-a-new-tabular-model-project"></a>新しいテーブル モデル プロジェクトの作成  
  
#### <a name="to-create-a-new-tabular-model-project"></a>新しいテーブル モデル プロジェクトを作成するには  
  
1.  Visual Studio での**ファイル** メニューのをクリックして**新規** > **プロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開**インストール済み** > **Business Intelligence** > **Analysis Services**、クリックして**Analysis Services 表形式プロジェクト**です。  
  
3.  **名前**、型**AW Internet Sales**、プロジェクト ファイルの場所を指定します。  
  
    既定では、**ソリューション名**は、プロジェクト名と同じです。 ただし、別のソリューション名を入力することができます。  
  
4.  **[OK]** をクリックします。  
  
5.  **表形式モデル デザイナー**ダイアログ ボックスで、**統合ワークスペース**です。  
  
    ワークスペースは、モデル作成時に、プロジェクトと同じ名前のテーブル モデル データベースをホストします。 統合ワークスペースでは、Visual Studio インスタンスを使用して組み込み、モデルを作成するためだけの独立した Analysis Services サーバー インスタンスをインストールする必要がなくなることを意味します。
      
6.  **互換性レベル** **SQL Server 2017/Azure Analysis Services (1400)** です。   
 
    ![as-lesson1-tmd](../tutorial-tabular-1400/media/as-lesson1-tmd.png)
      
    SQL Server 2017/Azure Analysis Services (1400) の互換性レベルのボックスの一覧が表示されない場合は、SQL Server Data Tools の最新バージョンを使用していません。 最新バージョンの入手については、「 [SQL Server Data Tools のインストール](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)」を参照してください。  
      
  
## <a name="understanding-the-ssdt-tabular-model-authoring-environment"></a>SSDT の表形式モデル作成環境についてください。  

これで、新しい表形式モデル プロジェクトを作成した、Visual Studio での環境を作成する表形式モデルの調査にはしばらくを見てみましょう。  
  
プロジェクトを作成した後、Visual Studio で開きます。 右側にあるで**表形式モデル エクスプ ローラー**モデル内のオブジェクトのツリー ビューを参照してください。 まだデータをインポートしていないため、フォルダーが空です。 メニュー バーに同様のアクションを実行するオブジェクトのフォルダーを右クリックすることができます。 このチュートリアルのステップ実行すると、表形式モデル エクスプ ローラーを使用してモデル プロジェクトで別のオブジェクトを移動します。

![as-lesson1-tme](../tutorial-tabular-1400/media/as-lesson1-tme.png)

クリックして、**ソリューション エクスプ ローラー**タブです。ここで、参照、 **Model.bim**ファイル。 左側 (空のウィンドウと Model.bim タブ)、デザイナーのウィンドウが表示されないかどうか**ソリューション エクスプ ローラー** **AW Internet Sales プロジェクト**をダブルクリックして、 **Model.bim**ファイル。 Model.bim ファイルには、モデル プロジェクトのメタデータが含まれています。 

![as-lesson1-se](../tutorial-tabular-1400/media/as-lesson1-se.png)
  
をクリックして**Model.bim**です。 **プロパティ**ウィンドウで、最も重要なは、モデル プロパティを確認する、 **DirectQuery モード**プロパティです。 このプロパティは、インメモリ モード (オフ) または DirectQuery モード (オン) でモデルを配置するかどうかを指定します。 このチュートリアルでは、作成し、インメモリ モードでモデルを展開します。

![as-lesson1-properties](../tutorial-tabular-1400/media/as-lesson1-properties.png)
  
指定できるデータ モデリング設定に従って、モデル プロジェクトを作成するときに特定のモデルのプロパティを自動的に設定、**ツール**メニュー >**オプション** ダイアログ ボックス。 データ バックアップ、ワークスペースの保有期間、およびワークスペース サーバーの各プロパティは、ワークスペース データベース (モデル作成データベース) をバックアップ、メモリ内保持、および構築するための方法と場所を指定します。 必要に応じて、後でこれらの設定を変更できますが、ここでは、そのままにこれらのプロパティは。  

**ソリューション エクスプ ローラー**を右クリックして**AW Internet Sales** (プロジェクト) をクリックし、**プロパティ**です。 **AW Internet Sales のプロパティ ページ** ダイアログ ボックスが表示されます。 設定するこれらのプロパティのいくつか後で、モデルを展開するときにします。  
  
SSDT をインストールしたときに、いくつかの新しいメニュー項目は、Visual Studio 環境に追加されました。 クリックして、**モデル**メニュー。 ここでは、データをインポート、ワークスペース データを更新する、Excel でモデルを参照、パースペクティブとロールを作成、モデルのビューを選択して計算オプションを設定します。 クリックして、**テーブル**メニュー。 ここでは、することができますを作成し、リレーションシップの管理、日付テーブルの設定を指定、パーティションを作成およびテーブルのプロパティを編集します。 クリックした場合、**列**メニューで、追加し、テーブル内の列を削除の列を固定および並べ替え順序を指定します。 SSDT は、バーにもいくつかのボタンを追加します。 最も役に立つは、選択した列の標準の集計メジャーを作成するオート Sum 機能です。 その他のツール バー ボタンは、よく使用される機能やコマンドにすばやくアクセスするために用意されています。  
  
いくつかのダイアログや場所を表示して、テーブル モデルの作成に関連する各種の機能を調べてみてください。 一部の項目がまだアクティブいないときに、表形式モデルの作成環境のことをお勧めを取得できます。  
  

## <a name="whats-next"></a>次の操作

[レッスン 2: データの取得](../tutorial-tabular-1400/as-lesson-2-get-data.md)です。

  
  
  

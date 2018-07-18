---
title: 'Analysis Services チュートリアル-レッスン 1: 新しい表形式モデル プロジェクトの作成 |Microsoft Docs'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 403e6d04d339e3126afe964bd919304d04295c0b
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38007130"
---
# <a name="create-a-tabular-model-project"></a>表形式モデル プロジェクトを作成します。

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、1400 互換性レベルで新しいテーブル モデル プロジェクトを作成するのに SQL Server Data Tools (SSDT) または Microsoft Analysis Services プロジェクトの VSIX に Visual Studio 2017 で Visual Studio を使用します。 開始することができます、新しいプロジェクトが作成されると、データを追加して、モデルを作成します。 このレッスンは表形式モデル オーサリング環境で Visual Studio の概要も提供します。  
  
このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件

この記事では、表形式のモデル作成チュートリアルの最初のレッスンです。 このレッスンを完了するには、必要があります、インプレースいくつかの前提条件があります。 詳細についてを参照してください。 [Analysis Services - Adventure Works チュートリアル](../tutorial-tabular-1400/as-adventure-works-tutorial.md)します。  
  
## <a name="create-a-new-tabular-model-project"></a>新しいテーブル モデル プロジェクトの作成  
  
#### <a name="to-create-a-new-tabular-model-project"></a>新しいテーブル モデル プロジェクトを作成するには  
  
1.  Visual Studio での**ファイル** メニューのをクリックして**新規** > **プロジェクト**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開**インストール済み** > **Business Intelligence** > **Analysis Services**、 をクリックし、 **Analysis Services 表形式プロジェクト**します。  
  
3.  **名前**、型**AW Internet Sales**、し、プロジェクト ファイルの場所を指定します。  
  
    既定では、**ソリューション名**はプロジェクト名と同じです。 ただし、別のソリューション名を入力することができます。  
  
4.  **[OK]** をクリックします。  
  
5.  **表形式モデル デザイナー**ダイアログ ボックスで、**統合ワークスペース**します。  
  
    ワークスペースは、モデル作成時に、プロジェクトと同じ名前のテーブル モデル データベースをホストします。 統合ワークスペースでは、Visual Studio が使用モデルのオーサリングのためだけに Analysis Services サーバー インスタンスを別途インストールする必要がないため、組み込みのインスタンスを意味します。
      
6.  **互換性レベル**、 **SQL Server 2017/Azure Analysis Services (1400)** します。   
 
    ![as-lesson1-tmd](../tutorial-tabular-1400/media/as-lesson1-tmd.png)
      
    SQL Server 2017/Azure Analysis Services (1400) Compatibility level リスト ボックスで、表示されない場合は、SQL Server Data Tools の最新バージョンを使用していません。 最新バージョンの入手については、「 [SQL Server Data Tools のインストール](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)」を参照してください。  
      
  
## <a name="understanding-the-ssdt-tabular-model-authoring-environment"></a>SSDT の表形式モデル オーサリング環境を理解します。  

新しいテーブル モデル プロジェクトを作成するので、Visual Studio での環境を作成する表形式モデルを少し探ってをみましょう。  
  
プロジェクトの作成後は、Visual Studio で開きます。 右側にあるで**Tabular Model Explorer**モデル内のオブジェクトのツリー ビューを参照してください。 データのインポートはまだ、ので、フォルダーが空です。 メニュー バーのようなアクションを実行するオブジェクトのフォルダーを右クリックすることができます。 このチュートリアルの手順と表形式モデル エクスプ ローラーを使用して ､ モデル プロジェクト内の異なるオブジェクトを移動します。

![as-lesson1-tme](../tutorial-tabular-1400/media/as-lesson1-tme.png)

をクリックして、**ソリューション エクスプ ローラー**タブ。ここでは、表示、 **Model.bim**ファイル。 (空のウィンドウと Model.bim タブ)、左に、デザイナー ウィンドウが表示されないかどうか**ソリューション エクスプ ローラー** **AW Internet Sales プロジェクト**、ダブルクリックして、 **Model.bim**ファイル。 Model.bim ファイルには ､ モデル プロジェクトのメタデータが含まれています。 

![as-lesson1-se](../tutorial-tabular-1400/media/as-lesson1-se.png)
  
クリックして**Model.bim**します。 **プロパティ**ウィンドウに、最も重要なは、モデル プロパティを表示、 **DirectQuery モード**プロパティ。 このプロパティは、インメモリ モード (オフ) または (On) の DirectQuery モードでモデルが展開されているかどうかを指定します。 このチュートリアルでは、作成して、インメモリ モードでモデルをデプロイします。

![as-lesson1-properties](../tutorial-tabular-1400/media/as-lesson1-properties.png)
  
指定できるデータ モデリング設定に従って、自動的にモデル プロジェクトを作成するときに特定のモデル プロパティを設定、**ツール**メニュー >**オプション** ダイアログ ボックス。 データ バックアップ、ワークスペースの保有期間、およびワークスペース サーバーの各プロパティは、ワークスペース データベース (モデル作成データベース) をバックアップ、メモリ内保持、および構築するための方法と場所を指定します。 必要に応じて、後でこれらの設定を変更できますが、ここはそのままこれらのプロパティ。  

**ソリューション エクスプ ローラー**を右クリックして**AW Internet Sales** (プロジェクト) をクリックし、**プロパティ**します。 **AW Internet Sales Property Pages**  ダイアログ ボックスが表示されます。 設定するこれらのプロパティの後でモデルをデプロイするときにします。  
  
SSDT をインストールしたときに、いくつかの新しいメニュー項目は、Visual Studio 環境に追加されました。 をクリックして、**モデル**メニュー。 ここでは、データをインポート、ワークスペース データを更新する、Excel でのモデルの参照、パースペクティブとロールを作成、､ モデル ビューを選択でき計算オプションを設定できます。 をクリックして、**テーブル**メニュー。 ここでは、作成しリレーションシップの管理、日付テーブルの設定を指定、パーティションを作成してテーブルのプロパティを編集します。 クリックすると、**列**メニューで、追加し、テーブル内の列を削除、列を固定および並べ替え順序を指定します。 SSDT は、バーにもいくつかのボタンを追加します。 最も役に立つは、選択した列の標準の集計メジャーを作成する オート Sum 機能です。 その他のツール バー ボタンは、よく使用される機能やコマンドにすばやくアクセスするために用意されています。  
  
いくつかのダイアログや場所を表示して、テーブル モデルの作成に関連する各種の機能を調べてみてください。 いくつかの項目は、まだアクティブは、表形式モデル オーサリング環境のことをお勧めを取得できます。  
  

## <a name="whats-next"></a>次の操作

[レッスン 2: データの取得](../tutorial-tabular-1400/as-lesson-2-get-data.md)します。

  
  
  

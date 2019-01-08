---
title: SQL Server のデータ マイニング アドインを Office の |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 89986d3c8de4a1cbefbccf285a92a2dc19c6c7aa
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52504750"
---
# <a name="sql-server-data-mining-add-ins-for-office"></a>Office 用 SQL Server データ マイニング アドイン

  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Office 用データ マイニング アドインは、予測、推奨設定、または検索の分析モデルを構築するために Excel のデータを使用できるようにする軽量な一連の予測分析用ツールです。  
  
> [!IMPORTANT]
> データ マイニング アドインを Office には、以降 Office 2016 ではサポートされません。
  
 アドインのウィザードおよびデータ管理のツールでは、次の一般的なデータ マイニング タスクの実行手順を説明しています。  
  
-   **モデリングの前のデータの整理とクレンジング。** Excel またはあらゆる Excel データ ソースに格納されているデータを使用します。 データ ソースの再利用、実験の繰り返し、またはモデルの再トレーニングに利用する接続を作成して保存できます。  
  
-   **プロファイリング、サンプリング、および準備** 多くの経験豊富なデータ マイニング担当者によれば、データ マイニング プロジェクトの 70 ～ 90% がデータの準備に費やされます。 アドインはこのタスクを高速化でき、Excel およびウィザードで視覚エフェクトを提供して、次の一般的なタスクを手助けします。  
  
    -   データをプロファイルし、その分布と特性を理解します。  
  
    -   ランダム サンプリングまたはオーバーサンプリングによってトレーニング データ セットとテスト セットを作成します。  
  
    -   外れ値を検出して、削除または置き換えます。  
  
    -   データのラベルを変更して分析の質を高めます。  
  
-   **教師あり学習または教師なし学習によるパターンの分析。** ウィザードをクリックで進みながら、クラスター分析、マーケット バスケット分析、予測など最も一般的なデータ マイニング タスクを実行できます。  
  
     このアドインには、Naïve Bayes、ロジスティック回帰、クラスタリング、時系列、ニューラル ネットワークなど広く利用されている機械学習アルゴリズムが含まれています。  
  
     データ マイニングを初めて使用する場合は、予測クエリの構築に関するヘルプを **クエリ** ウィザードから入手できます。  
  
     上級ユーザーの場合、 **詳細クエリ エディター**を使用したドラッグ アンド ドロップによるカスタムの DMX クエリ作成や、Excel VBA を使用した予測の自動化が可能です。  
  
-   **ドキュメントと管理。** データ セットを作成し、モデルを構築したら、データとモデル パラメーターの統計サマリーを生成することによって、作業と洞察を文書化します。  
  
-   **調査と視覚化。** データ マイニングは、完全に自動化できるアクティビティではない - を探索して意味のあるアクションを実行するように、結果を理解する必要があります。 アドインは、Excel の対話的ビューアー、モデル ダイアグラムをカスタマイズできる Visio テンプレート、追加のフィルタリングまたは修正のためにグラフとテーブルを Excel にエクスポートする機能を備えており、調査に役立ちます。  
  
-   **配置と統合。** 運用環境に、実験用のサーバーからの別のインスタンスにモデルをエクスポートする管理ツールを使用して、モデルを配置、有用なモデルを作成した場合[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]します。  
  
     また、作成時のサーバー上にモデルを残したまま、トレーニング データを更新し、Integration Services または DMX スクリプトを使用して予測を実行することもできます。  
  
     パワー ユーザーには、サーバーに送信した XMLA および DMX ステートメントを表示できる **トレース** 機能が役立ちます。  
  
## <a name="getting-started"></a>作業の開始  
 詳細については、「 [Office 用データ マイニング アドインの内容](http://go.microsoft.com/fwlink/p/?LinkId=616849)」を参照してください。  
  
## <a name="support-and-requirements"></a>サポートと必要条件  
 Office 用 SQL Server データ マイニング アドインは無料でダウンロードできます。 これらのツールを使用するには、次のいずれかのバージョンの Office が既にインストールされている必要があります。  
  
-   Office 2010 (32 ビット版または 64 ビット版)  
  
-   Office 2013 (32 ビット版または 64 ビット版)  
  
> [!WARNING]  
>  現在の Excel のバージョンに対応するバージョンのアドインをダウンロードしてください。  
  
 データ マイニング アドインを使用する場合は、以下のいずれかのエディションの SQL Server Analysis Services に接続する必要があります。  
  
-   Enterprise  
  
-   Business Intelligence  
  
-   Standard  
  
 接続先の SQL Server Analysis Services のエディションによっては、高度なアルゴリズムの一部を使用できない場合があります。 詳細については、「 [SQL Server 2016 の各エディションがサポートする機能](../../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)」を参照してください。  
  
 インストールの詳細については、ダウンロード センターからこのページを参照してください。 [http://www.microsoft.com/download/details.aspx?id=29061](http://www.microsoft.com/download/details.aspx?id=29061)  
  
  

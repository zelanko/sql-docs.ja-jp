---
title: Office 用データマイニングアドインの SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c9021a19-2c19-4f0a-a293-5f7e0ac2524c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 94b9935f5ab13431033accf7431c1a9b6394569a
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84520512"
---
# <a name="sql-server-data-mining-add-ins-for-office"></a>Office 用 SQL Server データ マイニング アドイン
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Office 用データ マイニング アドインは、予測、推奨設定、または検索の分析モデルを構築するために Excel のデータを使用できるようにする軽量な一連の予測分析用ツールです。  
  
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
  
-   **ドキュメントと管理。** データセットを作成し、いくつかのモデルを構築したら、データとモデルパラメーターの統計サマリーを生成して、作業と洞察を文書化します。  
  
-   **調査と視覚化。** データマイニングは、完全に自動化できるアクティビティではありません。結果を調査して理解し、意味のあるアクションを実行する必要があります。 アドインは、Excel の対話的ビューアー、モデル ダイアグラムをカスタマイズできる Visio テンプレート、追加のフィルタリングまたは修正のためにグラフとテーブルを Excel にエクスポートする機能を備えており、調査に役立ちます。  
  
-   **配置と統合。** 有用なモデルを作成したら、モデルを運用環境に配置します。そのためには、管理ツールを使用して、実験用サーバーからの別のインスタンスにモデルをエクスポートし [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。  
  
     また、作成時のサーバー上にモデルを残したまま、トレーニング データを更新し、Integration Services または DMX スクリプトを使用して予測を実行することもできます。  
  
     パワー ユーザーには、サーバーに送信した XMLA および DMX ステートメントを表示できる **トレース** 機能が役立ちます。  
  
## <a name="getting-started"></a>作業の開始  
 ツールの説明を読んでツールを設定するには、次のトピックを参照してください。  
  
-   [Excel 用のデータマイニングクライアント &#40;SQL Server データマイニングアドイン&#41;](../data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
-   [Excel 用テーブル分析ツール](../table-analysis-tools-for-excel.md)  
  
-   [Visio 用のデータ マイニング図形](../data-mining-shapes-for-visio.md)  
  
-   [データ マイニング サーバーへの接続](../connect-to-a-data-mining-server.md)  
  
## <a name="support-and-requirements"></a>サポートと必要条件  
 Office 用 SQL Server データ マイニング アドインは無料でダウンロードできます。 これらのツールを使用するには、次のいずれかのバージョンの Office が既にインストールされている必要があります。  
  
-   Office 2010 (32 ビット版または 64 ビット版)  
  
-   Office 2013 (32 ビット版または 64 ビット版)  
  
> [!WARNING]  
>  現在の Excel のバージョンに対応するバージョンのアドインをダウンロードしてください。  
  
 データ マイニング アドインを使用する場合は、以下のいずれかのエディションの SQL Server Analysis Services に接続する必要があります。  
  
-   エンタープライズ  
  
-   ビジネス インテリジェンス  
  
-   Standard  
  
 接続先の SQL Server Analysis Services のエディションによっては、高度なアルゴリズムの一部を使用できない場合があります。 詳細については、「 [SQL Server 2014 の各エディションがサポートする機能](https://msdn.microsoft.com/library/cc645993.aspx)」を参照してください。  
  
 インストールに関するその他のヘルプについては、ダウンロードセンターの次のページを参照してください。[https://www.microsoft.com/download/details.aspx?id=29061](https://www.microsoft.com/download/details.aspx?id=29061)  
  
  

---
title: Excel 用のテーブル分析ツール |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- getting started
ms.assetid: 6d9d1481-18e4-4108-9efa-68152b0940c9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af4c8ae7c2ba827e6110602bd21432fec4f74393
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067973"
---
# <a name="table-analysis-tools-for-excel"></a>Excel 用テーブル分析ツール
  [**分析**] ツールバーのデータマイニングツールは、データマイニングを開始する最も簡単な方法です。 これらのツールは、自動的にデータの分布と型を分析し、有効な結果を取得できるようパラメーターを設定します。 アルゴリズムを選択したり、複雑なパラメーターを構成したりする必要はありません。  
  
 ![DM](media/dm-tabletoolsanalyze.gif "DM")  
  
 [**分析**リボンには、次のツールがあります。  
  
 [Excel 用のテーブル分析ツール &#40;主要な影響元の分析&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 目的の列または出力値を選択すると、アルゴリズムがすべての入力データを分析して、対象に最大の影響を与えている要因を特定します。 必要に応じて、2 つの値を比較するレポートを作成できます。これにより、影響元がどのように変化するかを確認できます。  
  
 **主要影響**元の分析ツールでは、Microsoft の単純 Bayes アルゴリズムが使用されます。  
  
 [Excel 用のテーブル分析ツール &#40;のカテゴリの検出&#41;](detect-categories-table-analysis-tools-for-excel.md)  
 このツールを使用すると、任意のデータセットを追加し、クラスタリングを適用することによって、データのグループ化を検出できます。 類似点を見つけて、さらに分析するグループを作成する場合に便利です。  
  
 **カテゴリの検出**ツールは、Microsoft クラスタリングアルゴリズムを使用します。  
  
 [例 &#40;Excel 用のテーブル分析ツール&#41;](fill-from-example-table-analysis-tools-for-excel.md)  
 このツールは、不足値を帰属させるために役立ちます。 不足値の例をいくつか指定すると、このツールはテーブル内のすべてのデータに基づいてパターンを作成し、データのパターンに基づいて新しい値を推奨します。  
  
 **Fill From サンプル**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。  
  
 [Excel 用のテーブル分析ツールの予測 &#40;&#41;](forecast-table-analysis-tools-for-excel.md)  
 このツールは、時間の経過と共に変化するデータを取得し、将来の値を予測します。  
  
 **予測**ツールでは、Microsoft タイムシリーズアルゴリズムが使用されます。  
  
 [Excel 用のテーブル分析ツール &#40;例外を強調表示&#41;](highlight-exceptions-table-analysis-tools-for-excel.md)  
 このツールでは、データテーブル内のパターンを分析し、パターンに合わない行と値を検索します。 ユーザーは、これらの値を確認し、修正してモデルを再実行することも、後で処理するためにこれらの値にフラグを設定することもできます。  
  
 **例外の強調表示**ツールは、Microsoft クラスタリングアルゴリズムを使用します。  
  
 [ゴールシークシナリオ &#40;Excel 用のテーブル分析ツール&#41;](goal-seek-scenario-table-analysis-tools-for-excel.md)  
 **ゴールシーク**ツールでは、ターゲット値を指定します。このツールは、そのターゲットを満たすために変更する必要がある基になる要因を識別します。 たとえば、電話対応満足度を 20% 向上させる必要がある場合、その目標を達成するために変更する必要のある要因を予測するようモデルに要求できます。  
  
 **ゴールシーク**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。  
  
 [What-if シナリオ &#40;Excel 用のテーブル分析ツール&#41;](what-if-scenario-table-analysis-tools-for-excel.md)  
 **What-if 分析**ツールは、**ゴールシーク**ツールを補完します。 このツールで変更する必要のある値を入力すると、モデルはその変更が目標の結果を達成するために十分であるかどうかを予測します。 たとえば、電話オペレーターを 1 人追加することによって顧客満足度が 1 ポイント向上するかどうかを推測するようモデルに要求できます。  
  
 **What-if**ツールは、Microsoft ロジスティック回帰アルゴリズムを使用します。  
  
 [予測計算 &#40;Excel 用のテーブル分析ツール&#41;](prediction-calculator-table-analysis-tools-for-excel.md)  
 このツールは、目標となる結果につながる要因を分析するモデルを作成し、データから派生したスコア ルールに基づいて新しい入力の結果を予測します。 また、このツールは、新しい入力のスコアを簡単に記録できる対話的な意思決定ワークシートも生成します。 ユーザーは、オフラインで使用できるスコアリング ワークシートの印刷バージョンを作成することもできます。  
  
 **予測計算**ツールでは、Microsoft ロジスティック回帰アルゴリズムが使用されます。  
  
 [買い物かご分析 &#40;テーブル AnalysisTools for Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)  
 このツールは、クロスセルやアップセルで使用できるパターンを特定します。 同時に購入される頻度が高い製品グループを特定し、関連製品バンドルの価格およびコストに基づいてレポートも生成して、意思決定を支援します。  
  
 ツールの機能は、マーケット バスケット分析に限られません。アソシエーション分析に向いているすべての問題に対して適用できます。 たとえば、頻繁に同時発生するイベント、診断につながる要因、またはその他の考えられる原因と結果のセットを探すこともできます。  
  
 **買い物かご分析**ツールでは、Microsoft アソシエーションアルゴリズムが使用されます。  
  
## <a name="requirements-for-the-table-analysis-tools-for-excel"></a>Excel 用のテーブル分析ツールの要件  
 Excel 用のテーブル分析ツールを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへの接続を作成しておく必要があります。 データの分析に使用される Microsoft データ マイニング アルゴリズムには、この接続を介してアクセスします。 インスタンスにアクセスできない場合、データ マイニングを試すときに使用できるインスタンスを設定するよう管理者に依頼することをお勧めします。 詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。  
  
 テーブル分析ツールでデータを操作するには、使用する一連のデータを Excel テーブルに変換する必要があります。  
  
 [**分析**] リボンが表示されない場合は、まずデータテーブル内をクリックしてください。 メニューは、データ テーブルを選択するまでアクティブになりません。  
  
## <a name="see-also"></a>参照  
 [Excel 用のデータマイニングクライアント &#40;SQL Server データマイニングアドイン&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)   
 [データマイニングアドインの &#40;SQL Server Visio データマイニングダイアグラムのトラブルシューティング&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)   
 [Office 用データ マイニング アドインの内容](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  

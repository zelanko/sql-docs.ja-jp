---
title: 推定ウィザード (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- estimation
ms.assetid: 7f2b1d5f-c9b3-4939-b35a-34ae099af15f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2706dae37c1dc303aa6708fe1f7387a39835e4d5
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528370"
---
# <a name="estimate-wizard-data-mining-add-ins-for-excel"></a>推定ウィザード (Excel 用データ マイニング アドイン)
  ![[データ マイニング] リボンの推定ウィザード](media/dmc-estimate.gif "[データ マイニング] リボンの推定ウィザード")  
  
 **推定**ウィザードを使用すると、推定モデルを作成できます。 推定モデルは、データからパターンを抽出し、そのパターンを使用して結果に影響を与える要因を予測します。  
  
 推定は数値の結果を予測するために使用されます。 たとえば、教育機関の卒業率をパーセンテージで表した値が対象列に格納されている場合、教育機関ごとの生徒数、生徒と教員の比率、教員数など、卒業率の増減に関係する可能性がある要因を分析できます。  
  
## <a name="using-the-estimate-data-wizard"></a>データ推定ウィザードの使用  
  
1.  [**データマイニング**] リボンで、[**推定**] をクリックします。  
  
2.  **[ソースデータの選択**] ダイアログボックスで、使用するソースデータを選択します。 Excel**テーブル**、Excel**データ範囲**、または**外部データソース**のデータを使用できます。  
  
     外部データ ソースを使用する場合、カスタム ビューまたはカスタム クエリを作成し、それを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソースとして保存できます。  
  
3.  [**推定**] ダイアログボックスで、**分析する列**を選択します。  
  
     対象列には、連続する数値データが格納されている必要があります。  
  
4.  [**入力列**] チェックボックスをオンにして、入力として使用する列を選択します。  
  
     選択した列は、パターンの作成に使用されます。 分析には不要と思われる ID 番号などの列や、分析とは無関係なデータを含んだ列は、除外する必要があります。  
  
5.  **推定**ウィザードでは、データセットに最適なアルゴリズムが選択されます。 ただし、[**パラメーター** ] をクリックして [**アルゴリズムパラメーター** ] ダイアログボックスを開き、詳細オプションを設定することができます。  
  
6.  データが数値であり、Microsoft 線形回帰方式を使用できる場合、予測可能な値と関連付けられていることがわかっている (または非常に疑わしい) 数値列について、[**リグレッサー** ] ボックスをオンにすることができます。  
  
     そうすると、アルゴリズムによって、その列の値がテストされ、値が出力に影響するかどうかが判断されます。 わからない場合は、[**提案**] をクリックすると、アルゴリズムによってすべての列がテストされ、リグレッサーとして使用する最適な値が自動的に検出されます。  
  
    > [!NOTE]  
    >  推定を作成するにはリグレッサーが必要です。 ウィザードでは、データに対する最初のパスに基づいて、常に最適なリグレッサーが提示されます。 このため、どれを選択すればよいかわからない場合は、推奨された選択内容を使用することをお勧めします。  
  
7.  [**データをトレーニングセットとテストセットに分割**] ページで、テスト用にデータの小さなサブセットを作成するかどうかを指定します。  
  
8.  [**完了**] ページで、新しいマイニング構造とマイニングモードの名前を指定するか、既定の名前をそのまま使用します。  
  
9. モデルを使用するためのオプションを設定します。  
  
    -   [**参照**] を選択して、すぐにビューアーでモデルを開きます。  
  
         このグラフィカルなビューアーには、依存関係ネットワーク グラフやアルゴリズムによって生成されたデジション ツリーなどが表示されます。 この情報を調査することで、推測値をもたらした要因をより深く理解できます。  
  
    -   分析のユーザーが基になるデータを表示できるようにするには、[**ドリルスルーを有効**にする] を選択します。  
  
         このオプションを使用できるのは、デシジョン ツリー アルゴリズムまたは線形回帰アルゴリズムを使用する場合だけです。  
  
    -   **一時的なモデルを使用**します。 このチェック ボックスをオンにすると、モデルがサーバーに保存されません。 一時的なモデルは、Excel の終了時に削除されます。  
  
## <a name="more-about-estimation-models"></a>推定モデルの詳細  
 **推定**ウィザードでは、次のいずれかのアルゴリズムの使用がサポートされています。  
  
-   Microsoft デシジョンツリーアルゴリズム  
  
-   Microsoft 線形回帰アルゴリズム  
  
-   Microsoft ロジスティック回帰アルゴリズム  
  
-   Microsoft ニューラルネットワークアルゴリズム  
  
 [**アルゴリズムパラメーター** ] ダイアログボックスでは、選択したアルゴリズムに応じて、追加の詳細オプションを設定できます。 各アルゴリズムのオプションの詳細については、SQL Server オンライン ブックの次のトピックを参照してください。  
  
 [Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [Microsoft 線形回帰アルゴリズム テクニカル リファレンス](data-mining/microsoft-linear-regression-algorithm-technical-reference.md)  
  
 [Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [Microsoft Neural Network Algorithm Technical Reference](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a>要件  
 データ推定ウィザードを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに接続する必要があります。  
  
 接続を作成する方法の詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。  
  
 推定アルゴリズムを使用するには、予測しようとしている結果を、通貨、売上高、日付、時刻などの数値で表す必要があります。  
  
## <a name="see-also"></a>参照  
 [データマイニングモデルの作成](creating-a-data-mining-model.md)   
 [デシジョンツリーダイアグラムのチュートリアル &#40;データマイニングアドイン&#41;](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
  

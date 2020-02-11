---
title: 分類ウィザード (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- classification [data mining]
ms.assetid: 409c5076-c4c3-4f09-8f30-d3297df45f13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a62d937a733ea41b85a83224a043ff4ad7ecdd29
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087933"
---
# <a name="classify-wizard-data-mining-add-ins-for-excel"></a>分類ウィザード (Excel 用データ マイニング アドイン)
  ![[データ マイニング] リボンの分類ウィザード](media/dmc-classify.gif "[データ マイニング] リボンの分類ウィザード")  
  
 **分類**ウィザードを使用すると、excel テーブル、excel 範囲、または外部データソースの既存のデータに基づいて分類モデルを作成できます。  
  
 分類モデルはデータから共通のパターンを抽出します。そのため、分類モデルを使用すると、グループ化された値に基づいて予測を行うことができます。 たとえば、分類モデルを使用して、収入パターンまたは支出パターンに基づくリスクを予測できます。  
  
## <a name="using-the-classify-wizard"></a>分類ウィザードの使用  
  
1.  [**データマイニング**] リボンで、[**分類**] をクリックし、[**次へ**] をクリックします。  
  
2.  **[ソースデータの選択**] ページで、分析するデータを選択します。  
  
     このウィザードは、複数の種類のデータ (Excel テーブル、Excel 範囲、および外部データ ソース) をサポートしています。 外部データを使用する場合、外部データを Excel に追加するか、Analysis Services データ ソース内の一連のテーブルまたはビューを選択することができます。 また、テーブルを追加したり列を変更したりして、アドホック データ ソースを作成することもできます。  
  
3.  [**分類**] ページで、分類する列を選択します。  
  
     リスト内の列、**入力列**を確認し、一意の値を持つ列を選択解除し、ID 番号や顧客名などのパターンを作成するには役に立ちません。 また、実質的に分類可能な列と重複する列も削除する必要があります。  
  
     たとえば、製品カテゴリの予測を分類する場合、既知のビジネス ルールがある場合はサブカテゴリ フィールドを除外する必要があります。そうしないと、そのルールの強度によって、他の相関関係を発見できなくなる場合があります。  
  
4.  必要に応じて、[**パラメーター** ] をクリックして、アルゴリズムパラメーターを変更し、クラスターモデルの動作をカスタマイズします。  
  
5.  [**データをトレーニングセットとテストセットに分割**] ページで、テスト用に保持するデータの量を指定します。 残りのデータは、常にモデルのトレーニングに使用されます。  
  
     既定の設定では、30% がテスト データ、70% がトレーニング データです。  
  
6.  [**完了**] ページで、データセットとモデルのわかりやすい名前を指定し、完成したモデルの操作方法を制御する次のオプションを設定します。  
  
    -   **モデルを参照**します。 このオプションを選択すると、ウィザードがモデルの処理を終了するとすぐに、[**参照**] ウィンドウが開き、結果を調べることができます。 ビューアーの内容は、構築したモデルの種類によって異なります。 詳細については、「[デシジョンツリーモデルの参照](browsing-a-decision-trees-model.md)」および「[ニューラルネットワークモデルの参照](browsing-a-neural-network-model.md)」を参照してください。  
  
    -   **ドリルスルーを有効に**します。 このチェック ボックスをオンにすると、完成したモデルから基になるデータを表示できます。 このオプションは、デシジョン ツリー モデルを構築する場合にのみ使用できます。  
  
    -   **一時的なモデルを使用**します。 このチェック ボックスをオンにすると、モデルがサーバーに保存されません。 一時的なモデルは、Excel の終了時に削除されます。  
  
## <a name="more-about-classification-models"></a>分類モデルの詳細  
 [**アルゴリズムパラメーター** ] ダイアログボックスでは、Analysis Services に用意されている次のアルゴリズムの中から分類方法を選択することもできます。  
  
-   Microsoft デシジョン ツリー  
  
-   Microsoft ロジスティック回帰  
  
-   Microsoft Naïve Bayes  
  
-   Microsoft ニューラル ネットワーク  
  
 複数のアルゴリズムで同様の結果が生じる場合がありますが、アルゴリズムによってデータの分析方法は異なるため、いくつかのアルゴリズムを試して結果を比較することをお勧めします。 既定の方法は、Microsoft デシジョン ツリーです。  
  
 [**パラメーター** ] ボックスの一覧では、選択したアルゴリズムの種類に応じて、詳細設定オプションを変更できます。 各アルゴリズムのパラメーターについては、SQL Server オンライン ブックで詳しく説明します。  
  
 [Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [Microsoft Naive Bayes アルゴリズム テクニカル リファレンス](data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
 [Microsoft Neural Network Algorithm Technical Reference](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a>必要条件  
 **分類**ウィザードを使用するには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]データベースに接続している必要があります。 接続を作成する方法の詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データ マイニング モデルの作成](creating-a-data-mining-model.md)  
  
  

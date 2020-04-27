---
title: クラスターウィザード (Excel 用データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clustering [data mining]
ms.assetid: 85b25625-a7ab-4960-9f9c-df22e8ecae37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d93f676aec67b5d791924cbbda8f71a966d5bbc2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66087807"
---
# <a name="cluster-wizard-data-mining-add-ins-for-excel"></a>クラスター ウィザード (Excel 用データ マイニング アドイン)
  ![[データ マイニング] リボンのクラスター ウィザード](media/dmc-cluster.gif "[データ マイニング] リボンのクラスター ウィザード")  
  
 クラスター ウィザードでは、似た特性を共有する行を検出し、それらをグループ化してグループ間の距離を最大化するモデルを構築できます。 このウィザードは、あらゆる種類のデータのパターンを検索する場合に有用です。  
  
 クラスター ウィザードは、Microsoft クラスタリング アルゴリズムを使用しており、広範なカスタマイズが可能です。 このウィザードは、Excel テーブル、Excel 範囲、または [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] クエリからの既存のデータで動作します。 同様の機能は、Excel 用のテーブル分析ツールに用意されている[カテゴリの検出](detect-categories-table-analysis-tools-for-excel.md)ツールによって提供されます。 ただし、カテゴリの検出ツールはカスタマイズできないため、Excel テーブルのデータを使用する必要があります。  
  
## <a name="using-the-cluster-wizard"></a>クラスター ウィザードの使用  
  
1.  [データマイニング] リボンで、[**クラスター**] をクリックし、[**次へ**] をクリックします。  
  
2.  **[ソースデータの選択**] ページで、Excel のテーブルまたは範囲を選択します。 または、外部データ ソースを指定します。  
  
     外部データ ソースを使用する場合、カスタム ビューを作成するかカスタム クエリ テキストを貼り付けて、データ セットを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データ ソースとして保存できます。  
  
3.  [**クラスタリング**] ページでは、モデルの構築方法をカスタマイズできます。  
  
    -   **セグメント**数については、ウィザードで固定数のカテゴリを作成したり、最適なグループ数を自動的に検出したりすることができます。  
  
    -   [**入力列**] ボックスの一覧で列の一覧を確認し、パターンの作成に役立たない列を選択解除します。 除外する必要のある列には、ID 番号や顧客名などがあります。  
  
4.  必要に応じて、[**パラメーター** ] をクリックして、アルゴリズムパラメーターを変更し、クラスターモデルの動作をカスタマイズします。  
  
5.  [**データをトレーニングセットとテストセットに分割**] ページで、テスト用に保持するデータの量を指定します。 残りのデータは、常にモデルのトレーニングに使用されます。  
  
     既定の設定では、30% がテスト データ、70% がトレーニング データです。  
  
6.  [**完了**] ページで、データセットとモデルのわかりやすい名前を指定し、完成したモデルの操作方法を制御する次のオプションを設定します。  
  
    -   **モデルを参照**します。 このオプションを選択すると、ウィザードがモデルの処理を終了するとすぐに、[**参照**] ウィンドウが開き、結果を調べることができます。 ビューアーの内容は、構築したモデルの種類によって異なります。 詳細については、「[クラスターモデルの参照](browsing-a-clustering-model.md)」を参照してください。  
  
    -   **ドリルスルーを有効に**します。 このチェック ボックスをオンにすると、完成したモデルから基になるデータを表示できます。 このオプションは、デシジョン ツリー モデルを構築する場合にのみ使用できます。  
  
    -   **一時的なモデルを使用**します。 このチェック ボックスをオンにすると、モデルがサーバーに保存されません。 一時的なモデルは、Excel の終了時に削除されます。  
  
## <a name="more-about-clustering-models"></a>クラスターモデルの詳細  
 このウィザードで使用するクラスタリングアルゴリズムを変更するには、[**詳細設定**] をクリックし、[**アルゴリズムパラメーター** ] ダイアログボックスを使用します。  
  
 Microsoft クラスタリング アルゴリズムには、次のクラスタリング手法が用意されています。  
  
-   K-Means - スケーラブルまたは非スケーリング。  
  
-   Expectation Maximization (EM) - スケーラブルまたは非スケーリング。  
  
 また、CLUSTER_SEED パラメーターを使用して開始値を制御し、同じデータ セットを使用して繰り返されるモデルは常に同じ結果になるようにできます。  
  
### <a name="requirements"></a>要件  
 クラスター ウィザードを使用するには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに接続する必要があります。 詳細については、「 [Connect To Source data &#40;Excel 用データマイニングクライアント&#41;](connect-to-source-data-data-mining-client-for-excel.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データマイニングモデルの作成](creating-a-data-mining-model.md)   
 [Excel 用のテーブル分析ツール &#40;のカテゴリの検出&#41;](detect-categories-table-analysis-tools-for-excel.md)  
  
  

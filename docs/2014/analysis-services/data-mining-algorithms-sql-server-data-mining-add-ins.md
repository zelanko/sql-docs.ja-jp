---
title: データマイニングアルゴリズム (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation
- data mining algorithms
- clustering [data mining]
- linear regression
- association [data mining]
- neural networks
- logistic regression
- regression
- sequence analysis
- decision tree [data mining]
- Naive Bayes
- time series [data mining]
ms.assetid: 3a1a62e4-9fb5-4cdb-a6c6-1b8b30d417ef
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3a73ce5a538756a740afd2db72d585fa54f03cae
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84525931"
---
# <a name="data-mining-algorithms-sql-server-data-mining-add-ins"></a>データ マイニング アルゴリズム (SQL Server データ マイニング アドイン)
  Office 用データ マイニング アドインは、次のデータ マイニング アルゴリズムを使用して分析モデルの作成をサポートします。 すべてのアルゴリズムは、よく知られている機械学習メソッドに基づいており、Microsoft Research によって実装されたものです。  
  
## <a name="algorithms"></a>アルゴリズム  
  
|機械学習メソッド|しくみ|  
|-----------------------------|------------------|  
|Microsoft アソシエーションルールアルゴリズム|どの製品がともに購入されているか、またはどのイベントがともに発生するかを検出し、おすすめを作成するためのモデルを使用します。<br /><br /> [https://msdn.microsoft.com/library/ms174916.aspx](https://msdn.microsoft.com/library/ms174916.aspx)|  
|Microsoft クラスタリング アルゴリズム|市場セグメントを定義し、関連のある複数の顧客を自動的にグループ化するか、データ内のリレーションシップを見つけてそれ以降のマイニングで使用できるようにします。<br /><br /> [https://msdn.microsoft.com/library/ms174879.aspx](https://msdn.microsoft.com/library/ms174879.aspx)|  
|Microsoft デシジョン ツリー アルゴリズム|データ内のさまざまな要素間で、従来は不明だったリレーションシップを識別し、意思決定を下すためにより適切な情報を提供するか、特定の結果につながる要因を見つけます。<br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
|Microsoft 線形回帰アルゴリズム|数値形式の結果に寄与する要因を表す算術式を見つけます。<br /><br /> [https://msdn.microsoft.com/library/ms174824.aspx](https://msdn.microsoft.com/library/ms174824.aspx)|  
|Microsoft ロジスティック回帰アルゴリズム|バイナリ結果に寄与する要素を見つけ、それらの要素が結果にどのような影響を及ぼすかを研究します。<br /><br /> [https://msdn.microsoft.com/library/ms174828.aspx](https://msdn.microsoft.com/library/ms174828.aspx)|  
|Microsoft Naïve Bayes アルゴリズム|データ内のリレーションシップを探索し、結果との関連性が最も強いリレーションシップを見つけます。<br /><br /> [https://msdn.microsoft.com/library/ms174806.aspx](https://msdn.microsoft.com/library/ms174806.aspx)|  
|Microsoft ニューラルネットワークアルゴリズム|複数の入力と複数の出力の間に存在する隠されたリレーションシップを見つけます。 探索または予測の目的で使用します。<br /><br /> [https://msdn.microsoft.com/library/ms174941.aspx](https://msdn.microsoft.com/library/ms174941.aspx)|  
|Microsoft Time Series アルゴリズム|履歴データを使用して将来の値を予測します。<br /><br /> [https://msdn.microsoft.com/library/ms174923.aspx](https://msdn.microsoft.com/library/ms174923.aspx)|  
  
## <a name="advanced-options"></a>詳細オプション  
 Excel 用のデータ マイニング クライアントを使用する場合は、独自のデータ マイニング構造およびモデルを作成したり、アルゴリズムのパラメーターを調整したりすることができます。  
  
 [データマイニングアドイン SQL Server &#40;のアルゴリズムパラメーター&#41;](algorithm-parameters-sql-server-data-mining-add-ins.md)  
  
 これらの詳細オプションを使用してモデルをカスタマイズする方法は 2 つあります。  
  
-   **データマイニングクエリ**ウィザードを使用して、モデルを作成します。  
  
-   **データマイニングクライアント**で、ウィザードを開始した後、[**パラメーター**] をクリックします。  
  
## <a name="see-also"></a>参照  
 [クエリ &#40;SQL Server データマイニングアドイン&#41;](query-sql-server-data-mining-add-ins.md)   
 [高度なモデリング &#40;Excel 用データマイニングアドイン&#41;](advanced-modeling-data-mining-add-ins-for-excel.md)  
  
  

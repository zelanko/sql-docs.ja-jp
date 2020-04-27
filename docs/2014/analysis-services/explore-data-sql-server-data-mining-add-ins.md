---
title: データの探索 (SQL Server データマイニングアドイン) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- histogram [data mining]
- data visualization
ms.assetid: 714845a9-4c27-461a-9ba3-149e1e818386
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0bad2a2e65a65bbafa8218a3e0afbedd4b9f13b6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66081304"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a>データの探索 (SQL Server データ マイニング アドイン)
  ![データの探索ウィザード](media/dmc-explore.gif "データの探索ウィザード")  
  
 データの**探索**ウィザードは、データテーブル内のデータの種類と量を理解するのに役立ちます。 ウィザードは、選択した列の分布と値を一度に 1 列ずつグラフ化します。 その後、データのグループ化の方法を変更したり、確認用に内容を示すグラフを Excel ブックにコピーしたりできます。  
  
 データに連続する数値データが含まれている場合は、次の 2 つのビューを切り替えることができます。  
  
-   **折れ線グラフ。** このグラフは、データ値を X 軸、ケース数を Y 軸として表示します。  
  
-   **横棒グラフ。** このグラフは、それぞれの値のケース数に基づいて値をグループ化します。  
  
 データにグループが見つかると、データ値の実際の分布が使用されます。 そのため、横棒グラフには、一般的な 10 や 100 などの整数値軸マーカーが表示されません。 代わりに、横棒グラフに表示される範囲は 43521-55603 のようになります (Income 列の場合)。  
  
 データを別の範囲にグループ化するには、データを分析する前に Excel でこの操作を行う必要があります。 または、[ラベル](relabel-sql-server-data-mining-add-ins.md)の再付けウィザードを使用して、データのラベルを再作成することもできます。  
  
## <a name="using-the-explore-data-wizard"></a>データの探索ウィザードの使用  
  
1.  [**データマイニング**] リボンで、[**データの探索**] をクリックします。  
  
2.  **[ソースの選択**] ダイアログボックスで、データを含むテーブルまたはセルの範囲を選択します。  
  
3.  **[列の選択**] ダイアログボックスで、分析する列をペインに表示されているサンプルデータから選択します。  
  
4.  [**データの探索**] ダイアログボックスで、データの分布を表示するグラフの種類を選択します。  
  
5.  オプションで、新しい列をデータに追加したり、データを分割する方法を変更したり、グラフを Excel にコピーしたりできます。  
  
### <a name="requirements"></a>要件  
 **データの探索**ウィザードを使用するには、Excel データテーブルにデータが含まれている必要があります。   
  
## <a name="see-also"></a>参照  
 [データ マイニングの準備のチェック リスト](checklist-of-preparation-for-data-mining.md)  
  
  

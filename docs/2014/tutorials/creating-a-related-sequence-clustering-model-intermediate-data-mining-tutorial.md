---
title: 関連するシーケンスクラスターモデルの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1fb4f5bc-1756-45ca-9cd7-411a8c5992a9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 71db7ba5246e151bbca8a52972a2ba835b80ddb6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62855877"
---
# <a name="creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial"></a>関連するシーケンス クラスター モデルの作成 (中級者向けデータ マイニング チュートリアル)
  シーケンス クラスター モデルの検証により、Region や Income などの他の属性がモデルに大きな影響を与えていることがわかりました。そのため、シーケンスについての理解を深めるために、関連するシーケンス クラスター モデルを作成し、顧客の人口統計に関連する属性を削除します。  
  
 この作業では、地域別のシーケンス クラスター モデルのコピーを作成し、そのモデルからシーケンスに直接関連しない列を削除します。  
  
 新しいモデルには基になるマイニング モデルと同じすべての列が含まれますが、 マイニング構造から列を削除する必要はありません。新しいマイニング モデルで列を無視するように指定するだけです。  
  
### <a name="to-make-a-copy-of-the-sequence-clustering-model"></a>シーケンス クラスター モデルのコピーを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]のデータマイニングデザイナーで、[**マイニングモデル**] タブをクリックします。  
  
2.  コピーするモデルを右クリックし、[**新しいマイニングモデル**] をクリックします。  
  
3.  [**新しいマイニングモデル**] ダイアログボックスで、モデル名を入力し、[ `Sequence Clustering`Microsoft] を選択します。  
  
     このチュートリアルでは、という`Sequence Clustering`名前を入力します。  
  
4.  **[OK]** をクリックします。  
  
### <a name="to-remove-columns-from-the-mining-model"></a>マイニング モデルから列を削除するには  
  
1.  [**マイニングモデル**] タブの [シーケンスクラスター] という名前の新しいモデルの列で、[**収入グループ**] 属性の行をクリックし、[**無視**] を選択します。  
  
2.  属性**領域**に対してこの手順を繰り返します。  
  
3.  テーブル名の横にあるプラス記号をクリックし**て、テーブル**を展開し、入れ子になったテーブルの列を表示します。  
  
     新しいモデルの列は、次の列だけになります。  
  
     **注文番号キー**  
  
     **行番号キー**  
  
     **モデル予測**  
  
### <a name="to-process-the-new-sequence-clustering-model"></a>新しいシーケンス クラスター モデルを処理するには  
  
1.  [**マイニングモデル**] タブで、という名前`Sequence Clustering`の新しいモデルを右クリックし、[モデルの**処理**] を選択します。  
  
     新しいマイニング モデルは処理済みの構造に基づく簡略化されたモデルであるため、構造を再処理する必要はありません。 新しいマイニング モデルのみを処理できます。  
  
2.  [**はい**] をクリックして、更新されたデータマイニングプロジェクトをサーバーに配置します。  
  
3.  [**マイニングモデルの処理**] ダイアログボックスで、[**実行**] をクリックします。  
  
4.  [**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じ、[**マイニングモデルの処理**] ダイアログボックスでもう一度 [**閉じる**] をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [シーケンスクラスターモデルでの予測の作成 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [処理の要件および注意事項 &#40;データ マイニング&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  

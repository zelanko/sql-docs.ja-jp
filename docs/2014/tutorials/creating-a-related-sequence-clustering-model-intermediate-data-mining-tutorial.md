---
title: 関連するシーケンス クラスター モデル (中級者向けデータ マイニング チュートリアル) を作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fb4f5bc-1756-45ca-9cd7-411a8c5992a9
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c0820b087583194e78af1d1de46b4affe3a1d9fc
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36311810"
---
# <a name="creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial"></a>関連するシーケンス クラスター モデルの作成 (中級者向けデータ マイニング チュートリアル)
  シーケンス クラスター モデルの検証により、Region や Income などの他の属性がモデルに大きな影響を与えていることがわかりました。そのため、シーケンスについての理解を深めるために、関連するシーケンス クラスター モデルを作成し、顧客の人口統計に関連する属性を削除します。  
  
 この作業では、地域別のシーケンス クラスター モデルのコピーを作成し、そのモデルからシーケンスに直接関連しない列を削除します。  
  
 新しいモデルには基になるマイニング モデルと同じすべての列が含まれますが、 マイニング構造から列を削除する必要はありません。新しいマイニング モデルで列を無視するように指定するだけです。  
  
### <a name="to-make-a-copy-of-the-sequence-clustering-model"></a>シーケンス クラスター モデルのコピーを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]をクリックして、データ マイニング デザイナーで、**マイニング モデル**タブです。  
  
2.  コピー、および選択するモデルを右クリックして**新しいマイニング モデル**です。  
  
3.  **新しいマイニング モデル** ダイアログ ボックスは、モデルの名前を入力し、Microsoft`Sequence Clustering`です。  
  
     このチュートリアルでは、名前を入力`Sequence Clustering`です。  
  
4.  **[OK]** をクリックします。  
  
### <a name="to-remove-columns-from-the-mining-model"></a>マイニング モデルから列を削除するには  
  
1.  **マイニング モデルの**] タブの [Sequence Clustering という名前の新しいモデルの列の行をクリックして、 **Income Group**属性があり、選択**無視**です。  
  
2.  属性のこの手順を繰り返します**地域**です。  
  
3.  テーブル名の横にあるプラス記号をクリックして**v Assoc Seq Line Items**をテーブルを展開し、入れ子になったテーブルから列を表示します。  
  
     新しいモデルの列は、次の列だけになります。  
  
     **順序 NumberKey**  
  
     **行番号キー**  
  
     **モデルを予測します。**  
  
### <a name="to-process-the-new-sequence-clustering-model"></a>新しいシーケンス クラスター モデルを処理するには  
  
1.  **マイニング モデルの** タブで、という名前の新しいモデルを右クリックして`Sequence Clustering`を選択して**プロセス モデル**です。  
  
     新しいマイニング モデルは処理済みの構造に基づく簡略化されたモデルであるため、構造を再処理する必要はありません。 新しいマイニング モデルのみを処理できます。  
  
2.  をクリックして**はい**サーバーに更新されたデータ マイニング プロジェクトを配置します。  
  
3.  **マイニング モデルの処理**ダイアログ ボックスで、をクリックして**実行**です。  
  
4.  をクリックして**閉じる**を閉じる、**処理の進行状況**クリックしてダイアログ ボックスで、**閉じる**で再度、**マイニング モデルの処理** ダイアログ ボックス。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [シーケンス クラスター モデルで予測を作成する&#40;中級レベルのデータ マイニング チュートリアル&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [処理の要件および考慮事項&#40;データ マイニング&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
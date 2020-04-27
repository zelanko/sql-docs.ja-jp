---
title: '[ドリルスルー] ダイアログボックス (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.drillthrough.f1
ms.assetid: 42b78399-143d-4f44-90e0-b545ffb79e10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c065e36dd20646312d04379ea61b96d37a47a262
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66081492"
---
# <a name="drill-through-dialog-box-mining-model-viewer"></a>[ドリルスルー] ダイアログ ボックス (マイニング モデル ビューアー)
  データ マイニング デザイナーの **[マイニング モデル ビューアー]** タブを使用してマイニング モデルを表示する場合、モデルでドリルスルーが有効になっていれば、ケース データに関する詳細をドリルスルーできます。 さらに、基になるマイニング構造でドリルスルーが有効になっていれば、マイニング構造の列がマイニング モデルに含まれていない場合でも、それらの列を表示できます。 列リストでは、構造列に "Structure." というプレフィックスが付きます [ラベル]。  
  
> [!NOTE]  
>  既存のマイニング構造のドリルスルーを有効にすることはできません。 代わりに、マイニング構造を再作成し、作成中にドリルスルーを有効にする必要があります。  
  
 ドリルスルーをサポートする各マイニングモデルビューアーからケースデータにアクセスする方法の詳細については、 **「** [マイニングモデルからのケースデータへのドリル](data-mining/drill-through-to-case-data-from-a-mining-model.md)スルー」を参照してください。  
  
## <a name="options"></a>オプション  
 **[分類先のケース]**  
 選択したノードに含まれるルール、アイテムセット、およびクラスターの定義を表示します。  
  
 **[列リスト]**  
 モデル内の列と、構造列を表示します。  
  
 **注** 構造列は、マイニング構造でドリルスルーが有効であり、 **[モデルおよび構造列]** オプションを選択している場合にのみ表示されます。 さらに、これらの列を表示するには、マイニング モデルとマイニング構造の両方に対するドリルスルー権限を持っている必要があります。  
  
 モデルに含まれていない構造列は構造として表示され**ます。\<列名>**。  
  
> [!NOTE]  
>  列グリッドの任意の部分を右クリックして **[すべてコピー]** を選択すると、ドリルスルー データをタブ区切り形式でクリップボードにコピーできます。 コピーしたデータには、ケース データのみが含まれ、ノード定義は含まれません。  
  
 **[再生]**  
 データを更新するには、緑色の矢印ボタンをクリックします。  
  
## <a name="see-also"></a>参照  
 [データマイニング &#40;のドリルスルークエリ&#41;](data-mining/drillthrough-queries-data-mining.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [マイニング モデル ビューアーのタスクと操作方法](data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  

---
title: ドリルスルー ダイアログ ボックス (マイニング モデル ビューアー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.drillthrough.f1
ms.assetid: 42b78399-143d-4f44-90e0-b545ffb79e10
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 331ab6da3e2e244f3a0413d80006ceeb907704f4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151473"
---
# <a name="drill-through-dialog-box-mining-model-viewer"></a>[ドリルスルー] ダイアログ ボックス (マイニング モデル ビューアー)
  データ マイニング デザイナーの **[マイニング モデル ビューアー]** タブを使用してマイニング モデルを表示する場合、モデルでドリルスルーが有効になっていれば、ケース データに関する詳細をドリルスルーできます。 さらに、基になるマイニング構造でドリルスルーが有効になっていれば、マイニング構造の列がマイニング モデルに含まれていない場合でも、それらの列を表示できます。 列リストでは、構造列に "Structure." というプレフィックスが付きます [ラベル]。  
  
> [!NOTE]  
>  既存のマイニング構造のドリルスルーを有効にすることはできません。 代わりに、マイニング構造を再作成し、作成中にドリルスルーを有効にする必要があります。  
  
 各、ドリルスルーをサポートするマイニング モデル ビューアーからケース データにアクセスする方法については**を参照してください**[へのドリル スルー ケース データ マイニング モデルから](data-mining/drill-through-to-case-data-from-a-mining-model.md)します。  
  
## <a name="options"></a>および  
 **分類先のケース**  
 選択したノードに含まれるルール、アイテムセット、およびクラスターの定義を表示します。  
  
 **列の一覧**  
 モデル内の列と、構造列を表示します。  
  
 **注** 構造列は、マイニング構造でドリルスルーが有効であり、 **[モデルおよび構造列]** オプションを選択している場合にのみ表示されます。 さらに、これらの列を表示するには、マイニング モデルとマイニング構造の両方に対するドリルスルー権限を持っている必要があります。  
  
 モデルに含まれていない構造列として表示されます**構造体\<。列名 >** します。  
  
> [!NOTE]  
>  列グリッドの任意の部分を右クリックして **[すべてコピー]** を選択すると、ドリルスルー データをタブ区切り形式でクリップボードにコピーできます。 コピーしたデータには、ケース データのみが含まれ、ノード定義は含まれません。  
  
 **再生**  
 データを更新するには、緑色の矢印ボタンをクリックします。  
  
## <a name="see-also"></a>参照  
 [ドリルスルー クエリ&#40;データ マイニング&#41;](data-mining/drillthrough-queries-data-mining.md)   
 [マイニング モデル ビューアー&#40;データ マイニング モデル デザイナー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [マイニング モデル ビューアーのタスクと操作方法](data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  

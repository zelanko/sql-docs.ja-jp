---
title: マイニング モデルから列を除外 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a162adfdd2eeeb1209a68f5c05251b750bf3d590
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="exclude-a-column-from-a-mining-model"></a>マイニング モデルからの列の除外
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  新しいマイニング モデルを作成するとき、基となるマイニング構造に存在するすべての列を使用しないことがあります。 たとえば、顧客名列をドリルスルー用に追加し、モデリングには使用しない場合があります。 または、列の複数のコピーをそれぞれ異なる分離で作成して、各モデルで 1 つのコピーのみ使用し、残りは無視する場合があります。 複数の異なるモデルで入力列を選択的に追加して、追加した変数が出力列に与える影響を確認することもできます。  
  
 列の組み合わせごとに新しいマイニング構造を作成する必要はありません。代わりに、特定のモデルで使用されていないことを示すフラグを列に設定できます。  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>マイニング モデルから列を除外するには  
  
1.  **のデータ マイニング デザイナーの** [マイニング モデル] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブにある適切なマイニング モデルで、除外する列に対応するセルを選択します。  
  
2.  ドロップダウン リスト ボックスから **[無視]** を選択します。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  

---
title: マイニング構造から列を削除 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 315a969689c7c751e948f4ee82328f96ce507886
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="remove-columns-from-a-mining-structure"></a>マイニング構造からの列の削除
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング デザイナーを使用して、マイニング構造の作成後に構造から列を削除できます。 マイニング構造列を削除する理由には、次のようなものがあります。  
  
-   マイニング構造に列の複数のコピーが格納されており、モデルで重複データを使用しないようにする。  
  
-   データを保護する必要があるが、ドリルスルーが有効になっている。  
  
-   データがモデリングで使用されておらず、処理する必要がない。  
  
 マイニング構造から列を削除しても、データ ソース ビュー内の列または外部データ内の列は変更されません。メタデータのみ削除されます。 ただし、マイニング構造で使用される列を変更する場合は、構造およびその構造に基づくモデルを再処理する必要があります。  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a>マイニング構造から列を削除するには  
  
1.  データ マイニング デザイナーで **[マイニング構造]** タブを選択します。  
  
2.  マイニング構造のツリーを展開し、すべての列を表示します。  
  
3.  削除する列を右クリックして、 **[削除]** をクリックします。  
  
4.  **[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  

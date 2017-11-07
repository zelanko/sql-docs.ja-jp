---
title: "モデル列の別名を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- mining models [Analysis Services], columns
- column names [Analysis Services]
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a49c5aac7289573631a3ed50349c98690c28212d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-an-alias-for-a-model-column"></a>モデル列の別名の作成
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、モデル列の別名を作成できます。 この機能は、マイニング構造名が長すぎて扱いにくい場合や、内容またはモデル内での使い方をわかりやすくするために列名を変更する場合に便利です。 たとえば、構造列のコピーを作成して特定のモデル専用に列を分離すると、列名を変更して内容を正確に反映できます。  
  
 モデル列の別名を作成するには、 **[プロパティ]** ペインを使用し、列の [Name](../../analysis-services/scripting/properties/name-element-assl.md) プロパティを設定します。  
  
 データ マイニング デザイナーの **[マイニング モデル]** タブに、列の使用法のラベルの横にかっこで囲まれて別名が表示されます。  
  
 マイニング モデルのプロパティを設定する方法については、「 [マイニング モデル列](../../analysis-services/data-mining/mining-model-columns.md)」を参照してください。  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>マイニング モデル列に別名を追加するには  
  
1.  データ マイニング デザイナーの **[マイニング モデル]** タブで、変更するマイニング列のマイニング モデル内のセルを右クリックし、 **[プロパティ]**を選択します。  
  
2.  画面の右側の **[プロパティ]** ウィンドウで、Name プロパティの横のセルをクリックし、現在の値を削除します。 列の新しい名前を入力します。  
  
## <a name="see-also"></a>参照  
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [マイニング モデルのプロパティ](../../analysis-services/data-mining/mining-model-properties.md)  
  
  


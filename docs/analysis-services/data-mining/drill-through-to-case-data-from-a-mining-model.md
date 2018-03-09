---
title: "マイニング モデルからケース データにドリルスルー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: drillthrough [Analysis Services]
ms.assetid: b4d3f350-e543-4ea9-b3a2-b4f7c0a9ae27
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9f287437903c54c4eb66da3343bc2c80f18ac5fe
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="drill-through-to-case-data-from-a-mining-model"></a>マイニング モデルからケース データへのドリルスルー
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]マイニング モデルが、モデルを参照するときに、モデルのケースにドリルスルーできるように構成されている場合は、モデルの作成に使用されたケースに関する詳細情報を取得できます。 さらに、基になるマイニング構造が、構造ケースへのドリルスルーを許可するように構成されており、ユーザーが適切な権限を持っている場合は、マイニング構造から情報を返すことができます。 これには、マイニング モデルに含まれていない列を含めることもできます。  
  
 基になるデータへのドリルスルーがマイニング構造で許可されておらず、マイニング モデルでは許可されている場合、モデル ケースの情報は表示できますが、マイニング構造の情報は表示できません。  
  
> [!NOTE]  
>  **AllowDrillthrough** プロパティを **True**に設定することで、既存のマイニング モデルにドリルスルー機能を追加できます。 ただし、ドリルスルーを有効にした後、ケース データを表示する前にモデルを再処理する必要があります。 詳細については、「 [Enable Drillthrough for a Mining Model](../../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)」(マイニング モデルのドリルスルーの有効化) を参照してください。  
  
 使用するビューアーの種類に応じて、次に示す方法で、ドリルスルーするノードを選択できます。  
  
|ビューアー名|ペイン名またはタブ名|選択するノード|  
|-----------------|----------------------|-----------------|  
|**Microsoft ツリー ビューアー**|**[デシジョン ツリー]** タブ|ツリー ノードをクリックします。<br /><br /> **注** **All** ノードにはドリルスルーを使用しないでください。結果が返されるまでに非常に時間がかかることがあります。|  
|**Microsoft クラスター ビューアー**|**クラスター ダイアグラム**|クラスター ノードをクリックします。|  
|**Microsoft クラスター ビューアー**|**クラスターのプロファイル**|クラスター列内の任意の場所をクリックします。|  
|**Microsoft アソシエーション ビューアー**|**[ルール]** タブ|一連のルールを含む行をクリックします。|  
|**Microsoft アソシエーション ビューアー**|**[アイテムセット]** タブ|アイテムセットを含む行をクリックします。|  
|**Microsoft シーケンス クラスター ビューアー**|**[ルール]** タブ|一連のルールを含む行をクリックします。|  
|**Microsoft シーケンス クラスター ビューアー**|**[アイテムセット]** タブ|アイテムセットを含む行をクリックします。|  
  
> [!NOTE]  
>  ドリルスルーを使用できないモデルもあります。 ドリルスルーを使用できるかどうかは、モデルの作成に使用したアルゴリズムによって異なります。 ドリルスルーをサポートするマイニング モデルの種類の一覧については、「 [ドリルスルー クエリ &#40;データ マイニング&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)に設定することで、既存のマイニング モデルにドリルスルー機能を追加できます。  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a>マイニング モデルからのドリルスルー データを表示するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のマイニング モデルを含むマイニング構造を開きます。  
  
2.  データ マイニング デザイナーで、 **[マイニング モデル ビューアー]** タブをクリックします。  
  
3.  **[マイニング モデル]** ボックスの一覧からモデルを選択します。  
  
4.  **[ビューアー]** ボックスの一覧からビューアーを選択し、特定のノードを右クリックします。  
  
5.  **[ドリルスルー]**を選択してから、 **[モデル列のみ]**または **[モデル列および構造列]** を選択します。 **[ドリルスルー]** ウィンドウが表示されます。  
  
6.  データをクリップボードにコピーするには、テーブル内の任意の行を右クリックして **[すべてコピー]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [ドリルスルー クエリ &#40;データ マイニング&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
  
